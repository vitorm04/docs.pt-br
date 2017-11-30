---
title: "Usando o Cofre de chaves do Azure para proteger segredos em tempo de produção"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Usando o Cofre de chaves do Azure para proteger segredos em tempo de produção"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7f922997e8d0c63e206cd68f4efda14985c86b72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="30299-104">Usando o Cofre de chaves do Azure para proteger segredos em tempo de produção</span><span class="sxs-lookup"><span data-stu-id="30299-104">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="30299-105">Segredos armazenadas como variáveis de ambiente ou armazenada pela ferramenta Gerenciador de segredo ainda são armazenados localmente e descriptografados no computador.</span><span class="sxs-lookup"><span data-stu-id="30299-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="30299-106">É uma opção mais segura para armazenar segredos [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que fornece um local central seguro para armazenar chaves e segredos.</span><span class="sxs-lookup"><span data-stu-id="30299-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="30299-107">O pacote de Microsoft.Extensions.Configuration.AzureKeyVault permite que um aplicativo do ASP.NET Core para ler informações de configuração do Cofre de chaves do Azure.</span><span class="sxs-lookup"><span data-stu-id="30299-107">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="30299-108">Para começar a usar os segredos de um cofre de chaves do Azure, você deve seguir estas etapas:</span><span class="sxs-lookup"><span data-stu-id="30299-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="30299-109">Primeiro, registre seu aplicativo como um aplicativo do AD do Azure.</span><span class="sxs-lookup"><span data-stu-id="30299-109">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="30299-110">(Acesso a cofres de chaves é gerenciado pelo AD do Azure). Isso pode ser feito por meio do portal de gerenciamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="30299-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="30299-111">Como alternativa, se você quiser que seu aplicativo para autenticar usando um certificado em vez de um segredo de cliente ou a senha, você pode usar o [AzureRmADApplication novo](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) cmdlet do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30299-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="30299-112">O certificado que você se registrar com o Cofre de chaves do Azure precisa somente sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="30299-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="30299-113">(O aplicativo usará a chave privada).</span><span class="sxs-lookup"><span data-stu-id="30299-113">(Your application will use the private key.)</span></span>

<span data-ttu-id="30299-114">Segundo, dê o acesso do aplicativo registrado para o Cofre de chaves ao criar uma nova entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="30299-114">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="30299-115">Você pode fazer isso usando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="30299-115">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="30299-116">Em terceiro lugar, incluem o Cofre de chave como uma fonte de configuração em seu aplicativo chamando o método de extensão IConfigurationBuilder.AddAzureKeyVault quando você cria uma instância de IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="30299-116">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="30299-117">Observe que a chamada AddAzureKeyVault exigirá a ID do aplicativo que foi registrada e recebe acesso para o Cofre de chaves nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="30299-117">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="30299-118">Atualmente, padrão do .NET e .NET Core oferecem suporte a obtenção de informações de configuração de um cofre de chaves do Azure usando uma ID de cliente e o segredo do cliente.</span><span class="sxs-lookup"><span data-stu-id="30299-118">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="30299-119">Aplicativos do .NET framework podem usar uma sobrecarga de IConfigurationBuilder.AddAzureKeyVault que usa um certificado no lugar de segredo do cliente.</span><span class="sxs-lookup"><span data-stu-id="30299-119">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="30299-120">Redação deste artigo, o trabalho é [em andamento](https://github.com/aspnet/Configuration/issues/605) para disponibilizar essa sobrecarga no .NET Core e .NET padrão.</span><span class="sxs-lookup"><span data-stu-id="30299-120">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="30299-121">Até que a sobrecarga de AddAzureKeyVault que aceita que um certificado estiver disponível, os aplicativos ASP.NET Core podem acessar um cofre de chaves do Azure com autenticação baseada em certificado criando explicitamente um objeto KeyVaultClient, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="30299-121">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="30299-122">Neste exemplo, a chamada para AddAzureKeyVault é fornecido no final do registro do provedor de configuração.</span><span class="sxs-lookup"><span data-stu-id="30299-122">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="30299-123">É uma prática recomendada para registrar o Cofre de chaves do Azure como o último provedor de configuração para que ele tenha a oportunidade de substituem os valores de configuração de provedores anteriores, e para que nenhum valor de configuração de outras fontes substituem aquelas do key vault.</span><span class="sxs-lookup"><span data-stu-id="30299-123">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="30299-124">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="30299-124">Additional resources</span></span>

-   <span data-ttu-id="30299-125">**Usando o Cofre de chaves do Azure para proteger segredos do aplicativo**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="30299-125">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="30299-126">**Armazenamento seguro de segredos do aplicativo durante o desenvolvimento**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="30299-126">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="30299-127">**Configurando a proteção de dados**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="30299-127">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="30299-128">**Tempo de vida e gerenciamento de chave**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#proteção de dados-configurações padrão*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="30299-128">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="30299-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="30299-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="30299-130">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="30299-130">GitHub repo.</span></span>
    [<span data-ttu-id="30299-131">*https://GitHub.com/ASPNET/Configuration/Tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span><span class="sxs-lookup"><span data-stu-id="30299-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span></span>](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="30299-132">[Anterior] (desenvolvedor-aplicativo-segredos-storage.md) [Avançar] (... / chave takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="30299-132">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>
