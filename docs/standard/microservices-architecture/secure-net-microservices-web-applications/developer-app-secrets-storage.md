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
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="7c005-104">Armazenar segredos do aplicativo com segurança durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="7c005-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="7c005-105">Para se conectar com recursos protegidos e outros serviços, aplicativos do ASP.NET Core normalmente precisam usar cadeias de caracteres de conexão, senhas ou outras credenciais que contenham informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="7c005-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="7c005-106">Essas informações confidenciais são chamadas *segredos*.</span><span class="sxs-lookup"><span data-stu-id="7c005-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="7c005-107">É uma prática recomendada para não incluir os segredos no código-fonte e certamente não armazenar segredos no controle de origem.</span><span class="sxs-lookup"><span data-stu-id="7c005-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="7c005-108">Em vez disso, você deve usar o modelo de configuração do ASP.NET Core para ler os segredos de locais mais seguras.</span><span class="sxs-lookup"><span data-stu-id="7c005-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="7c005-109">Você deve separar os segredos para acessar o desenvolvimento e teste recursos daquelas usadas para acessar recursos de produção, pois diferentes pessoas precisarão de acesso a esses conjuntos diferentes de segredos.</span><span class="sxs-lookup"><span data-stu-id="7c005-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="7c005-110">Para armazenar segredos usados durante o desenvolvimento, abordagens comuns são ou armazenar segredos em variáveis de ambiente ou usando a ferramenta Gerenciador de segredo do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7c005-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="7c005-111">Para o armazenamento mais seguro em ambientes de produção, microservices pode armazenar segredos em um cofre de chaves do Azure.</span><span class="sxs-lookup"><span data-stu-id="7c005-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="7c005-112">Armazenar segredos em variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="7c005-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="7c005-113">É uma maneira de manter segredos fora do código-fonte para desenvolvedores definir os segredos baseada em cadeia de caracteres como [variáveis de ambiente](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) em seus computadores de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="7c005-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="7c005-114">Quando você usar variáveis de ambiente para armazenar segredos com nomes hierárquicos (aqueles aninhados em seções de configuração), crie um nome para as variáveis de ambiente que inclui a hierarquia completa do nome do segredo, delimitadas por dois-pontos (:).</span><span class="sxs-lookup"><span data-stu-id="7c005-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="7c005-115">Por exemplo, definir uma variável de ambiente log: LogLevel:Default para depuração seria equivalente a um valor de configuração do seguinte arquivo JSON:</span><span class="sxs-lookup"><span data-stu-id="7c005-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="7c005-116">Para acessar esses valores de variáveis de ambiente, o aplicativo precisa apenas chamar AddEnvironmentVariables em seu ConfigurationBuilder ao construir um objeto IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="7c005-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="7c005-117">Observe que as variáveis de ambiente geralmente são armazenadas como texto sem formatação, portanto se o processo com as variáveis de ambiente ou a máquina estiver comprometido, os valores de variáveis de ambiente será visíveis.</span><span class="sxs-lookup"><span data-stu-id="7c005-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="7c005-118">Armazenar segredos usando o Gerenciador de segredo do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7c005-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="7c005-119">O ASP.NET Core [Manager segredo](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) ferramenta fornece outro método para manter os segredos fora do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="7c005-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="7c005-120">Para usar a ferramenta Gerenciador de segredo, inclua uma referência de ferramentas (DotNetCliToolReference) para o pacote de Microsoft.Extensions.SecretManager.Tools no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="7c005-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="7c005-121">Quando essa dependência está presente e foi restaurada, o comando de segredos do usuário do dotnet pode ser usado para definir o valor de segredos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7c005-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="7c005-122">Esses segredos serão armazenados em um arquivo JSON no diretório do usuário perfil (detalhes variam de acordo com o sistema operacional), fora do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="7c005-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="7c005-123">Segredos definidos pela ferramenta Gerenciador de segredo são organizados pela propriedade UserSecretsId do projeto que está usando os segredos.</span><span class="sxs-lookup"><span data-stu-id="7c005-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="7c005-124">Portanto, você deve ser-se de definir a propriedade UserSecretsId no arquivo de projeto (conforme mostrado no trecho abaixo).</span><span class="sxs-lookup"><span data-stu-id="7c005-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="7c005-125">A cadeia de caracteres real usada como a ID não é importante, desde que ele seja exclusivo no projeto.</span><span class="sxs-lookup"><span data-stu-id="7c005-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="7c005-126">Usar os segredos armazenados com o Gerenciador de segredo em um aplicativo é feito chamando AddUserSecrets&lt;T&gt; na instância do ConfigurationBuilder para incluir os segredos do aplicativo em sua configuração.</span><span class="sxs-lookup"><span data-stu-id="7c005-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="7c005-127">O parâmetro genérico T deve ser um tipo do assembly que o UserSecretId foi aplicada.</span><span class="sxs-lookup"><span data-stu-id="7c005-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="7c005-128">Normalmente, usando AddUserSecrets&lt;inicialização&gt; é bom.</span><span class="sxs-lookup"><span data-stu-id="7c005-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7c005-129">[Anterior] (autorização-net-microservices-web-applications.md) [Avançar] (azure-key-cofre-protege-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="7c005-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
