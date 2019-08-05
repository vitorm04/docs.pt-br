---
title: Armazenando segredos de aplicativo com segurança durante o desenvolvimento
description: Segurança nos microsserviços e aplicativos Web do .NET – não armazene seus segredos de aplicativo, como senhas, cadeias de conexão ou chaves de API, no controle do código-fonte, entenda as opções que você pode usar no ASP.NET Core, especificamente, saiba como lidar com os "segredos do usuário".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675693"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="ac675-103">Armazenar segredos de aplicativo com segurança durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ac675-103">Store application secrets safely during development</span></span>

<span data-ttu-id="ac675-104">Para se conectar com recursos protegidos e outros serviços, os aplicativos ASP.NET Core normalmente precisam usar cadeias de conexão, senhas ou outras credenciais que contêm informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="ac675-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="ac675-105">Essas informações confidenciais são chamadas *segredos*.</span><span class="sxs-lookup"><span data-stu-id="ac675-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="ac675-106">Uma prática recomendada é não incluir segredos no código-fonte e não armazená-los no controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ac675-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="ac675-107">Em vez disso, você deve usar o modelo de configuração do ASP.NET Core para ler os segredos de locais mais seguros.</span><span class="sxs-lookup"><span data-stu-id="ac675-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="ac675-108">Você precisa separar os segredos para acessar os recursos de desenvolvimento e de preparo daqueles que são usados para acessar recursos de produção, pois diferentes pessoas precisarão acessar esses diferentes conjuntos de segredos.</span><span class="sxs-lookup"><span data-stu-id="ac675-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="ac675-109">Para armazenar segredos usados durante o desenvolvimento, as abordagens comuns são armazenar segredos em variáveis de ambiente ou por meio do uso da ferramenta Secret Manager do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ac675-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="ac675-110">Para obter mais armazenamento seguro em ambientes de produção, os microsserviços podem armazenar segredos em um Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="ac675-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="ac675-111">Armazenar segredos em variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="ac675-111">Store secrets in environment variables</span></span>

<span data-ttu-id="ac675-112">Uma maneira de manter segredos fora do código-fonte é para os desenvolvedores definirem segredos baseados em cadeia de caracteres como [variáveis de ambiente](/aspnet/core/security/app-secrets#environment-variables) em seus computadores de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ac675-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="ac675-113">Ao usar variáveis de ambiente para armazenar segredos com nomes hierárquicos, como aqueles aninhados em seções de configuração, você precisa nomear as variáveis para incluir a hierarquia completa de suas seções, delimitada por dois-pontos (:).</span><span class="sxs-lookup"><span data-stu-id="ac675-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="ac675-114">Por exemplo, a definição de uma variável de ambiente `Logging:LogLevel:Default` para o valor `Debug` seria equivalente a um valor de configuração do arquivo JSON a seguir:</span><span class="sxs-lookup"><span data-stu-id="ac675-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="ac675-115">Para acessar esses valores de variáveis de ambiente, o aplicativo precisa apenas chamar AddEnvironmentVariables em seu ConfigurationBuilder ao construir um objeto IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="ac675-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="ac675-116">Observe que as variáveis de ambiente geralmente são armazenadas como texto sem formatação. Portanto, se o computador ou o processo com variáveis de ambiente estiver comprometido, os valores das variáveis de ambiente estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="ac675-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="ac675-117">Armazenar segredos com o Secret Manager do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ac675-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="ac675-118">A ferramenta [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) do ASP.NET Core oferece outro método de manter segredos fora do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ac675-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="ac675-119">Para usar a ferramenta Secret Manager, instale o pacote **Microsoft.Extensions.Configuration.SecretManager** no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ac675-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="ac675-120">Quando essa dependência estiver presente e tiver sido restaurada, o comando `dotnet user-secrets` poderá ser usado para definir o valor dos segredos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ac675-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="ac675-121">Esses segredos serão armazenados em um arquivo JSON no diretório do perfil do usuário (os detalhes variam de acordo com o sistema operacional), fora do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ac675-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="ac675-122">Os segredos definidos pela ferramenta Secret Manager são organizados pela propriedade `UserSecretsId` do projeto que está usando os segredos.</span><span class="sxs-lookup"><span data-stu-id="ac675-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="ac675-123">Portanto, você precisa definir a propriedade UserSecretsId em seu arquivo de projeto, como mostra o snippet a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac675-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="ac675-124">O valor padrão é um GUID atribuído pelo Visual Studio, mas a cadeia de caracteres real não é importante, desde que seja exclusiva no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ac675-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="ac675-125">O uso de segredos armazenados com o Secret Manager em um aplicativo é realizado chamando `AddUserSecrets<T>` na instância ConfigurationBuilder para incluir os segredos do aplicativo em sua configuração.</span><span class="sxs-lookup"><span data-stu-id="ac675-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="ac675-126">O parâmetro genérico T deve ser um tipo do assembly ao qual o UserSecretId foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="ac675-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="ac675-127">Geralmente, basta usar o `AddUserSecrets<Startup>`.</span><span class="sxs-lookup"><span data-stu-id="ac675-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="ac675-128">O `AddUserSecrets<Startup>()` está incluído nas opções padrão do ambiente de desenvolvimento quando o método `CreateDefaultBuilder` é usado em *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="ac675-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ac675-129">[Anterior](authorization-net-microservices-web-applications.md)
>[Próximo](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="ac675-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
