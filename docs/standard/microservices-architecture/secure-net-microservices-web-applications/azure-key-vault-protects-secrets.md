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
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Usando o Cofre de chaves do Azure para proteger segredos em tempo de produção

Segredos armazenadas como variáveis de ambiente ou armazenada pela ferramenta Gerenciador de segredo ainda são armazenados localmente e descriptografados no computador. É uma opção mais segura para armazenar segredos [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), que fornece um local central seguro para armazenar chaves e segredos.

O pacote de Microsoft.Extensions.Configuration.AzureKeyVault permite que um aplicativo do ASP.NET Core para ler informações de configuração do Cofre de chaves do Azure. Para começar a usar os segredos de um cofre de chaves do Azure, você deve seguir estas etapas:

Primeiro, registre seu aplicativo como um aplicativo do AD do Azure. (Acesso a cofres de chaves é gerenciado pelo AD do Azure). Isso pode ser feito por meio do portal de gerenciamento do Azure.

Como alternativa, se você quiser que seu aplicativo para autenticar usando um certificado em vez de um segredo de cliente ou a senha, você pode usar o [AzureRmADApplication novo](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) cmdlet do PowerShell. O certificado que você se registrar com o Cofre de chaves do Azure precisa somente sua chave pública. (O aplicativo usará a chave privada).

Segundo, dê o acesso do aplicativo registrado para o Cofre de chaves ao criar uma nova entidade de serviço. Você pode fazer isso usando os seguintes comandos do PowerShell:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Em terceiro lugar, incluem o Cofre de chave como uma fonte de configuração em seu aplicativo chamando o método de extensão IConfigurationBuilder.AddAzureKeyVault quando você cria uma instância de IConfigurationRoot. Observe que a chamada AddAzureKeyVault exigirá a ID do aplicativo que foi registrada e recebe acesso para o Cofre de chaves nas etapas anteriores.

  Atualmente, padrão do .NET e .NET Core oferecem suporte a obtenção de informações de configuração de um cofre de chaves do Azure usando uma ID de cliente e o segredo do cliente. Aplicativos do .NET framework podem usar uma sobrecarga de IConfigurationBuilder.AddAzureKeyVault que usa um certificado no lugar de segredo do cliente. Redação deste artigo, o trabalho é [em andamento](https://github.com/aspnet/Configuration/issues/605) para disponibilizar essa sobrecarga no .NET Core e .NET padrão. Até que a sobrecarga de AddAzureKeyVault que aceita que um certificado estiver disponível, os aplicativos ASP.NET Core podem acessar um cofre de chaves do Azure com autenticação baseada em certificado criando explicitamente um objeto KeyVaultClient, conforme mostrado no exemplo a seguir:

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

Neste exemplo, a chamada para AddAzureKeyVault é fornecido no final do registro do provedor de configuração. É uma prática recomendada para registrar o Cofre de chaves do Azure como o último provedor de configuração para que ele tenha a oportunidade de substituem os valores de configuração de provedores anteriores, e para que nenhum valor de configuração de outras fontes substituem aquelas do key vault.

## <a name="additional-resources"></a>Recursos adicionais

-   **Usando o Cofre de chaves do Azure para proteger segredos do aplicativo**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Armazenamento seguro de segredos do aplicativo durante o desenvolvimento**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Configurando a proteção de dados**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Tempo de vida e gerenciamento de chave**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#proteção de dados-configurações padrão*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** Repositório do GitHub.
    [*https://GitHub.com/ASPNET/Configuration/Tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Anterior] (desenvolvedor-aplicativo-segredos-storage.md) [Avançar] (... / chave takeaways.md)
