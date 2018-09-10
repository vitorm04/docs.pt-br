---
title: Usando o Azure Key Vault para proteger segredos no momento da produção
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Usando o Azure Key Vault para proteger segredos no momento da produção
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5738b81c90c886aff48451742881807dc09a9ff9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863981"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Usando o Azure Key Vault para proteger segredos no momento da produção

Os segredos armazenados como variáveis de ambiente ou armazenados pela ferramenta Secret Manager ainda são armazenados localmente e descriptografados no computador. Uma opção mais segura para armazenar segredos é o [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que oferece um local seguro e central para armazenar chaves e segredos.

O pacote Microsoft.Extensions.Configuration.AzureKeyVault permite que um aplicativo do ASP.NET Core leia informações de configuração do Azure Key Vault. Para começar a usar os segredos de um Azure Key Vault, siga estas etapas:

Primeiro, registre seu aplicativo como um aplicativo Azure AD. (O acesso a cofres de chaves é gerenciado pelo Azure AD). Isso pode ser feito por meio do Portal de Gerenciamento do Azure.

Ou, se você desejar que seu aplicativo seja autenticado usando um certificado em vez de um segredo do cliente ou senha, será possível usar o cmdlet do PowerShell [AzureRmADApplication novo](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication). O certificado que você registrar com o Azure Key Vault precisa apenas de sua chave pública. (O aplicativo usará a chave privada.)

Segundo, conceda ao aplicativo registrado acesso ao cofre de chaves criando uma nova entidade de serviço. É possível fazer isso usando os seguintes comandos do PowerShell:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Em terceiro lugar, inclua o cofre de chaves como uma fonte de configuração em seu aplicativo chamando o método de extensão IConfigurationBuilder.AddAzureKeyVault quando você criar uma instância IConfigurationRoot. Observe que chamar AddAzureKeyVault exigirá a ID do aplicativo que foi registrado e que recebeu acesso ao cofre de chaves nas etapas anteriores.

  No momento, o .NET Standard e o .NET Core dão suporte à obtenção de informações de configuração de um Azure Key Vault usando uma ID de cliente e o segredo do cliente. Os aplicativos do .NET Framework podem usar uma sobrecarga de IConfigurationBuilder.AddAzureKeyVault que usa um certificado no lugar do segredo do cliente. No momento da redação deste artigo, o trabalho está [em andamento](https://github.com/aspnet/Configuration/issues/605) para disponibilizar essa sobrecarga no .NET Standard e no .NET Core. Até que a sobrecarga AddAzureKeyVault que aceita um certificado esteja disponível, os aplicativos do ASP.NET Core poderão acessar um Azure Key Vault com autenticação baseada em certificado criando explicitamente um objeto KeyVaultClient, conforme mostrado no exemplo a seguir:

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

Neste exemplo, a chamada a AddAzureKeyVault vem no final do registro do provedor de configuração. É uma melhor prática registrar o Azure Key Vault como o último provedor de configuração para que ele tenha uma oportunidade de substituir valores de configuração de provedores anteriores, e para que nenhum valor de configuração de outras fontes substituam os do cofre de chaves.

## <a name="additional-resources"></a>Recursos adicionais

-   **Usando o Azure Key Vault para proteger segredos do aplicativo**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Armazenamento seguro dos segredos do aplicativo durante o desenvolvimento**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Configurando a proteção de dados**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Gerenciamento de chaves e tempo de vida**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   Repositório do GitHub **Microsoft.Extensions.Configuration.KeyPerFile**.
    [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
[Anterior](developer-app-secrets-storage.md)
[Próximo](../key-takeaways.md)
