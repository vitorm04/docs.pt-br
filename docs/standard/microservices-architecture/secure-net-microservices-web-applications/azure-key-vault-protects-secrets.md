---
title: "Usando o Azure Key Vault para proteger segredos no momento da produção"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Usando o Azure Key Vault para proteger segredos no momento da produção"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb289c7361362c225eac8b9898bac276c4b623b4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="1af43-104">Usando o Azure Key Vault para proteger segredos no momento da produção</span><span class="sxs-lookup"><span data-stu-id="1af43-104">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="1af43-105">Os segredos armazenados como variáveis de ambiente ou armazenados pela ferramenta Secret Manager ainda são armazenados localmente e descriptografados no computador.</span><span class="sxs-lookup"><span data-stu-id="1af43-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="1af43-106">Uma opção mais segura para armazenar segredos é o [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que oferece um local seguro e central para armazenar chaves e segredos.</span><span class="sxs-lookup"><span data-stu-id="1af43-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="1af43-107">O pacote Microsoft.Extensions.Configuration.AzureKeyVault permite que um aplicativo do ASP.NET Core leia informações de configuração do Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="1af43-107">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="1af43-108">Para começar a usar os segredos de um Azure Key Vault, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1af43-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="1af43-109">Primeiro, registre seu aplicativo como um aplicativo Azure AD.</span><span class="sxs-lookup"><span data-stu-id="1af43-109">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="1af43-110">(O acesso a cofres de chaves é gerenciado pelo Azure AD). Isso pode ser feito por meio do Portal de Gerenciamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="1af43-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="1af43-111">Ou, se você desejar que seu aplicativo seja autenticado usando um certificado em vez de um segredo do cliente ou senha, será possível usar o cmdlet do PowerShell [AzureRmADApplication novo](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication).</span><span class="sxs-lookup"><span data-stu-id="1af43-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="1af43-112">O certificado que você registrar com o Azure Key Vault precisa apenas de sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="1af43-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="1af43-113">(O aplicativo usará a chave privada.)</span><span class="sxs-lookup"><span data-stu-id="1af43-113">(Your application will use the private key.)</span></span>

<span data-ttu-id="1af43-114">Segundo, conceda ao aplicativo registrado acesso ao cofre de chaves criando uma nova entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="1af43-114">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="1af43-115">É possível fazer isso usando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1af43-115">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="1af43-116">Em terceiro lugar, inclua o cofre de chaves como uma fonte de configuração em seu aplicativo chamando o método de extensão IConfigurationBuilder.AddAzureKeyVault quando você criar uma instância IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="1af43-116">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="1af43-117">Observe que chamar AddAzureKeyVault exigirá a ID do aplicativo que foi registrado e que recebeu acesso ao cofre de chaves nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="1af43-117">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="1af43-118">No momento, o .NET Standard e o .NET Core dão suporte à obtenção de informações de configuração de um Azure Key Vault usando uma ID de cliente e o segredo do cliente.</span><span class="sxs-lookup"><span data-stu-id="1af43-118">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="1af43-119">Os aplicativos do .NET Framework podem usar uma sobrecarga de IConfigurationBuilder.AddAzureKeyVault que usa um certificado no lugar do segredo do cliente.</span><span class="sxs-lookup"><span data-stu-id="1af43-119">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="1af43-120">No momento da redação deste artigo, o trabalho está [em andamento](https://github.com/aspnet/Configuration/issues/605) para disponibilizar essa sobrecarga no .NET Standard e no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1af43-120">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="1af43-121">Até que a sobrecarga AddAzureKeyVault que aceita um certificado esteja disponível, os aplicativos do ASP.NET Core poderão acessar um Azure Key Vault com autenticação baseada em certificado criando explicitamente um objeto KeyVaultClient, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1af43-121">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

<span data-ttu-id="1af43-122">Neste exemplo, a chamada a AddAzureKeyVault vem no final do registro do provedor de configuração.</span><span class="sxs-lookup"><span data-stu-id="1af43-122">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="1af43-123">É uma melhor prática registrar o Azure Key Vault como o último provedor de configuração para que ele tenha uma oportunidade de substituir valores de configuração de provedores anteriores, e para que nenhum valor de configuração de outras fontes substituam os do cofre de chaves.</span><span class="sxs-lookup"><span data-stu-id="1af43-123">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1af43-124">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="1af43-124">Additional resources</span></span>

-   <span data-ttu-id="1af43-125">**Usando o Azure Key Vault para proteger segredos do aplicativo**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="1af43-125">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="1af43-126">**Armazenamento seguro de segredos do aplicativo durante o desenvolvimento**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="1af43-126">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="1af43-127">**Configurando a proteção de dados**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="1af43-127">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="1af43-128">**Tempo de vida e gerenciamento de chaves**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="1af43-128">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="1af43-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="1af43-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="1af43-130">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="1af43-130">GitHub repo.</span></span>
    [<span data-ttu-id="1af43-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span><span class="sxs-lookup"><span data-stu-id="1af43-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span></span>](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="1af43-132">[Anterior] (developer-app-secrets-storage.md) [Próximo] (../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="1af43-132">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>
