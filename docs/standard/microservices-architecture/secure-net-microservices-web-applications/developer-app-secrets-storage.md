---
title: "Armazenando segredos de aplicativo com segurança durante o desenvolvimento"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Armazenando segredos de aplicativo com segurança durante o desenvolvimento"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f70f7c741da9653745e4f542125986c701b5d22d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="6713b-104">Armazenando segredos de aplicativo com segurança durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="6713b-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="6713b-105">Para se conectar com recursos protegidos e outros serviços, os aplicativos ASP.NET Core normalmente precisam usar cadeias de conexão, senhas ou outras credenciais que contêm informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="6713b-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="6713b-106">Essas informações confidenciais são chamadas *segredos*.</span><span class="sxs-lookup"><span data-stu-id="6713b-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="6713b-107">É uma melhor prática não incluir segredos no código-fonte e certamente não armazenar segredos no controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="6713b-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="6713b-108">Em vez disso, você deve usar o modelo de configuração do ASP.NET Core para ler os segredos de locais mais seguros.</span><span class="sxs-lookup"><span data-stu-id="6713b-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="6713b-109">Você deve separar os segredos para acessar os recursos de desenvolvimento e de preparo dos usados para acessar recursos de produção, pois diferentes pessoas precisarão acessar esses conjuntos diferentes de segredos.</span><span class="sxs-lookup"><span data-stu-id="6713b-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="6713b-110">Para armazenar segredos usados durante o desenvolvimento, as abordagens comuns são armazenar segredos em variáveis de ambiente ou por meio do uso da ferramenta Secret Manager do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6713b-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="6713b-111">Para obter mais armazenamento seguro em ambientes de produção, os microsserviços podem armazenar segredos em um Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="6713b-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="6713b-112">Armazenando segredos em variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="6713b-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="6713b-113">Uma maneira de manter segredos fora do código-fonte é para os desenvolvedores definirem segredos baseados em cadeia de caracteres como [variáveis de ambiente](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) em seus computadores de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="6713b-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="6713b-114">Quando você usa variáveis de ambiente para armazenar segredos com nomes hierárquicos (os aninhados em seções de configuração), crie um nome para as variáveis de ambiente que inclui a hierarquia completa do nome do segredo, delimitado por dois-pontos (:).</span><span class="sxs-lookup"><span data-stu-id="6713b-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="6713b-115">Por exemplo, definir uma variável de ambiente Logging:LogLevel:Default como Depuração seria equivalente a um valor de configuração do seguinte arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="6713b-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="6713b-116">Para acessar esses valores de variáveis de ambiente, o aplicativo precisa apenas chamar AddEnvironmentVariables em seu ConfigurationBuilder ao construir um objeto IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="6713b-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="6713b-117">Observe que as variáveis de ambiente geralmente são armazenadas como texto sem formatação. Portanto, se o computador ou o processo com variáveis de ambiente estiver comprometido, os valores de variável de ambiente estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="6713b-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="6713b-118">Armazenando segredos usando o Secret Manager do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6713b-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="6713b-119">A ferramenta [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) do ASP.NET Core oferece outro método de manter segredos fora do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="6713b-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="6713b-120">Para usar a ferramenta Secret Manager, inclua uma referência de ferramentas (DotNetCliToolReference) ao pacote Microsoft.Extensions.SecretManager.Tools em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="6713b-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="6713b-121">Quando essa dependência estiver presente e tiver sido restaurada, o comando dotnet user-secrets poderá ser usado para definir o valor de segredos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6713b-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="6713b-122">Esses segredos serão armazenados em um arquivo JSON no diretório do perfil do usuário (os detalhes variam de acordo com o sistema operacional), fora do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="6713b-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="6713b-123">Os segredos definidos pela ferramenta Secret Manager são organizados pela propriedade UserSecretsId do projeto que está usando os segredos.</span><span class="sxs-lookup"><span data-stu-id="6713b-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="6713b-124">Portanto, é necessário definir a propriedade UserSecretsId em seu arquivo de projeto (conforme mostrado no trecho de código abaixo).</span><span class="sxs-lookup"><span data-stu-id="6713b-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="6713b-125">A cadeia de caracteres real usada como a ID não é importante, desde que seja exclusiva no projeto.</span><span class="sxs-lookup"><span data-stu-id="6713b-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="6713b-126">Usar os segredos armazenados com o Secret Manager em um aplicativo é realizado chamando AddUserSecrets&lt;T&gt; na instância ConfigurationBuilder para incluir os segredos do aplicativo em sua configuração.</span><span class="sxs-lookup"><span data-stu-id="6713b-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="6713b-127">O parâmetro genérico T deve ser um tipo do assembly ao qual o UserSecretId foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="6713b-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="6713b-128">Normalmente, é bom usar AddUserSecrets&lt;Startup&gt;.</span><span class="sxs-lookup"><span data-stu-id="6713b-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6713b-129">[Anterior] (authorization-net-microservices-web-applications.md) [Próximo] (azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="6713b-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
