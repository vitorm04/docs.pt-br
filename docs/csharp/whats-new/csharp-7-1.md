---
title: Novidades no C# 7.1
description: Uma visão geral dos novos recursos no C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: 18306da709ea30f03f6c42b4a917e9b39695eb16
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796600"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="f53d7-103">Novidades no C# 7.1</span><span class="sxs-lookup"><span data-stu-id="f53d7-103">What's new in C# 7.1</span></span>

<span data-ttu-id="f53d7-104">O C# 7.1 é a primeira versão de ponto da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="f53d7-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="f53d7-105">Ele marca uma cadência de versão maior para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="f53d7-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="f53d7-106">Use os novos recursos mais cedo, de preferência, quando cada novo recurso estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="f53d7-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="f53d7-107">O C# 7.1 adiciona a capacidade de configurar o compilador para que ele corresponda a uma versão especificada da linguagem.</span><span class="sxs-lookup"><span data-stu-id="f53d7-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="f53d7-108">Isso permite que você separe a decisão de atualizar ferramentas da decisão de atualizar versões da linguagem.</span><span class="sxs-lookup"><span data-stu-id="f53d7-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="f53d7-109">O C# 7.1 adiciona a [seleção de versão da linguagem](../language-reference/configure-language-version.md) elemento de configuração, três novos recursos de linguagem e um novo comportamento do compilador.</span><span class="sxs-lookup"><span data-stu-id="f53d7-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="f53d7-110">Os novos recursos de linguagem nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="f53d7-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="f53d7-111">`async` Método `Main`</span><span class="sxs-lookup"><span data-stu-id="f53d7-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f53d7-112">O ponto de entrada para um aplicativo pode ter o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="f53d7-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="f53d7-113">`default` Expressões literais</span><span class="sxs-lookup"><span data-stu-id="f53d7-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f53d7-114">Use expressões literais padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="f53d7-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="f53d7-115">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="f53d7-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="f53d7-116">Em muitos casos, os nomes dos elementos de tupla podem ser inferidos com base na inicialização da tupla.</span><span class="sxs-lookup"><span data-stu-id="f53d7-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="f53d7-117">Correspondência de padrões em parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="f53d7-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="f53d7-118">Você pode usar expressões de correspondência de padrão em variáveis cujo tipo é um parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f53d7-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="f53d7-119">Por fim, o compilador traz duas opções `-refout` e `-refonly`, que controlam a [geração de assembly de referência](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="f53d7-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="f53d7-120">Para usar as últimas funcionalidades em uma versão de ponto, você precisa [configurar a versão da linguagem do compilador](../language-reference/configure-language-version.md) e selecionar a versão.</span><span class="sxs-lookup"><span data-stu-id="f53d7-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="f53d7-121">O restante deste artigo fornece uma visão geral de cada recurso.</span><span class="sxs-lookup"><span data-stu-id="f53d7-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="f53d7-122">Para cada recurso, você aprenderá o raciocínio por trás dele.</span><span class="sxs-lookup"><span data-stu-id="f53d7-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="f53d7-123">Você aprenderá a sintaxe.</span><span class="sxs-lookup"><span data-stu-id="f53d7-123">You'll learn the syntax.</span></span> <span data-ttu-id="f53d7-124">Você pode explorar esses recursos em seu ambiente usando a ferramenta global `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="f53d7-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="f53d7-125">Instale a ferramenta global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="f53d7-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="f53d7-126">Clone o repositório [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="f53d7-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="f53d7-127">Definir o diretório atual do subdiretório *csharp7* para o repositório *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="f53d7-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="f53d7-128">Execute `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="f53d7-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="f53d7-129">Async main</span><span class="sxs-lookup"><span data-stu-id="f53d7-129">Async main</span></span>

<span data-ttu-id="f53d7-130">Um método *async main* permite que você use `await` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="f53d7-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="f53d7-131">Anteriormente, você precisava escrever:</span><span class="sxs-lookup"><span data-stu-id="f53d7-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f53d7-132">Agora, você pode escrever:</span><span class="sxs-lookup"><span data-stu-id="f53d7-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f53d7-133">Se o programa não retorna um código de saída, declare um método `Main` que retorna um <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="f53d7-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f53d7-134">Leia mais sobre os detalhes no tópico [async main](../programming-guide/main-and-command-args/index.md) no guia de programação.</span><span class="sxs-lookup"><span data-stu-id="f53d7-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f53d7-135">Expressões literais padrão</span><span class="sxs-lookup"><span data-stu-id="f53d7-135">Default literal expressions</span></span>

<span data-ttu-id="f53d7-136">Expressões literais padrão são uma melhoria das expressões de valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f53d7-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="f53d7-137">Essas expressões inicializam uma variável com o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f53d7-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f53d7-138">Nos casos em que você anteriormente escrevia:</span><span class="sxs-lookup"><span data-stu-id="f53d7-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f53d7-139">Agora você pode omitir o tipo no lado direito da inicialização:</span><span class="sxs-lookup"><span data-stu-id="f53d7-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f53d7-140">Para saber mais, confira a seção [Literais padrão](../language-reference/operators/default.md#default-literal) do artigo do [operador padrão](../language-reference/operators/default.md).</span><span class="sxs-lookup"><span data-stu-id="f53d7-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="f53d7-141">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="f53d7-141">Inferred tuple element names</span></span>

<span data-ttu-id="f53d7-142">Esse recurso é uma pequena melhoria do recurso de tuplas introduzido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="f53d7-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="f53d7-143">Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja usar para os elementos de tupla:</span><span class="sxs-lookup"><span data-stu-id="f53d7-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="f53d7-144">Os nomes dos elementos de tupla podem ser inferidos com base nas variáveis usadas para inicializar a tupla no C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="f53d7-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f53d7-145">Saiba mais sobre esse recurso no artigo [Tuplas](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="f53d7-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="f53d7-146">Restrições em parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="f53d7-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="f53d7-147">A partir do C# 7.1, a expressão de padrão para o padrão de tipo `is` e `switch` pode ter o tipo de um parâmetro de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f53d7-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="f53d7-148">Isso pode ser mais útil ao verificar tipos que podem ser do tipo `struct` ou `class` e você deseja evitar conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="f53d7-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="f53d7-149">Geração de assembly de referência</span><span class="sxs-lookup"><span data-stu-id="f53d7-149">Reference assembly generation</span></span>

<span data-ttu-id="f53d7-150">Há duas novas opções do compilador que geram *assemblies somente de referência*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) e [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f53d7-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f53d7-151">Os artigos vinculados explicam essas opções e os assemblies de referência mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="f53d7-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
