---
title: Novidades no C# 7.1
description: Uma visão geral dos novos recursos no C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728648"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="7dbb5-103">Novidades no C# 7.1</span><span class="sxs-lookup"><span data-stu-id="7dbb5-103">What's new in C# 7.1</span></span>

<span data-ttu-id="7dbb5-104">O C# 7.1 é a primeira versão de ponto da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="7dbb5-105">Ele marca uma cadência de versão maior para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="7dbb5-106">Use os novos recursos mais cedo, de preferência, quando cada novo recurso estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="7dbb5-107">O C# 7.1 adiciona a capacidade de configurar o compilador para que ele corresponda a uma versão especificada da linguagem.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="7dbb5-108">Isso permite que você separe a decisão de atualizar ferramentas da decisão de atualizar versões da linguagem.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="7dbb5-109">O C# 7.1 adiciona a [seleção de versão da linguagem](../language-reference/configure-language-version.md) elemento de configuração, três novos recursos de linguagem e um novo comportamento do compilador.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="7dbb5-110">Os novos recursos de linguagem nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="7dbb5-111">`async` Método `Main`</span><span class="sxs-lookup"><span data-stu-id="7dbb5-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="7dbb5-112">O ponto de entrada para um aplicativo pode ter o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="7dbb5-113">`default` Expressões literais</span><span class="sxs-lookup"><span data-stu-id="7dbb5-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="7dbb5-114">Use expressões literais padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="7dbb5-115">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="7dbb5-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="7dbb5-116">Em muitos casos, os nomes dos elementos de tupla podem ser inferidos com base na inicialização da tupla.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="7dbb5-117">Por fim, o compilador traz duas opções `/refout` e `/refonly`, que controlam a [geração de assembly de referência](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="7dbb5-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="7dbb5-118">Para usar as últimas funcionalidades em uma versão de ponto, você precisa [configurar a versão da linguagem do compilador](../language-reference/configure-language-version.md) e selecionar a versão.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-118">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="7dbb5-119">Async main</span><span class="sxs-lookup"><span data-stu-id="7dbb5-119">Async main</span></span>

<span data-ttu-id="7dbb5-120">Um método *async main* permite que você use `await` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-120">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="7dbb5-121">Anteriormente, você precisava escrever:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-121">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="7dbb5-122">Agora, você pode escrever:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-122">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="7dbb5-123">Se o programa não retorna um código de saída, declare um método `Main` que retorna um <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-123">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="7dbb5-124">Leia mais sobre os detalhes no tópico [async main](../programming-guide/main-and-command-args/index.md) no guia de programação.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-124">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="7dbb5-125">Expressões literais padrão</span><span class="sxs-lookup"><span data-stu-id="7dbb5-125">Default literal expressions</span></span>

<span data-ttu-id="7dbb5-126">Expressões literais padrão são uma melhoria das expressões de valor padrão.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-126">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="7dbb5-127">Essas expressões inicializam uma variável com o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-127">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="7dbb5-128">Nos casos em que você anteriormente escrevia:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-128">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="7dbb5-129">Agora você pode omitir o tipo no lado direito da inicialização:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-129">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="7dbb5-130">Saiba mais sobre essa melhoria no tópico do Guia de Programação do C# em [expressões de valor padrão](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7dbb5-130">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="7dbb5-131">Essa melhoria também altera algumas das regras de análise da [palavra-chave padrão](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="7dbb5-131">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="7dbb5-132">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="7dbb5-132">Inferred tuple element names</span></span>

<span data-ttu-id="7dbb5-133">Esse recurso é uma pequena melhoria do recurso de tuplas introduzido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-133">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="7dbb5-134">Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja usar para os elementos de tupla:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-134">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="7dbb5-135">Os nomes dos elementos de tupla podem ser inferidos com base nas variáveis usadas para inicializar a tupla no C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="7dbb5-135">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="7dbb5-136">Saiba mais sobre esse recurso no tópico [Tuplas](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="7dbb5-136">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="7dbb5-137">Geração de assembly de referência</span><span class="sxs-lookup"><span data-stu-id="7dbb5-137">Reference assembly generation</span></span>

<span data-ttu-id="7dbb5-138">Há duas novas opções do compilador que geram *assemblies somente de referência*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) e [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7dbb5-138">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="7dbb5-139">Os tópicos vinculados explicam essas opções e os assemblies de referência mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="7dbb5-139">The linked topics explain these options and reference assemblies in more detail.</span></span>
