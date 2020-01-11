---
title: '#Diretiva de pré-processamento "if" – Referência de C#'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899847"
---
# <a name="if-c-reference"></a><span data-ttu-id="df1b9-102">#if (C# referência)</span><span class="sxs-lookup"><span data-stu-id="df1b9-102">#if (C# reference)</span></span>

<span data-ttu-id="df1b9-103">Quando o Compilador do Visual C# encontra uma diretiva `#if`, seguida eventualmente por uma diretiva [#endif](preprocessor-endif.md), ele compila o código entre as diretivas somente quando o símbolo especificado é definido.</span><span class="sxs-lookup"><span data-stu-id="df1b9-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="df1b9-104">Ao contrário do C e do C++, não é possível atribuir um valor numérico a um símbolo.</span><span class="sxs-lookup"><span data-stu-id="df1b9-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="df1b9-105">A instrução `#if` em C# é booleana e apenas testa se o símbolo foi definido ou não.</span><span class="sxs-lookup"><span data-stu-id="df1b9-105">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="df1b9-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="df1b9-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="df1b9-107">Você pode usar os operadores [==](../operators/equality-operators.md#equality-operator-) (igualdade) e [! =](../operators/equality-operators.md#inequality-operator-) (desigualdade) somente para testar os valores [bool](../builtin-types/bool.md) `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="df1b9-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="df1b9-108">`true` significa que o símbolo está definido.</span><span class="sxs-lookup"><span data-stu-id="df1b9-108">`true` means the symbol is defined.</span></span> <span data-ttu-id="df1b9-109">A instrução `#if DEBUG` tem o mesmo significado que `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="df1b9-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="df1b9-110">Você pode usar o [& & (e)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [ &#124; &#124; (ou)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)e [! (não)](../operators/boolean-logical-operators.md#logical-negation-operator-) operadores para avaliar se vários símbolos foram definidos.</span><span class="sxs-lookup"><span data-stu-id="df1b9-110">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="df1b9-111">Também é possível agrupar os símbolos e operadores com parênteses.</span><span class="sxs-lookup"><span data-stu-id="df1b9-111">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="df1b9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="df1b9-112">Remarks</span></span>

<span data-ttu-id="df1b9-113">`#if`, juntamente com as diretivas [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) e [#undef](preprocessor-undef.md), permite incluir ou excluir código com base na existência de um ou mais símbolos.</span><span class="sxs-lookup"><span data-stu-id="df1b9-113">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="df1b9-114">Isso pode ser útil ao compilar o código para um build de depuração ou ao compilar para uma configuração específica.</span><span class="sxs-lookup"><span data-stu-id="df1b9-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="df1b9-115">Uma diretiva condicional que começa com uma diretiva `#if` deverá ser explicitamente encerrada com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="df1b9-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="df1b9-116">A diretiva `#define` permite definir um símbolo.</span><span class="sxs-lookup"><span data-stu-id="df1b9-116">`#define` lets you define a symbol.</span></span> <span data-ttu-id="df1b9-117">Ao usar o símbolo como a expressão passada para a diretiva `#if`, a expressão será avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="df1b9-117">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="df1b9-118">Você também pode definir um símbolo com a opção do compilador [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="df1b9-118">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="df1b9-119">É possível excluir um símbolo com [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="df1b9-119">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="df1b9-120">Um símbolo definido com `-define` ou com `#define` não entra em conflito com uma variável do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="df1b9-120">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="df1b9-121">Ou seja, um nome de variável não deve ser passado para uma diretiva de pré-processamento e um símbolo pode ser avaliado apenas por uma diretiva de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="df1b9-121">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="df1b9-122">O escopo de um símbolo criado com `#define` é o arquivo no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="df1b9-122">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="df1b9-123">O sistema de compilação também reconhece os símbolos de pré-processador predefinidos que representam [estruturas de destino](../../../standard/frameworks.md) diferentes em projetos em estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="df1b9-123">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="df1b9-124">Eles são úteis ao criar aplicativos que podem direcionar mais de uma implementação ou versão do .NET.</span><span class="sxs-lookup"><span data-stu-id="df1b9-124">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="df1b9-125">Para projetos tradicionais de .NET Framework, você precisa configurar manualmente os símbolos de compilação condicional para as diferentes estruturas de destino no Visual Studio por meio das páginas de propriedades do projeto.</span><span class="sxs-lookup"><span data-stu-id="df1b9-125">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="df1b9-126">As constantes TRACE e DEBUG são exemplos de outros símbolos predefinidos.</span><span class="sxs-lookup"><span data-stu-id="df1b9-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="df1b9-127">Para substituir os valores definidos no projeto, use a diretiva `#define`.</span><span class="sxs-lookup"><span data-stu-id="df1b9-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="df1b9-128">Por exemplo, o símbolo DEBUG é definido automaticamente, de acordo com as propriedades de configuração do build (Modo de Depuração ou Modo de Versão).</span><span class="sxs-lookup"><span data-stu-id="df1b9-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="df1b9-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="df1b9-129">Examples</span></span>

<span data-ttu-id="df1b9-130">O exemplo a seguir mostra como definir um símbolo MYTEST em um arquivo e testar os valores dos símbolos MYTEST e DEBUG.</span><span class="sxs-lookup"><span data-stu-id="df1b9-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="df1b9-131">A saída deste exemplo depende do fato de você criar o projeto no modo de configuração de versão ou no modo de configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="df1b9-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="df1b9-132">O exemplo a seguir mostra como testar várias estruturas de destino para que você possa usar APIs mais recentes, quando possível:</span><span class="sxs-lookup"><span data-stu-id="df1b9-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="df1b9-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="df1b9-133">See also</span></span>

- [<span data-ttu-id="df1b9-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="df1b9-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="df1b9-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="df1b9-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="df1b9-136">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="df1b9-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="df1b9-137">Como compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="df1b9-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
