---
title: VPN auf Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/19/2018
ms.topic: article
description: Informationen Sie zum verwenden, Setup, und Konfigurieren von VPN-Funktionen für Ihr Windows 10 IoT Core-Gerät.
keywords: Windows Iot, VPN, Setup sowie von Geräten
ms.openlocfilehash: 94eafcb74a05179a7741cb516b5e7be30b525092
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512977"
---
# <a name="leveraging-vpn-capabilities-for-your-windows-10-iot-core-device"></a><span data-ttu-id="8c7e7-104">Nutzt die VPN-Funktionen für Ihr Windows 10 IoT Core-Gerät</span><span class="sxs-lookup"><span data-stu-id="8c7e7-104">Leveraging VPN capabilities for your Windows 10 IoT Core device</span></span>

<span data-ttu-id="8c7e7-105">Um die VPN-Funktionen von Windows 10 IoT Core nutzen zu können, führen Sie in der unten stehenden Anweisungen aus.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-105">In order to leverage the VPN capabilities of Windows 10 IoT Core, follow the instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="8c7e7-106">Die meisten der unten stehenden Anweisungen müssen angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-106">Most of the instructions below must be adapted.</span></span> <span data-ttu-id="8c7e7-107">Sie sind spezifisch für den VPN-Host an, dem der Benutzer eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-107">They are specific to the VPN host that the user is connecting to.</span></span> <span data-ttu-id="8c7e7-108">Die verwendeten Zertifikate sind Beispiele.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-108">The certs used are examples.</span></span>

## <a name="establishing-a-vpn-connection"></a><span data-ttu-id="8c7e7-109">Eine VPN-Verbindung</span><span class="sxs-lookup"><span data-stu-id="8c7e7-109">Establishing a VPN connection</span></span> 

1. <span data-ttu-id="8c7e7-110">Abrufen Sie der erforderlichen Zertifikate, und kopieren Sie Ihre IoT-Geräte (z. B. zu einem Ordner \vpntest).</span><span class="sxs-lookup"><span data-stu-id="8c7e7-110">Obtain the necessary certs and copy to your IoT device (e.g. to a \vpntest folder).</span></span>

* <span data-ttu-id="8c7e7-111">RASTest.pfx</span><span class="sxs-lookup"><span data-stu-id="8c7e7-111">RASTest.pfx</span></span>
* <span data-ttu-id="8c7e7-112">IssuingCA.crl</span><span class="sxs-lookup"><span data-stu-id="8c7e7-112">IssuingCA.crl</span></span>
* <span data-ttu-id="8c7e7-113">RootCA.crl</span><span class="sxs-lookup"><span data-stu-id="8c7e7-113">RootCA.crl</span></span>

2. <span data-ttu-id="8c7e7-114">Anwenden von Zertifikaten für lokalen Computer ein.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-114">Apply local machine certs a.</span></span> <span data-ttu-id="8c7e7-115">PowerShell in Gerät als administrator</span><span class="sxs-lookup"><span data-stu-id="8c7e7-115">PowerShell into device as administrator</span></span>

```powershell
certmgr -add .\IssuingCA.crl -r localmachine -s root
certmgr -add .\RootCA.crl -r localmachine -s root
```

3. <span data-ttu-id="8c7e7-116">Anwenden von Zertifikaten für Benutzer ein.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-116">Apply user certs a.</span></span> <span data-ttu-id="8c7e7-117">Melden Sie sich das IoT-Geräte mithilfe von SSH als "DefaultAccount".</span><span class="sxs-lookup"><span data-stu-id="8c7e7-117">Login to the IoT Device using SSH as "DefaultAccount".</span></span>
<span data-ttu-id="8c7e7-118">b.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-118">b.</span></span> <span data-ttu-id="8c7e7-119">Geben Sie an der Eingabeaufforderung "PowerShell" ein.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-119">From the command prompt, type "PowerShell".</span></span>
<span data-ttu-id="8c7e7-120">c.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-120">c.</span></span> <span data-ttu-id="8c7e7-121">Führen Sie die folgenden Befehle aus PowerShell (beim Anmelden als "Standard-Konto"):</span><span class="sxs-lookup"><span data-stu-id="8c7e7-121">Issue the following commands from PowerShell (while logged in as "Default Account"):</span></span>

```powershell
$mypwd = ConvertTo-SecureString -String "<password>" -Force -AsPlainText
import-pfxcertificate -FilePath RasTest.pfx -CertStoreLocation cert:currentUser\my -Password $mypwd

Cert -add .\IssuingCA.crl -r currentuser -s my
certmgr -add .\RootCA.crl -r currentuser -s my
```

