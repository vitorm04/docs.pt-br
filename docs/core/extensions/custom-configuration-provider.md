---
title: Implementar um provedor de configuração personalizado no .NET
description: Saiba como implementar um provedor de configuração personalizada em aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: how-to
ms.openlocfilehash: 968bf202eeea32742444681260d5ab0b27b403f9
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720732"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="96d71-103">Implementar um provedor de configuração personalizado no .NET</span><span class="sxs-lookup"><span data-stu-id="96d71-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="96d71-104">Há muitos [provedores de configuração](configuration-providers.md) disponíveis para fontes de configuração comuns, como arquivos JSON, XML e ini.</span><span class="sxs-lookup"><span data-stu-id="96d71-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="96d71-105">Talvez seja necessário implementar um provedor de configuração personalizado quando um dos provedores disponíveis não atender às suas necessidades de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d71-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="96d71-106">Neste artigo, você aprenderá a implementar um provedor de configuração personalizado que se baseia em um banco de dados como sua fonte de configuração.</span><span class="sxs-lookup"><span data-stu-id="96d71-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="96d71-107">Provedor de Configuração personalizado</span><span class="sxs-lookup"><span data-stu-id="96d71-107">Custom configuration provider</span></span>

<span data-ttu-id="96d71-108">O aplicativo de exemplo demonstra como criar um provedor de configuração básica que lê pares chave-valor de configuração de um banco de dados usando [Entity Framework (EF) Core](/ef/core).</span><span class="sxs-lookup"><span data-stu-id="96d71-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="96d71-109">O provedor tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="96d71-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="96d71-110">O banco de dados EF na memória é usado para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="96d71-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="96d71-111">Para usar um banco de dados que exija uma cadeia de conexão, implemente um `ConfigurationBuilder` secundário para fornecer a cadeia de conexão de outro provedor de configuração.</span><span class="sxs-lookup"><span data-stu-id="96d71-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="96d71-112">O provedor lê uma tabela de banco de dados na configuração na inicialização.</span><span class="sxs-lookup"><span data-stu-id="96d71-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="96d71-113">O provedor não consulta o banco de dados em uma base por chave.</span><span class="sxs-lookup"><span data-stu-id="96d71-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="96d71-114">O recarregamento na alteração não está implementado, portanto, a atualização do banco de dados após a inicialização do aplicativo não tem efeito sobre a configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d71-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="96d71-115">Defina uma `Settings` entidade de tipo de registro para armazenar valores de configuração no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="96d71-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="96d71-116">Por exemplo, você pode adicionar um arquivo *Settings.cs* em sua pasta *modelos* :</span><span class="sxs-lookup"><span data-stu-id="96d71-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="96d71-117">Para obter informações sobre tipos de registro, consulte [tipos de registro em C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="96d71-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="96d71-118">Adicione um `EntityConfigurationContext` para armazenar e acessar os valores configurados.</span><span class="sxs-lookup"><span data-stu-id="96d71-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="96d71-119">*Providers/EntityConfigurationContext. cs*:</span><span class="sxs-lookup"><span data-stu-id="96d71-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="96d71-120">Crie uma classe que implementa <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span><span class="sxs-lookup"><span data-stu-id="96d71-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="96d71-121">*Providers/EntityConfigurationSource. cs*:</span><span class="sxs-lookup"><span data-stu-id="96d71-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="96d71-122">Crie o provedor de configuração personalizado através da herança de <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span><span class="sxs-lookup"><span data-stu-id="96d71-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="96d71-123">O provedor de configuração inicializa o banco de dados quando ele está vazio.</span><span class="sxs-lookup"><span data-stu-id="96d71-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="96d71-124">Como as chaves de configuração não diferenciam maiúsculas de minúsculas, o dicionário usado para inicializar o banco de dados é criado com o comparador que não diferencia maiúsculas de minúsculas ([StringComparer. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span><span class="sxs-lookup"><span data-stu-id="96d71-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="96d71-125">*Providers/EntityConfigurationProvider. cs*:</span><span class="sxs-lookup"><span data-stu-id="96d71-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="96d71-126">Um `AddEntityConfiguration` método de extensão permite adicionar a origem de configuração a uma <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instância do.</span><span class="sxs-lookup"><span data-stu-id="96d71-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="96d71-127">*Extensões/ConfigurationBuilderExtensions. cs*:</span><span class="sxs-lookup"><span data-stu-id="96d71-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="96d71-128">O código a seguir mostra como usar o `EntityConfigurationProvider` personalizado em *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="96d71-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="21-22":::

## <a name="see-also"></a><span data-ttu-id="96d71-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="96d71-129">See also</span></span>

- [<span data-ttu-id="96d71-130">Configuração no .NET</span><span class="sxs-lookup"><span data-stu-id="96d71-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="96d71-131">Provedores de configuração no .NET</span><span class="sxs-lookup"><span data-stu-id="96d71-131">Configuration providers in .NET</span></span>](configuration-providers.md)
