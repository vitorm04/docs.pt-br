---
title: Refatorar em funções puras – LINQ to XML
description: Saiba mais sobre as funções puras e como usá-las para refatorar o código.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552305"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a><span data-ttu-id="d9a46-103">Refatorar em funções puras (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d9a46-103">Refactor into pure functions (LINQ to XML)</span></span>

<span data-ttu-id="d9a46-104">Um aspecto importante de transformações e puras é aprender como o código do refatorar usando funções puras.</span><span class="sxs-lookup"><span data-stu-id="d9a46-104">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

> [!NOTE]
> <span data-ttu-id="d9a46-105">A nomenclatura comuns em programação funcional é que você refatora programa usando funções puras.</span><span class="sxs-lookup"><span data-stu-id="d9a46-105">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="d9a46-106">No Visual Basic e C++, isso alinha com o uso das funções em linguagens respectivos.</span><span class="sxs-lookup"><span data-stu-id="d9a46-106">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="d9a46-107">No entanto, em C#, as funções são chamadas métodos.</span><span class="sxs-lookup"><span data-stu-id="d9a46-107">However, in C#, functions are called methods.</span></span> <span data-ttu-id="d9a46-108">Para fins desta discussão, uma função pura é implementada como um método em C#.</span><span class="sxs-lookup"><span data-stu-id="d9a46-108">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>

<span data-ttu-id="d9a46-109">Conforme observado anteriormente nesta seção, uma função pura tem duas características úteis:</span><span class="sxs-lookup"><span data-stu-id="d9a46-109">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="d9a46-110">Não tem efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="d9a46-110">It has no side effects.</span></span> <span data-ttu-id="d9a46-111">A função não altera nenhuma variável ou os dados de qualquer tipo fora da função.</span><span class="sxs-lookup"><span data-stu-id="d9a46-111">The function doesn't change any variables or the data of any type outside of the function.</span></span>
- <span data-ttu-id="d9a46-112">É consistente.</span><span class="sxs-lookup"><span data-stu-id="d9a46-112">It's consistent.</span></span> <span data-ttu-id="d9a46-113">Dado o mesmo conjunto de dados de entrada, sempre retornará o mesmo valor de saída.</span><span class="sxs-lookup"><span data-stu-id="d9a46-113">Given the same set of input data, it will always return the same output value.</span></span>

<span data-ttu-id="d9a46-114">Uma maneira de fazer a transição para programação funcional é o código existente do refatorar para eliminar efeitos colaterais desnecessários e dependências externas.</span><span class="sxs-lookup"><span data-stu-id="d9a46-114">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="d9a46-115">Dessa maneira, você pode criar versões puras de função do código existente.</span><span class="sxs-lookup"><span data-stu-id="d9a46-115">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="d9a46-116">Este artigo discute o que é uma função pura e o que não é.</span><span class="sxs-lookup"><span data-stu-id="d9a46-116">This article discusses what a pure function is and what it's not.</span></span> <span data-ttu-id="d9a46-117">O tutorial [: manipular conteúdo em um documento do WordprocessingML](xml-shape-wordprocessingml-documents.md) mostra como manipular um documento do WordprocessingML e inclui dois exemplos de como refatorar usando uma função pura.</span><span class="sxs-lookup"><span data-stu-id="d9a46-117">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

<span data-ttu-id="d9a46-118">Os seguintes exemplos contrastam duas funções não puras e uma função pura.</span><span class="sxs-lookup"><span data-stu-id="d9a46-118">The following examples contrast two non-pure functions and a pure function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a><span data-ttu-id="d9a46-119">Exemplo: implementar uma função não pura que altera um membro de classe estática</span><span class="sxs-lookup"><span data-stu-id="d9a46-119">Example: Implement a non-pure function that changes a static class member</span></span>

<span data-ttu-id="d9a46-120">No código a seguir, a `HyphenatedConcat` função não é uma função pura, pois modifica o `aMember` membro de classe estática:</span><span class="sxs-lookup"><span data-stu-id="d9a46-120">In the following code, the `HyphenatedConcat` function isn't a pure function, because it modifies the `aMember` static class member:</span></span>

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="d9a46-121">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="d9a46-121">This example produces the following output:</span></span>

```output
StringOne-StringTwo
```

