---
title: Armazenando segredos de aplicativo com segurança durante o desenvolvimento
description: Segurança nos microsserviços e aplicativos Web do .NET – não armazene seus segredos de aplicativo, como senhas, cadeias de conexão ou chaves de API, no controle do código-fonte, entenda as opções que você pode usar no ASP.NET Core, especificamente, saiba como lidar com os "segredos do usuário".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361983"
---
# <a name="store-application-secrets-safely-during-development"></a>Armazenar segredos de aplicativo com segurança durante o desenvolvimento

Para se conectar com recursos protegidos e outros serviços, os aplicativos ASP.NET Core normalmente precisam usar cadeias de conexão, senhas ou outras credenciais que contêm informações confidenciais. Essas informações confidenciais são chamadas *segredos*. Uma prática recomendada é não incluir segredos no código-fonte e não armazená-los no controle do código-fonte. Em vez disso, você deve usar o modelo de configuração do ASP.NET Core para ler os segredos de locais mais seguros.

Você precisa separar os segredos para acessar os recursos de desenvolvimento e de preparo daqueles que são usados para acessar recursos de produção, pois diferentes pessoas precisarão acessar esses diferentes conjuntos de segredos. Para armazenar segredos usados durante o desenvolvimento, as abordagens comuns são armazenar segredos em variáveis de ambiente ou por meio do uso da ferramenta Secret Manager do ASP.NET Core. Para obter mais armazenamento seguro em ambientes de produção, os microsserviços podem armazenar segredos em um Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Armazenar segredos em variáveis de ambiente

Uma maneira de manter segredos fora do código-fonte é para os desenvolvedores definirem segredos baseados em cadeia de caracteres como [variáveis de ambiente](/aspnet/core/security/app-secrets#environment-variables) em seus computadores de desenvolvimento. Ao usar variáveis de ambiente para armazenar segredos com nomes hierárquicos, como aqueles aninhados em seções de configuração, você precisa nomear as variáveis para incluir a hierarquia completa de suas seções, delimitada por dois-pontos (:).

Por exemplo, a definição de uma variável de ambiente `Logging:LogLevel:Default` para o valor `Debug` seria equivalente a um valor de configuração do arquivo JSON a seguir:

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

Observe que as variáveis de ambiente geralmente são armazenadas como texto sem formatação. Portanto, se o computador ou o processo com variáveis de ambiente estiver comprometido, os valores das variáveis de ambiente estarão visíveis.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Armazenar segredos com o Secret Manager do ASP.NET Core

A ferramenta [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) do ASP.NET Core oferece outro método de manter segredos fora do código-fonte. Para usar a ferramenta Secret Manager, instale o pacote **Microsoft.Extensions.Configuration.SecretManager** no arquivo de projeto. Quando essa dependência estiver presente e tiver sido restaurada, o comando `dotnet user-secrets` poderá ser usado para definir o valor dos segredos na linha de comando. Esses segredos serão armazenados em um arquivo JSON no diretório do perfil do usuário (os detalhes variam de acordo com o sistema operacional), fora do código-fonte.

Os segredos definidos pela ferramenta Secret Manager são organizados pela propriedade `UserSecretsId` do projeto que está usando os segredos. Portanto, você precisa definir a propriedade UserSecretsId em seu arquivo de projeto, como mostra o snippet a seguir. O valor padrão é um GUID atribuído pelo Visual Studio, mas a cadeia de caracteres real não é importante, desde que seja exclusiva no seu computador.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

O uso de segredos armazenados com o Secret Manager em um aplicativo é realizado chamando `AddUserSecrets<T>` na instância ConfigurationBuilder para incluir os segredos do aplicativo em sua configuração. O parâmetro genérico T deve ser um tipo do assembly ao qual o UserSecretId foi aplicado. Geralmente, basta usar o `AddUserSecrets<Startup>`.

O `AddUserSecrets<Startup>()` está incluído nas opções padrão do ambiente de desenvolvimento quando o método `CreateDefaultBuilder` é usado em *Program.cs*.

>[!div class="step-by-step"]
>[Anterior](authorization-net-microservices-web-applications.md)
>[Próximo](azure-key-vault-protects-secrets.md)
