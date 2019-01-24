---
title: Usando o Azure Key Vault para proteger segredos no momento da produção
description: Segurança em microsserviços e aplicativos Web do .NET – o Azure Key Vault é uma excelente maneira de lidar com os segredos do aplicativo que são totalmente controlados pelos administradores. Os administradores podem até mesmo atribuir e revogar os valores de desenvolvimento sem que os desenvolvedores precisam lidar com eles.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 291d60f941e4280ff120296ce1c392df3300dc44
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362413"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="e7ca2-104">Usar o Azure Key Vault para proteger os segredos no tempo de produção</span><span class="sxs-lookup"><span data-stu-id="e7ca2-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="e7ca2-105">Os segredos armazenados como variáveis de ambiente ou armazenados pela ferramenta Secret Manager ainda são armazenados localmente e descriptografados no computador.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="e7ca2-106">Uma opção mais segura para armazenar segredos é o [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que oferece um local seguro e central para armazenar chaves e segredos.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="e7ca2-107">O pacote **Microsoft.Extensions.Configuration.AzureKeyVault** permite que um aplicativo do ASP.NET Core leia informações de configuração do Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="e7ca2-108">Para começar a usar os segredos de um Azure Key Vault, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e7ca2-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="e7ca2-109">Registre seu aplicativo como um aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="e7ca2-110">(O acesso a cofres de chaves é gerenciado pelo Azure AD). Isso pode ser feito por meio do portal de gerenciamento do Azure.\\</span><span class="sxs-lookup"><span data-stu-id="e7ca2-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\\</span></span>

   <span data-ttu-id="e7ca2-111">Ou, se você desejar que seu aplicativo seja autenticado usando um certificado em vez de um segredo do cliente ou senha, será possível usar o cmdlet do PowerShell [AzureRmADApplication novo](/powershell/module/azurerm.resources/new-azurermadapplication).</span><span class="sxs-lookup"><span data-stu-id="e7ca2-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="e7ca2-112">O certificado que você registrar com o Azure Key Vault precisa apenas de sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="e7ca2-113">(O aplicativo usará a chave privada.)</span><span class="sxs-lookup"><span data-stu-id="e7ca2-113">(Your application will use the private key.)</span></span>

2. <span data-ttu-id="e7ca2-114">Permita que o aplicativo registrado acesse o Key Vault criando uma entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="e7ca2-115">É possível fazer isso usando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e7ca2-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="e7ca2-116">Inclua o Key Vault como uma fonte de configuração em seu aplicativo chamando o método de extensão <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> ao criar uma instância de <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="e7ca2-117">Observe que a chamada de `AddAzureKeyVault` requer a ID do aplicativo que foi registrada e permitiu acesso ao Key Vault nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="e7ca2-118">Você também pode usar uma sobrecarga de `AddAzureKeyVault`, que usa um certificado no lugar do segredo do cliente, apenas incluindo uma referência ao pacote [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory).</span><span class="sxs-lookup"><span data-stu-id="e7ca2-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7ca2-119">Recomendamos que você registre o Azure Key Vault como o último provedor de configuração, para que ele possa substituir os valores de configuração dos provedores anteriores.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e7ca2-120">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="e7ca2-120">Additional resources</span></span>

- <span data-ttu-id="e7ca2-121">**Usando o Azure Key Vault para proteger segredos do aplicativo** \\</span><span class="sxs-lookup"><span data-stu-id="e7ca2-121">**Using Azure Key Vault to protect application secrets** \\</span></span>
  [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="e7ca2-122">**Armazenamento seguro dos segredos do aplicativo durante o desenvolvimento** \\</span><span class="sxs-lookup"><span data-stu-id="e7ca2-122">**Safe storage of app secrets during development** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](/aspnet/core/security/app-secrets)

- <span data-ttu-id="e7ca2-123">**Configurando a proteção de dados** \\</span><span class="sxs-lookup"><span data-stu-id="e7ca2-123">**Configuring data protection** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="e7ca2-124">**Gerenciamento e tempo de vida de chaves** \\</span><span class="sxs-lookup"><span data-stu-id="e7ca2-124">**Key management and lifetime** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

- <span data-ttu-id="e7ca2-125">Repositório do GitHub **Microsoft.Extensions.Configuration.KeyPerFile**.</span><span class="sxs-lookup"><span data-stu-id="e7ca2-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repo.</span></span> \
  [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
><span data-ttu-id="e7ca2-126">[Anterior](developer-app-secrets-storage.md)
>[Próximo](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="e7ca2-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