<span data-ttu-id="d9a46-122">Observe que é irrelevante se os dados que estão sendo modificados têm `public` ou têm `private` acesso ou é membro `static` , `shared` membro ou membro de instância.</span><span class="sxs-lookup"><span data-stu-id="d9a46-122">Note that it's irrelevant whether the data being modified has `public` or `private` access, or is a `static` member, `shared` member, or instance member.</span></span> <span data-ttu-id="d9a46-123">Uma função pura não altera nenhum dado fora da função.</span><span class="sxs-lookup"><span data-stu-id="d9a46-123">A pure function doesn't change any data outside of the function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a><span data-ttu-id="d9a46-124">Exemplo: implementar uma função não pura que altera um parâmetro</span><span class="sxs-lookup"><span data-stu-id="d9a46-124">Example: Implement a non-pure function that changes a parameter</span></span>

<span data-ttu-id="d9a46-125">Além disso, a seguinte versão da mesma função não é pura porque modifica o conteúdo de seu parâmetro, `sb` .</span><span class="sxs-lookup"><span data-stu-id="d9a46-125">Furthermore, the following version of this same function isn't pure because it modifies the contents of its parameter, `sb`.</span></span>

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="d9a46-126">Esta versão do programa gerenciar as mesmas saída que a primeira versão, porque a função de `HyphenatedConcat` alterou o valor (estado) do primeiro parâmetro chamar a função de membro de <xref:System.Text.StringBuilder.Append%2A> .</span><span class="sxs-lookup"><span data-stu-id="d9a46-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="d9a46-127">Observe que essa alteração ocorre apesar do fato que `HyphenatedConcat` usa passagem de parâmetro de chamada por valor.</span><span class="sxs-lookup"><span data-stu-id="d9a46-127">Note that this alteration occurs despite the fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9a46-128">Para tipos de referência, se você passa um parâmetro por valor, ele resulta em uma cópia de referência a um objeto que está sendo passado.</span><span class="sxs-lookup"><span data-stu-id="d9a46-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="d9a46-129">Esta cópia ainda está associada com os mesmos dados de instância que a referência original (até que a variável de referência é atribuído a um novo objeto).</span><span class="sxs-lookup"><span data-stu-id="d9a46-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="d9a46-130">A chamada por referência não é necessariamente necessária para uma função modificar um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d9a46-130">Call-by-reference isn't necessarily required for a function to modify a parameter.</span></span>

## <a name="example-implement-a-pure-function"></a><span data-ttu-id="d9a46-131">Exemplo: implementar uma função pura</span><span class="sxs-lookup"><span data-stu-id="d9a46-131">Example: Implement a pure function</span></span>

<span data-ttu-id="d9a46-132">Esta próxima versão do programa mostra como implementar a função `HyphenatedConcat` como uma função pura.</span><span class="sxs-lookup"><span data-stu-id="d9a46-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="d9a46-133">Além disso, esta versão gerencia a mesma linha de saída: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="d9a46-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="d9a46-134">Observe que para manter o valor concatenado, ele é armazenado na variável intermediária `s2` .</span><span class="sxs-lookup"><span data-stu-id="d9a46-134">Note that to retain the concatenated value, it's stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="d9a46-135">Uma abordagem que pode ser muito útil é escrever as funções que são localmente impuros (isto é, declare e alteram variáveis locais) mas é global pura.</span><span class="sxs-lookup"><span data-stu-id="d9a46-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="d9a46-136">Tais funções têm muitas das características desejáveis de composability, mas impedem alguns de linguagem e mais complicados de programação, como ter que usar a recursão quando um loop simples realizaria a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="d9a46-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="d9a46-137">Operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="d9a46-137">Standard query operators</span></span>

<span data-ttu-id="d9a46-138">Uma característica importante dos operadores de consulta padrão é que eles são implementados como funções puras.</span><span class="sxs-lookup"><span data-stu-id="d9a46-138">An important characteristic of the standard query operators is that they're implemented as pure functions.</span></span>

<span data-ttu-id="d9a46-139">Para obter mais informações, consulte Visão geral [dos operadores de consulta padrão (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) e [visão geral dos operadores de consulta padrão (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9a46-139">For more information, see [Standard Query Operators Overview (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) and [Standard Query Operators Overview (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9a46-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9a46-140">See also</span></span>

- [<span data-ttu-id="d9a46-141">Introdução às transformações funcionais puras</span><span class="sxs-lookup"><span data-stu-id="d9a46-141">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="d9a46-142">Programação funcional versus programação imperativa</span><span class="sxs-lookup"><span data-stu-id="d9a46-142">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)
