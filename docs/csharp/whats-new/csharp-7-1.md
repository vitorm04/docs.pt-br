---
title: Novidades no C# 7.1
description: Uma visão geral dos novos recursos no C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480957"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="a5642-103">Novidades no C# 7.1</span><span class="sxs-lookup"><span data-stu-id="a5642-103">What's new in C# 7.1</span></span>

<span data-ttu-id="a5642-104">O C# 7.1 é a primeira versão de ponto da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="a5642-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="a5642-105">Ele marca uma cadência de versão maior para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="a5642-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="a5642-106">Use os novos recursos mais cedo, de preferência, quando cada novo recurso estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="a5642-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="a5642-107">O C# 7.1 adiciona a capacidade de configurar o compilador para que ele corresponda a uma versão especificada da linguagem.</span><span class="sxs-lookup"><span data-stu-id="a5642-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="a5642-108">Isso permite que você separe a decisão de atualizar ferramentas da decisão de atualizar versões da linguagem.</span><span class="sxs-lookup"><span data-stu-id="a5642-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="a5642-109">O C# 7.1 adiciona a [seleção de versão da linguagem](../language-reference/configure-language-version.md) elemento de configuração, três novos recursos de linguagem e um novo comportamento do compilador.</span><span class="sxs-lookup"><span data-stu-id="a5642-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="a5642-110">Os novos recursos de linguagem nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="a5642-110">The new language features in this release are:</span></span>

* [`async` `Main` <span data-ttu-id="a5642-111">method</span><span class="sxs-lookup"><span data-stu-id="a5642-111">method</span></span>](#async-main)
  - <span data-ttu-id="a5642-112">O ponto de entrada para um aplicativo pode ter o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="a5642-112">The entry point for an application can have the `async` modifier.</span></span>
* [`default` <span data-ttu-id="a5642-113">Expressões literais</span><span class="sxs-lookup"><span data-stu-id="a5642-113">literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="a5642-114">Use expressões literais padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="a5642-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="a5642-115">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="a5642-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="a5642-116">Em muitos casos, os nomes dos elementos de tupla podem ser inferidos com base na inicialização da tupla.</span><span class="sxs-lookup"><span data-stu-id="a5642-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="a5642-117">Restrições em parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="a5642-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="a5642-118">Você pode usar expressões de correspondência de padrão em variáveis cujo tipo é um parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a5642-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="a5642-119">Por fim, o compilador traz duas opções `/refout` e `/refonly`, que controlam a [geração de assembly de referência](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="a5642-119">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="a5642-120">Para usar as últimas funcionalidades em uma versão de ponto, você precisa [configurar a versão da linguagem do compilador](../language-reference/configure-language-version.md) e selecionar a versão.</span><span class="sxs-lookup"><span data-stu-id="a5642-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="a5642-121">Async main</span><span class="sxs-lookup"><span data-stu-id="a5642-121">Async main</span></span>

<span data-ttu-id="a5642-122">Um método *async main* permite que você use `await` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="a5642-122">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="a5642-123">Anteriormente, você precisava escrever:</span><span class="sxs-lookup"><span data-stu-id="a5642-123">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="a5642-124">Agora, você pode escrever:</span><span class="sxs-lookup"><span data-stu-id="a5642-124">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="a5642-125">Se o programa não retorna um código de saída, declare um método `Main` que retorna um <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="a5642-125">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="a5642-126">Leia mais sobre os detalhes no tópico [async main](../programming-guide/main-and-command-args/index.md) no guia de programação.</span><span class="sxs-lookup"><span data-stu-id="a5642-126">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="a5642-127">Expressões literais padrão</span><span class="sxs-lookup"><span data-stu-id="a5642-127">Default literal expressions</span></span>

<span data-ttu-id="a5642-128">Expressões literais padrão são uma melhoria das expressões de valor padrão.</span><span class="sxs-lookup"><span data-stu-id="a5642-128">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="a5642-129">Essas expressões inicializam uma variável com o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="a5642-129">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="a5642-130">Nos casos em que você anteriormente escrevia:</span><span class="sxs-lookup"><span data-stu-id="a5642-130">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="a5642-131">Agora você pode omitir o tipo no lado direito da inicialização:</span><span class="sxs-lookup"><span data-stu-id="a5642-131">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="a5642-132">Saiba mais sobre essa melhoria no artigo do Guia de Programação do C# em [expressões de valor padrão](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a5642-132">You can learn more about this enhancement in the C# Programming Guide article on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="a5642-133">Essa melhoria também altera algumas das regras de análise da [palavra-chave padrão](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="a5642-133">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="a5642-134">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="a5642-134">Inferred tuple element names</span></span>

<span data-ttu-id="a5642-135">Esse recurso é uma pequena melhoria do recurso de tuplas introduzido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="a5642-135">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="a5642-136">Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja usar para os elementos de tupla:</span><span class="sxs-lookup"><span data-stu-id="a5642-136">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="a5642-137">Os nomes dos elementos de tupla podem ser inferidos com base nas variáveis usadas para inicializar a tupla no C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="a5642-137">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="a5642-138">Saiba mais sobre esse recurso no artigo [Tuplas](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="a5642-138">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="a5642-139">Restrições em parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="a5642-139">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="a5642-140">A partir do C# 7.1, a expressão de padrão para o padrão de tipo `is` e `switch` pode ter o tipo de um parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a5642-140">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="a5642-141">Isso pode ser mais útil ao verificar tipos que podem ser do tipo `struct` ou `class` e você deseja evitar conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="a5642-141">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="a5642-142">Geração de assembly de referência</span><span class="sxs-lookup"><span data-stu-id="a5642-142">Reference assembly generation</span></span>

<span data-ttu-id="a5642-143">Há duas novas opções do compilador que geram *assemblies somente de referência*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) e [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a5642-143">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="a5642-144">Os artigos vinculados explicam essas opções e os assemblies de referência mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="a5642-144">The linked articles explain these options and reference assemblies in more detail.</span></span>
