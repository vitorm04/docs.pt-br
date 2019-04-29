---
title: Refatoração em funções puras (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787160"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="108b8-102">Refatoração em funções puras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="108b8-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="108b8-103">Um aspecto importante de transformações e puras é aprender como o código do refatorar usando funções puras.</span><span class="sxs-lookup"><span data-stu-id="108b8-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="108b8-104">Conforme observado anteriormente nesta seção, uma função pura tem duas características úteis:</span><span class="sxs-lookup"><span data-stu-id="108b8-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="108b8-105">Não tem efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="108b8-105">It has no side effects.</span></span> <span data-ttu-id="108b8-106">A função não altera quaisquer variáveis ou os dados de qualquer tipo fora da função.</span><span class="sxs-lookup"><span data-stu-id="108b8-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="108b8-107">É consistente.</span><span class="sxs-lookup"><span data-stu-id="108b8-107">It is consistent.</span></span> <span data-ttu-id="108b8-108">Dado o mesmo conjunto de dados de entrada, sempre retornará o mesmo valor de saída.</span><span class="sxs-lookup"><span data-stu-id="108b8-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="108b8-109">Uma maneira de fazer a transição para programação funcional é o código existente do refatorar para eliminar efeitos colaterais desnecessários e dependências externas.</span><span class="sxs-lookup"><span data-stu-id="108b8-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="108b8-110">Dessa maneira, você pode criar versões puras de função do código existente.</span><span class="sxs-lookup"><span data-stu-id="108b8-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="108b8-111">Este tópico descreve o que é uma função pura e o que não é.</span><span class="sxs-lookup"><span data-stu-id="108b8-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="108b8-112">O [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial mostra como manipular um documento WordprocessingML e inclui dois exemplos de como refatorar usando uma função pura.</span><span class="sxs-lookup"><span data-stu-id="108b8-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="108b8-113">Eliminando efeitos colaterais e dependências externas</span><span class="sxs-lookup"><span data-stu-id="108b8-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="108b8-114">Os seguintes exemplos contrastam duas funções não puras e uma função pura.</span><span class="sxs-lookup"><span data-stu-id="108b8-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="108b8-115">Função não pura que altera um membro de classe</span><span class="sxs-lookup"><span data-stu-id="108b8-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="108b8-116">No código a seguir, a função de `HyphenatedConcat` não é uma função pura, porque altera o membro de dados `aMember` na classe:</span><span class="sxs-lookup"><span data-stu-id="108b8-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

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

<span data-ttu-id="108b8-117">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="108b8-117">This code produces the following output:</span></span>

```
StringOne-StringTwo
```

<span data-ttu-id="108b8-118">Observe que é irrelevante se os dados que está sendo modificados tem `public` ou `private` acessar ou é um `shared` membro ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="108b8-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="108b8-119">Uma função pura não altera quaisquer dados fora da função.</span><span class="sxs-lookup"><span data-stu-id="108b8-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="108b8-120">Função não pura que altera um argumento</span><span class="sxs-lookup"><span data-stu-id="108b8-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="108b8-121">Além disso, a seguinte versão dessa mesma função não é pura porque modifica o conteúdo do seu parâmetro, `sb`.</span><span class="sxs-lookup"><span data-stu-id="108b8-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

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

<span data-ttu-id="108b8-122">Esta versão do programa gerenciar as mesmas saída que a primeira versão, porque a função de `HyphenatedConcat` alterou o valor (estado) do primeiro parâmetro chamar a função de membro de <xref:System.Text.StringBuilder.Append%2A> .</span><span class="sxs-lookup"><span data-stu-id="108b8-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="108b8-123">Observe que essa mudança ocorre independentemente do fato de que `HyphenatedConcat` usa passar o parâmetro de atendimento-por- valor.</span><span class="sxs-lookup"><span data-stu-id="108b8-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="108b8-124">Para tipos de referência, se você passa um parâmetro por valor, ele resulta em uma cópia de referência a um objeto que está sendo passado.</span><span class="sxs-lookup"><span data-stu-id="108b8-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="108b8-125">Esta cópia ainda está associada com os mesmos dados de instância que a referência original (até que a variável de referência é atribuído a um novo objeto).</span><span class="sxs-lookup"><span data-stu-id="108b8-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="108b8-126">a Atendimento-por- referência não necessariamente é necessária para uma função modifique um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="108b8-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="108b8-127">Função pura</span><span class="sxs-lookup"><span data-stu-id="108b8-127">Pure Function</span></span>

<span data-ttu-id="108b8-128">Seguir essa versão de hows de programa como implementar a função de `HyphenatedConcat` como uma função pura.</span><span class="sxs-lookup"><span data-stu-id="108b8-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

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

<span data-ttu-id="108b8-129">Além disso, esta versão gerencia a mesma linha de saída: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="108b8-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="108b8-130">Observe que para manter o valor concatenado, ele é armazenado em `s2`variável intermediária.</span><span class="sxs-lookup"><span data-stu-id="108b8-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="108b8-131">Uma abordagem que pode ser muito útil é escrever as funções que são localmente impuros (isto é, declare e alteram variáveis locais) mas é global pura.</span><span class="sxs-lookup"><span data-stu-id="108b8-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="108b8-132">Tais funções têm muitas das características desejáveis de composability, mas impedem alguns de linguagem e mais complicados de programação, como ter que usar a recursão quando um loop simples realizaria a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="108b8-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="108b8-133">Operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="108b8-133">Standard Query Operators</span></span>

<span data-ttu-id="108b8-134">Uma característica importante dos operadores de consulta padrão é que são implementados como funções puras.</span><span class="sxs-lookup"><span data-stu-id="108b8-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="108b8-135">Para obter mais informações, consulte [visão geral de operadores padrão consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="108b8-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="108b8-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="108b8-136">See also</span></span>

- [<span data-ttu-id="108b8-137">Introdução às transformações funcionais puras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="108b8-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="108b8-138">Programação funcional versus Programação imperativa (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="108b8-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
