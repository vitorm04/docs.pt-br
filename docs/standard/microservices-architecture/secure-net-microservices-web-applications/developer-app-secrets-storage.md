---
title: Armazenando segredos de aplicativo com segurança durante o desenvolvimento
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Armazenando segredos de aplicativo com segurança durante o desenvolvimento
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d8dd2da07104d6461d4eec0cb3fccd61c4db71c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="storing-application-secrets-safely-during-development"></a>Armazenando segredos de aplicativo com segurança durante o desenvolvimento

Para se conectar com recursos protegidos e outros serviços, os aplicativos ASP.NET Core normalmente precisam usar cadeias de conexão, senhas ou outras credenciais que contêm informações confidenciais. Essas informações confidenciais são chamadas *segredos*. É uma melhor prática não incluir segredos no código-fonte e certamente não armazenar segredos no controle do código-fonte. Em vez disso, você deve usar o modelo de configuração do ASP.NET Core para ler os segredos de locais mais seguros.

Você deve separar os segredos para acessar os recursos de desenvolvimento e de preparo dos usados para acessar recursos de produção, pois diferentes pessoas precisarão acessar esses conjuntos diferentes de segredos. Para armazenar segredos usados durante o desenvolvimento, as abordagens comuns são armazenar segredos em variáveis de ambiente ou por meio do uso da ferramenta Secret Manager do ASP.NET Core. Para obter mais armazenamento seguro em ambientes de produção, os microsserviços podem armazenar segredos em um Azure Key Vault.

## <a name="storing-secrets-in-environment-variables"></a>Armazenando segredos em variáveis de ambiente

Uma maneira de manter segredos fora do código-fonte é para os desenvolvedores definirem segredos baseados em cadeia de caracteres como [variáveis de ambiente](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) em seus computadores de desenvolvimento. Quando você usa variáveis de ambiente para armazenar segredos com nomes hierárquicos (os aninhados em seções de configuração), crie um nome para as variáveis de ambiente que inclui a hierarquia completa do nome do segredo, delimitado por dois-pontos (:).

Por exemplo, definir uma variável de ambiente Logging:LogLevel:Default como Depuração seria equivalente a um valor de configuração do seguinte arquivo JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Para acessar esses valores de variáveis de ambiente, o aplicativo precisa apenas chamar AddEnvironmentVariables em seu ConfigurationBuilder ao construir um objeto IConfigurationRoot.

Observe que as variáveis de ambiente geralmente são armazenadas como texto sem formatação. Portanto, se o computador ou o processo com variáveis de ambiente estiver comprometido, os valores de variável de ambiente estarão visíveis.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Armazenando segredos usando o Secret Manager do ASP.NET Core

A ferramenta [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) do ASP.NET Core oferece outro método de manter segredos fora do código-fonte. Para usar a ferramenta Secret Manager, inclua uma referência de ferramentas (DotNetCliToolReference) ao pacote Microsoft.Extensions.SecretManager.Tools em seu arquivo de projeto. Quando essa dependência estiver presente e tiver sido restaurada, o comando dotnet user-secrets poderá ser usado para definir o valor de segredos na linha de comando. Esses segredos serão armazenados em um arquivo JSON no diretório do perfil do usuário (os detalhes variam de acordo com o sistema operacional), fora do código-fonte.

Os segredos definidos pela ferramenta Secret Manager são organizados pela propriedade UserSecretsId do projeto que está usando os segredos. Portanto, é necessário definir a propriedade UserSecretsId em seu arquivo de projeto (conforme mostrado no trecho de código abaixo). A cadeia de caracteres real usada como a ID não é importante, desde que seja exclusiva no projeto.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Usar os segredos armazenados com o Secret Manager em um aplicativo é realizado chamando AddUserSecrets&lt;T&gt; na instância ConfigurationBuilder para incluir os segredos do aplicativo em sua configuração. O parâmetro genérico T deve ser um tipo do assembly ao qual o UserSecretId foi aplicado. Normalmente, é bom usar AddUserSecrets&lt;Startup&gt;.


>[!div class="step-by-step"]
[Anterior] (authorization-net-microservices-web-applications.md) [Próximo] (azure-key-vault-protects-secrets.md)
