---
title: "Armazenar segredos do aplicativo com segurança durante o desenvolvimento"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Armazenar segredos do aplicativo com segurança durante o desenvolvimento"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f1b8b257a3e677c7e665e1d394a8adf7e651bec2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="storing-application-secrets-safely-during-development"></a>Armazenar segredos do aplicativo com segurança durante o desenvolvimento

Para se conectar com recursos protegidos e outros serviços, aplicativos do ASP.NET Core normalmente precisam usar cadeias de caracteres de conexão, senhas ou outras credenciais que contenham informações confidenciais. Essas informações confidenciais são chamadas *segredos*. É uma prática recomendada para não incluir os segredos no código-fonte e certamente não armazenar segredos no controle de origem. Em vez disso, você deve usar o modelo de configuração do ASP.NET Core para ler os segredos de locais mais seguras.

Você deve separar os segredos para acessar o desenvolvimento e teste recursos daquelas usadas para acessar recursos de produção, pois diferentes pessoas precisarão de acesso a esses conjuntos diferentes de segredos. Para armazenar segredos usados durante o desenvolvimento, abordagens comuns são ou armazenar segredos em variáveis de ambiente ou usando a ferramenta Gerenciador de segredo do ASP.NET Core. Para o armazenamento mais seguro em ambientes de produção, microservices pode armazenar segredos em um cofre de chaves do Azure.

## <a name="storing-secrets-in-environment-variables"></a>Armazenar segredos em variáveis de ambiente

É uma maneira de manter segredos fora do código-fonte para desenvolvedores definir os segredos baseada em cadeia de caracteres como [variáveis de ambiente](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) em seus computadores de desenvolvimento. Quando você usar variáveis de ambiente para armazenar segredos com nomes hierárquicos (aqueles aninhados em seções de configuração), crie um nome para as variáveis de ambiente que inclui a hierarquia completa do nome do segredo, delimitadas por dois-pontos (:).

Por exemplo, definir uma variável de ambiente log: LogLevel:Default para depuração seria equivalente a um valor de configuração do seguinte arquivo JSON:

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

Observe que as variáveis de ambiente geralmente são armazenadas como texto sem formatação, portanto se o processo com as variáveis de ambiente ou a máquina estiver comprometido, os valores de variáveis de ambiente será visíveis.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Armazenar segredos usando o Gerenciador de segredo do ASP.NET Core

O ASP.NET Core [Manager segredo](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) ferramenta fornece outro método para manter os segredos fora do código-fonte. Para usar a ferramenta Gerenciador de segredo, inclua uma referência de ferramentas (DotNetCliToolReference) para o pacote de Microsoft.Extensions.SecretManager.Tools no seu arquivo de projeto. Quando essa dependência está presente e foi restaurada, o comando de segredos do usuário do dotnet pode ser usado para definir o valor de segredos da linha de comando. Esses segredos serão armazenados em um arquivo JSON no diretório do usuário perfil (detalhes variam de acordo com o sistema operacional), fora do código-fonte.

Segredos definidos pela ferramenta Gerenciador de segredo são organizados pela propriedade UserSecretsId do projeto que está usando os segredos. Portanto, você deve ser-se de definir a propriedade UserSecretsId no arquivo de projeto (conforme mostrado no trecho abaixo). A cadeia de caracteres real usada como a ID não é importante, desde que ele seja exclusivo no projeto.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Usar os segredos armazenados com o Gerenciador de segredo em um aplicativo é feito chamando AddUserSecrets&lt;T&gt; na instância do ConfigurationBuilder para incluir os segredos do aplicativo em sua configuração. O parâmetro genérico T deve ser um tipo do assembly que o UserSecretId foi aplicada. Normalmente, usando AddUserSecrets&lt;inicialização&gt; é bom.


>[!div class="step-by-step"]
[Anterior] (autorização-net-microservices-web-applications.md) [Avançar] (azure-key-cofre-protege-secrets.md)
