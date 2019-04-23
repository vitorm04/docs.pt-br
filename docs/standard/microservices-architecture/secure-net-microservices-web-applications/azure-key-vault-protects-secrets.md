---
title: Usando o Azure Key Vault para proteger segredos no momento da produção
description: Segurança em microsserviços e aplicativos Web do .NET – o Azure Key Vault é uma excelente maneira de lidar com os segredos do aplicativo que são totalmente controlados pelos administradores. Os administradores podem até mesmo atribuir e revogar os valores de desenvolvimento sem que os desenvolvedores precisam lidar com eles.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672414"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="f49c1-104">Usar o Azure Key Vault para proteger os segredos no tempo de produção</span><span class="sxs-lookup"><span data-stu-id="f49c1-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="f49c1-105">Os segredos armazenados como variáveis de ambiente ou armazenados pela ferramenta Secret Manager ainda são armazenados localmente e descriptografados no computador.</span><span class="sxs-lookup"><span data-stu-id="f49c1-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="f49c1-106">Uma opção mais segura para armazenar segredos é o [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que oferece um local seguro e central para armazenar chaves e segredos.</span><span class="sxs-lookup"><span data-stu-id="f49c1-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="f49c1-107">O pacote **Microsoft.Extensions.Configuration.AzureKeyVault** permite que um aplicativo do ASP.NET Core leia informações de configuração do Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f49c1-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="f49c1-108">Para começar a usar os segredos de um Azure Key Vault, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f49c1-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="f49c1-109">Registre seu aplicativo como um aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f49c1-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="f49c1-110">(O acesso a cofres de chaves é gerenciado pelo Azure AD). Isso pode ser feito por meio do portal de gerenciamento do Azure.\\</span><span class="sxs-lookup"><span data-stu-id="f49c1-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\\</span></span>

   <span data-ttu-id="f49c1-111">Ou, se você desejar que seu aplicativo seja autenticado usando um certificado em vez de um segredo do cliente ou senha, use o cmdlet do PowerShell [New-AzADApplication](/powershell/module/az.resources/new-azadapplication).</span><span class="sxs-lookup"><span data-stu-id="f49c1-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="f49c1-112">O certificado que você registrar com o Azure Key Vault precisa apenas de sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="f49c1-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="f49c1-113">O aplicativo usará a chave privada.</span><span class="sxs-lookup"><span data-stu-id="f49c1-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="f49c1-114">Permita que o aplicativo registrado acesse o Key Vault criando uma entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="f49c1-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="f49c1-115">É possível fazer isso usando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f49c1-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="f49c1-116">Inclua o Key Vault como uma fonte de configuração em seu aplicativo chamando o método de extensão <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> ao criar uma instância de <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>.</span><span class="sxs-lookup"><span data-stu-id="f49c1-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="f49c1-117">Observe que a chamada de `AddAzureKeyVault` requer a ID do aplicativo que foi registrada e permitiu acesso ao Key Vault nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="f49c1-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="f49c1-118">Você também pode usar uma sobrecarga de `AddAzureKeyVault`, que usa um certificado no lugar do segredo do cliente, apenas incluindo uma referência ao pacote [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory).</span><span class="sxs-lookup"><span data-stu-id="f49c1-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f49c1-119">Recomendamos que você registre o Azure Key Vault como o último provedor de configuração, para que ele possa substituir os valores de configuração dos provedores anteriores.</span><span class="sxs-lookup"><span data-stu-id="f49c1-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f49c1-120">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f49c1-120">Additional resources</span></span>

- <span data-ttu-id="f49c1-121">**Usando o Azure Key Vault para proteger segredos do aplicativo** \\</span><span class="sxs-lookup"><span data-stu-id="f49c1-121">**Using Azure Key Vault to protect application secrets** \\</span></span>
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="f49c1-122">**Armazenamento seguro dos segredos do aplicativo durante o desenvolvimento** \\</span><span class="sxs-lookup"><span data-stu-id="f49c1-122">**Safe storage of app secrets during development** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="f49c1-123">**Configurando a proteção de dados** \\</span><span class="sxs-lookup"><span data-stu-id="f49c1-123">**Configuring data protection** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="f49c1-124">**Gerenciamento e tempo de vida de chaves da proteção de dados no ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="f49c1-124">**Data Protection key management and lifetime in ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="f49c1-125">Repositório do GitHub **Microsoft.Extensions.Configuration.KeyPerFile**.</span><span class="sxs-lookup"><span data-stu-id="f49c1-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="f49c1-126">[Anterior](developer-app-secrets-storage.md)
>[Próximo](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="f49c1-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
