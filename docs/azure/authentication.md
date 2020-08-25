---
title: Noções básicas sobre a autenticação nas bibliotecas do Azure para .NET
description: Explica as diferentes maneiras de se autenticar com o SDK do Azure para .NET.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: bc2fce919d88a528f21df9f561cbe33e1119762a
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811373"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="47850-103">Autenticar com o SDK do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="47850-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="47850-104">Recomendado: Azure. Identity</span><span class="sxs-lookup"><span data-stu-id="47850-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="47850-105">Os pacotes mais recentes no SDK do Azure para .NET usam um pacote de autenticação comum para autenticar, `Azure.Identity` .</span><span class="sxs-lookup"><span data-stu-id="47850-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="47850-106">`Azure.Identity`O uso do é recomendado em outros mecanismos de autenticação descritos mais adiante neste documento.</span><span class="sxs-lookup"><span data-stu-id="47850-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="47850-107">Os pacotes que dão suporte às credenciais fornecidas pelo `Azure.Identity` são criados sobre o `Azure.Core` e têm identificadores de pacote começando com o *Azure*.</span><span class="sxs-lookup"><span data-stu-id="47850-107">Packages supporting the credentials provided by `Azure.Identity` are built on top of `Azure.Core` and have package identifiers starting with *Azure*.</span></span> <span data-ttu-id="47850-108">[Consulte a lista](packages.md) de pacotes para obter um inventário das embalagens que usam `Azure.Core` .</span><span class="sxs-lookup"><span data-stu-id="47850-108">[See the package list](packages.md) for an inventory of packages that use `Azure.Core`.</span></span>

<span data-ttu-id="47850-109">Para obter instruções completas sobre como usar o `Azure.Identity` em seu projeto, consulte a documentação para o [cliente de identidade do Azure para .net](/dotnet/api/overview/azure/identity-readme).</span><span class="sxs-lookup"><span data-stu-id="47850-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="47850-110">Consulte o [exemplo de identidade, gerenciamento de recursos e armazenamento do Azure](/samples/dotnet/samples/azure-identity-resource-management-storage/) para obter exemplos de como usar a identidade do Azure para gerenciar e acessar recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="47850-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="47850-111">Para autenticar com bibliotecas que não dão suporte ao Azure. Identity, consulte o restante deste tópico.</span><span class="sxs-lookup"><span data-stu-id="47850-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="47850-112">Acessar recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="47850-112">Access Azure resources</span></span>

<span data-ttu-id="47850-113">Para interagir com os recursos do Azure, como recuperar um segredo de Key Vault ou armazenar um blob no armazenamento, muitas bibliotecas de serviço do Azure exigem uma cadeia de conexão ou chaves para autenticação.</span><span class="sxs-lookup"><span data-stu-id="47850-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="47850-114">Por exemplo, o banco de dados SQL usa uma [cadeia de conexão SQL padrão](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="47850-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="47850-115">As cadeias de conexão de serviço são usadas em outros serviços do Azure, como [CosmosDB](/azure/cosmos-db/), [cache do Azure para Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)e [barramento de serviço](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="47850-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="47850-116">Você pode obter essas cadeias de caracteres usando o portal do Azure, a CLI ou o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47850-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="47850-117">Você também pode usar as bibliotecas de gerenciamento do Azure para .NET a fim de consultar recursos para criar cadeias de conexão no seu código.</span><span class="sxs-lookup"><span data-stu-id="47850-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="47850-118">Os métodos para usar uma cadeia de conexão variam de acordo com o produto.</span><span class="sxs-lookup"><span data-stu-id="47850-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="47850-119">[Consulte a documentação do seu produto do Azure](/azure/?product=featured).</span><span class="sxs-lookup"><span data-stu-id="47850-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="47850-120">Gerenciar recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="47850-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="47850-121">Agora que a entidade de serviço foi criada, duas opções estão disponíveis para fazer a autenticação na entidade de serviço a fim de criar e gerenciar recursos.</span><span class="sxs-lookup"><span data-stu-id="47850-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="47850-122">Para ambas as opções, você precisará adicionar os seguintes pacotes NuGet ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="47850-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="47850-123">Fazer autenticação com credenciais do token</span><span class="sxs-lookup"><span data-stu-id="47850-123">Authenticate with token credentials</span></span>

<span data-ttu-id="47850-124">O primeiro método é compilar o objeto de credencial de token no código.</span><span class="sxs-lookup"><span data-stu-id="47850-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="47850-125">Você deve armazenar as credenciais com segurança em um arquivo de configuração, no registro ou no Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="47850-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="47850-126">Use os valores *clientId*, *clientSecret* e *tenantId* da saída do JSON quando criou a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="47850-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="47850-127">Em seguida, crie o objeto `Azure` do ponto de entrada para começar a trabalhar com a API:</span><span class="sxs-lookup"><span data-stu-id="47850-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

<span data-ttu-id="47850-128">É recomendável que você forneça explicitamente a *SubscriptionId* da saída JSON para o `Azure` objeto:</span><span class="sxs-lookup"><span data-stu-id="47850-128">It is recommended that you explicitly provide the *subscriptionId* from the JSON output to the `Azure` object:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="47850-129">Autenticação baseada em arquivo</span><span class="sxs-lookup"><span data-stu-id="47850-129">File-based authentication</span></span>

<span data-ttu-id="47850-130">A autenticação baseada em arquivo permite que você coloque as credenciais da entidade de serviço em um arquivo de texto sem formatação e proteja-o no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="47850-130">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="47850-131">Leia o conteúdo do arquivo e crie o objeto `Azure` de ponto de entrada para começar a trabalhar com a API:</span><span class="sxs-lookup"><span data-stu-id="47850-131">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
