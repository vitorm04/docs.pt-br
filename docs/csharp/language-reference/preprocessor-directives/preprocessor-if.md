---
title: '#Diretiva de pré-processamento "if" – Referência de C#'
ms.custom: seodec18
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 561a628c60888a8d4f3c50c8413784e1ed210599
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036001"
---
# <a name="if-c-reference"></a><span data-ttu-id="b9117-102">#if (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b9117-102">#if (C# Reference)</span></span>

<span data-ttu-id="b9117-103">Quando o Compilador do Visual C# encontra uma diretiva `#if`, seguida eventualmente por uma diretiva [#endif](preprocessor-endif.md), ele compila o código entre as diretivas somente quando o símbolo especificado é definido.</span><span class="sxs-lookup"><span data-stu-id="b9117-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="b9117-104">Ao contrário do C e do C++, não é possível atribuir um valor numérico a um símbolo.</span><span class="sxs-lookup"><span data-stu-id="b9117-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="b9117-105">A instrução #if em C# é booliana e testa apenas quando o símbolo foi definido ou não.</span><span class="sxs-lookup"><span data-stu-id="b9117-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="b9117-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9117-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="b9117-107">É possível usar os operadores [==](../operators/equality-operators.md#equality-operator-) (igualdade) e [!=](../operators/equality-operators.md#inequality-operator-) (desigualdade) apenas para testar [true](../keywords/true-literal.md) ou [false](../keywords/false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b9117-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true-literal.md) or [false](../keywords/false-literal.md).</span></span> <span data-ttu-id="b9117-108">True significa que o símbolo foi definido.</span><span class="sxs-lookup"><span data-stu-id="b9117-108">True means the symbol is defined.</span></span> <span data-ttu-id="b9117-109">A instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="b9117-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="b9117-110">É possível usar os operadores [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (e), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (ou) e [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="b9117-110">You can use the operators [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or), and [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span></span> <span data-ttu-id="b9117-111">(não) para avaliar se vários símbolos foram definidos.</span><span class="sxs-lookup"><span data-stu-id="b9117-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="b9117-112">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="b9117-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9117-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9117-113">Remarks</span></span>

<span data-ttu-id="b9117-114">`#if`, juntamente com as diretivas [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) e [#undef](preprocessor-undef.md), permite incluir ou excluir código com base na existência de um ou mais símbolos.</span><span class="sxs-lookup"><span data-stu-id="b9117-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="b9117-115">Isso pode ser útil ao compilar o código para um build de depuração ou ao compilar para uma configuração específica.</span><span class="sxs-lookup"><span data-stu-id="b9117-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="b9117-116">Uma diretiva condicional que começa com uma diretiva `#if` deverá ser explicitamente encerrada com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="b9117-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="b9117-117">A diretiva `#define` permite definir um símbolo.</span><span class="sxs-lookup"><span data-stu-id="b9117-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="b9117-118">Ao usar o símbolo como a expressão passada para a diretiva `#if`, a expressão será avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="b9117-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="b9117-119">Você também pode definir um símbolo com a opção do compilador [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b9117-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b9117-120">É possível excluir um símbolo com [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="b9117-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="b9117-121">Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="b9117-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="b9117-122">Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processamento e um símbolo pode ser avaliado apenas por uma diretiva de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="b9117-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="b9117-123">O escopo de um símbolo criado com `#define` é o arquivo no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="b9117-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="b9117-124">O sistema de compilação também reconhece os símbolos de pré-processador predefinidos que representam [estruturas de destino](../../../standard/frameworks.md) diferentes em projetos em estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="b9117-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="b9117-125">Eles são úteis ao criar aplicativos que podem direcionar mais de uma implementação ou versão do .NET.</span><span class="sxs-lookup"><span data-stu-id="b9117-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="b9117-126">Para projetos tradicionais de .NET Framework, você precisa configurar manualmente os símbolos de compilação condicional para as diferentes estruturas de destino no Visual Studio por meio das páginas de propriedades do projeto.</span><span class="sxs-lookup"><span data-stu-id="b9117-126">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="b9117-127">As constantes TRACE e DEBUG são exemplos de outros símbolos predefinidos.</span><span class="sxs-lookup"><span data-stu-id="b9117-127">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="b9117-128">Para substituir os valores definidos no projeto, use a diretiva `#define`.</span><span class="sxs-lookup"><span data-stu-id="b9117-128">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="b9117-129">Por exemplo, o símbolo DEBUG é definido automaticamente, de acordo com as propriedades de configuração do build (Modo de Depuração ou Modo de Versão).</span><span class="sxs-lookup"><span data-stu-id="b9117-129">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="b9117-130">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b9117-130">Examples</span></span>

<span data-ttu-id="b9117-131">O exemplo a seguir mostra como definir um símbolo MYTEST em um arquivo e testar os valores dos símbolos MYTEST e DEBUG.</span><span class="sxs-lookup"><span data-stu-id="b9117-131">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="b9117-132">A saída deste exemplo depende do fato de você criar o projeto no modo de configuração de versão ou no modo de configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="b9117-132">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="b9117-133">O exemplo a seguir mostra como testar várias estruturas de destino para que você possa usar APIs mais recentes, quando possível:</span><span class="sxs-lookup"><span data-stu-id="b9117-133">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="b9117-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9117-134">See also</span></span>

- [<span data-ttu-id="b9117-135">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b9117-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9117-136">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b9117-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b9117-137">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="b9117-137">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="b9117-138">Como compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="b9117-138">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
