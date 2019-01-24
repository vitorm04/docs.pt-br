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
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Usar o Azure Key Vault para proteger os segredos no tempo de produção

Os segredos armazenados como variáveis de ambiente ou armazenados pela ferramenta Secret Manager ainda são armazenados localmente e descriptografados no computador. Uma opção mais segura para armazenar segredos é o [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que oferece um local seguro e central para armazenar chaves e segredos.

O pacote **Microsoft.Extensions.Configuration.AzureKeyVault** permite que um aplicativo do ASP.NET Core leia informações de configuração do Azure Key Vault. Para começar a usar os segredos de um Azure Key Vault, siga estas etapas:

1. Registre seu aplicativo como um aplicativo do Azure AD. (O acesso a cofres de chaves é gerenciado pelo Azure AD). Isso pode ser feito por meio do portal de gerenciamento do Azure.\

   Ou, se você desejar que seu aplicativo seja autenticado usando um certificado em vez de um segredo do cliente ou senha, será possível usar o cmdlet do PowerShell [AzureRmADApplication novo](/powershell/module/azurerm.resources/new-azurermadapplication). O certificado que você registrar com o Azure Key Vault precisa apenas de sua chave pública. (O aplicativo usará a chave privada.)

2. Permita que o aplicativo registrado acesse o Key Vault criando uma entidade de serviço. É possível fazer isso usando os seguintes comandos do PowerShell:

   ```powershell
   $sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Inclua o Key Vault como uma fonte de configuração em seu aplicativo chamando o método de extensão <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> ao criar uma instância de <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>. Observe que a chamada de `AddAzureKeyVault` requer a ID do aplicativo que foi registrada e permitiu acesso ao Key Vault nas etapas anteriores.

   Você também pode usar uma sobrecarga de `AddAzureKeyVault`, que usa um certificado no lugar do segredo do cliente, apenas incluindo uma referência ao pacote [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory).

> [!IMPORTANT]
> Recomendamos que você registre o Azure Key Vault como o último provedor de configuração, para que ele possa substituir os valores de configuração dos provedores anteriores.

## <a name="additional-resources"></a>Recursos adicionais

- **Usando o Azure Key Vault para proteger segredos do aplicativo** \
  [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Armazenamento seguro dos segredos do aplicativo durante o desenvolvimento** \
  [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](/aspnet/core/security/app-secrets)

- **Configurando a proteção de dados** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](/aspnet/core/security/data-protection/configuration/overview)

- **Gerenciamento e tempo de vida de chaves** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

- Repositório do GitHub **Microsoft.Extensions.Configuration.KeyPerFile**. \
  [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
>[Anterior](developer-app-secrets-storage.md)
>[Próximo](../key-takeaways.md)