4. <span data-ttu-id="8c7e7-122">Korrektur Hosts-Datei hinzufügen, einen Eintrag in die Datei c:\windows\system32\driverS\etc\hosts (unten gezeigten Beispiel);</span><span class="sxs-lookup"><span data-stu-id="8c7e7-122">Fix hosts file Add an entry into c:\windows\system32\driverS\etc\hosts file (example shown below);</span></span>

> |    |    |    |
> |----|----| ---|
> | <span data-ttu-id="8c7e7-123">10.10.10.10</span><span class="sxs-lookup"><span data-stu-id="8c7e7-123">10.10.10.10</span></span> | <span data-ttu-id="8c7e7-124">MyVPN.DomainName.org</span><span class="sxs-lookup"><span data-stu-id="8c7e7-124">MyVPN.DomainName.org</span></span> | <span data-ttu-id="8c7e7-125">Ersetzen Sie dies durch IP-Adressen und Domänennamen nach Bedarf</span><span class="sxs-lookup"><span data-stu-id="8c7e7-125">Replace with IP address and domain name as needed</span></span> |

5. <span data-ttu-id="8c7e7-126">Erstellen des VPN-Test-app ersetzen "MyVPN.DomainName.org" im Quellcode.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-126">Build the VPN test app Replace the "MyVPN.DomainName.org" in the source code.</span></span> <span data-ttu-id="8c7e7-127">Erweitern Sie nach Bedarf weiter.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-127">Augment further as needed.</span></span>

6. <span data-ttu-id="8c7e7-128">Bereitstellen von den folgenden Code in der "Starten und beenden eine VPN-Verbindung" im Abschnitt mit dem Windows 10 IoT-Gerät.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-128">Deploy the code below in the "Starting and stopping a VPN Connection" section to the Windows 10 IoT device.</span></span>
<span data-ttu-id="8c7e7-129">Geben Sie eine beliebige "Profilname" aus, und klicken Sie auf die Schaltfläche "Eine Verbindung herstellen, VPN".</span><span class="sxs-lookup"><span data-stu-id="8c7e7-129">Enter an arbitrary "Profile name" and press the "Connect to VPN" button.</span></span> 


## <a name="starting-and-stopping-a-vpn-connection"></a><span data-ttu-id="8c7e7-130">Starten und beenden eine VPN-Verbindung</span><span class="sxs-lookup"><span data-stu-id="8c7e7-130">Starting and stopping a VPN connection</span></span>

<span data-ttu-id="8c7e7-131">Verwenden Sie den folgenden Code zum Starten und beenden eine VPN-Verbindung.</span><span class="sxs-lookup"><span data-stu-id="8c7e7-131">Use the code below to start and stop a VPN connection.</span></span>

```csharp

  private async Task ConnectVPNProfile()
        {
            string vpnProfileName = "MyVPNProfileName";

            string[] epdg = { "MyVPN.DomainName.org" };
            VpnManagementErrorStatus status = VpnManagementErrorStatus.Ok;
            IAsyncOperation<VpnManagementErrorStatus> op;

            var vpnMa = new VpnManagementAgent();
            var vpnProfile = new VpnNativeProfile();
            vpnProfile.AlwaysOn = true;
            vpnProfile.ProfileName = vpnProfileName;
            vpnProfile.RequireVpnClientAppUI = true;
            vpnProfile.RememberCredentials = true;
            vpnProfile.RoutingPolicyType = VpnRoutingPolicyType.SplitRouting;
            vpnProfile.TunnelAuthenticationMethod = VpnAuthenticationMethod.Eap;
            vpnProfile.UserAuthenticationMethod = VpnAuthenticationMethod.Eap;
            foreach (var s in epdg)
            {
                vpnProfile.Servers.Add(s);
            }

            vpnProfile.EapConfiguration = GetEapXmlString();

            // Adds the profile using the management api.
           status = await vpnMa.AddProfileFromObjectAsync(vpnProfile);
            Debug.WriteLine($"Add profile: {status}");
            TextBlockLog.Text += $"Add profile: {status}\r\n";

            await Task.Delay(1000);

            op = vpnMa.ConnectProfileAsync(vpnProfile);
            status = await op;
            Debug.WriteLine($"Connect succeeded: {status}");
            TextBlockLog.Text += $"Connect profile: {status}\r\n";


        }


  public static string GetEapXmlString()
        {
            //string template = "<EapHostConfig xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">25</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>25</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1\"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled=\"true\"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>true</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">false</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>";
            string template = "<EapHostConfig xmlns =\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">13</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><CAHashList Enabled=\"true\"><IssuerHash>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </IssuerHash></CAHashList></FilteringInfo></TLSExtensions></EapType></Eap></Config></EapHostConfig>";
            //TODO: Create propper XML here
            string result = template;

            return result;
        }
```







