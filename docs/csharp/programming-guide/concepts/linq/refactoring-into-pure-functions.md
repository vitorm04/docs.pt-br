---
title: "Refatoração em funções puras (C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 9bb17207ba72bb22f5d6db55e9d1bd77e3013445
ms.openlocfilehash: 2bce781df80a777203ed8e713bedf83f1c7779a8
ms.contentlocale: pt-br
ms.lasthandoff: 08/25/2017

---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="d1023-102">Refatoração em funções puras (C#)</span><span class="sxs-lookup"><span data-stu-id="d1023-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="d1023-103">Um aspecto importante de transformações e puras é aprender como o código do refatorar usando funções puras.</span><span class="sxs-lookup"><span data-stu-id="d1023-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1023-104">A nomenclatura comuns em programação funcional é que você refatora programa usando funções puras.</span><span class="sxs-lookup"><span data-stu-id="d1023-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="d1023-105">No Visual Basic e C++, isso alinha com o uso das funções em linguagens respectivos.</span><span class="sxs-lookup"><span data-stu-id="d1023-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="d1023-106">No entanto, em C#, as funções são chamadas métodos.</span><span class="sxs-lookup"><span data-stu-id="d1023-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="d1023-107">Para fins desta discussão, uma função pura é implementada como um método em C#.</span><span class="sxs-lookup"><span data-stu-id="d1023-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="d1023-108">Conforme observado anteriormente nesta seção, uma função pura tem duas características úteis:</span><span class="sxs-lookup"><span data-stu-id="d1023-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="d1023-109">Não tem efeito colateral.</span><span class="sxs-lookup"><span data-stu-id="d1023-109">It has no side effects.</span></span> <span data-ttu-id="d1023-110">A função não altera quaisquer variáveis ou os dados de qualquer tipo fora da função.</span><span class="sxs-lookup"><span data-stu-id="d1023-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="d1023-111">É consistente.</span><span class="sxs-lookup"><span data-stu-id="d1023-111">It is consistent.</span></span> <span data-ttu-id="d1023-112">Dado o mesmo conjunto de dados de entrada, sempre retornará o mesmo valor de saída.</span><span class="sxs-lookup"><span data-stu-id="d1023-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="d1023-113">Uma maneira de fazer a transição para programação funcional é o código existente do refatorar para eliminar efeitos colaterais desnecessários e dependências externas.</span><span class="sxs-lookup"><span data-stu-id="d1023-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="d1023-114">Dessa maneira, você pode criar versões puras de função do código existente.</span><span class="sxs-lookup"><span data-stu-id="d1023-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="d1023-115">Este tópico descreve o que é uma função pura e o que não é.</span><span class="sxs-lookup"><span data-stu-id="d1023-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="d1023-116">O tutorial [Tutorial: manipulando conteúdo em um documento WordprocessingML](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) mostra como manipular um documento WordprocessingML e inclui dois exemplos de como refatorar usando uma função pura.</span><span class="sxs-lookup"><span data-stu-id="d1023-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="d1023-117">Eliminando efeitos colaterais e dependências externas</span><span class="sxs-lookup"><span data-stu-id="d1023-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="d1023-118">Os seguintes exemplos contrastam duas funções não puras e uma função pura.</span><span class="sxs-lookup"><span data-stu-id="d1023-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="d1023-119">Função não pura que altera um membro de classe</span><span class="sxs-lookup"><span data-stu-id="d1023-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="d1023-120">No código a seguir, a função de `HypenatedConcat` não é uma função pura, porque altera o membro de dados `aMember` na classe:</span><span class="sxs-lookup"><span data-stu-id="d1023-120">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HypenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HypenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 <span data-ttu-id="d1023-121">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d1023-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="d1023-122">Observe que é irrelevante se os dados modificados têm acesso a `public` ou `private`, ou são um membro de `static` ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="d1023-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="d1023-123">Uma função pura não altera quaisquer dados fora da função.</span><span class="sxs-lookup"><span data-stu-id="d1023-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="d1023-124">Função não pura que altera um argumento</span><span class="sxs-lookup"><span data-stu-id="d1023-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="d1023-125">Além disso, a seguinte versão dessa mesma função não é pura porque modifica o conteúdo do seu parâmetro, `sb`.</span><span class="sxs-lookup"><span data-stu-id="d1023-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```csharp  
public class Program  
{  
    public static void HypenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HypenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 <span data-ttu-id="d1023-126">Esta versão do programa gerenciar as mesmas saída que a primeira versão, porque a função de `HypenatedConcat` alterou o valor (estado) do primeiro parâmetro chamar a função de membro de <xref:System.Text.StringBuilder.Append%2A> .</span><span class="sxs-lookup"><span data-stu-id="d1023-126">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="d1023-127">Observe que essa mudança ocorre independentemente do fato de que `HypenatedConcat` usa passar o parâmetro de atendimento-por- valor.</span><span class="sxs-lookup"><span data-stu-id="d1023-127">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1023-128">Para tipos de referência, se você passa um parâmetro por valor, ele resulta em uma cópia de referência a um objeto que está sendo passado.</span><span class="sxs-lookup"><span data-stu-id="d1023-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="d1023-129">Esta cópia ainda está associada com os mesmos dados de instância que a referência original (até que a variável de referência é atribuído a um novo objeto).</span><span class="sxs-lookup"><span data-stu-id="d1023-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="d1023-130">a Atendimento-por- referência não necessariamente é necessária para uma função modifique um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d1023-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="d1023-131">Função pura</span><span class="sxs-lookup"><span data-stu-id="d1023-131">Pure Function</span></span>  
<span data-ttu-id="d1023-132">Esta próxima versão do programa mostra como implementar a função `HypenatedConcat` como uma função pura.</span><span class="sxs-lookup"><span data-stu-id="d1023-132">This next version of the program shows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="d1023-133">Além disso, esta versão gerencia a mesma linha de saída: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="d1023-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="d1023-134">Observe que para manter o valor concatenado, ele é armazenado em `s2`variável intermediária.</span><span class="sxs-lookup"><span data-stu-id="d1023-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="d1023-135">Uma abordagem que pode ser muito útil é escrever as funções que são localmente impuros (isto é, declare e alteram variáveis locais) mas é global pura.</span><span class="sxs-lookup"><span data-stu-id="d1023-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="d1023-136">Tais funções têm muitas das características desejáveis de composability, mas impedem alguns de linguagem e mais complicados de programação, como ter que usar a recursão quando um loop simples realizaria a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="d1023-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="d1023-137">Operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="d1023-137">Standard Query Operators</span></span>  
 <span data-ttu-id="d1023-138">Uma característica importante dos operadores de consulta padrão é que são implementados como funções puras.</span><span class="sxs-lookup"><span data-stu-id="d1023-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="d1023-139">Para obter mais informações, consulte [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d1023-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1023-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1023-140">See Also</span></span>  
 <span data-ttu-id="d1023-141">[Introdução às transformações funcionais puras (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="d1023-141">[Introduction to Pure Functional Transformations (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
 [<span data-ttu-id="d1023-142">Programação funcional versus Programação obrigatória (C#)</span><span class="sxs-lookup"><span data-stu-id="d1023-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

