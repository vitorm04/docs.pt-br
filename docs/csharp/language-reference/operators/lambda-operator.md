---
title: Operador =&gt; – Referência de C#
ms.custom: seodec18
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 8641757d9252c88cf30595cec06d27b964e4d95c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415280"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="80d8f-102">Operador =&gt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="80d8f-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="80d8f-103">O operador `=>` pode ser usado de duas maneiras no C#:</span><span class="sxs-lookup"><span data-stu-id="80d8f-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="80d8f-104">Assim como o [operador lambda](#lambda-operator) em uma [expressão lambda](../../lambda-expressions.md), ele separa as variáveis de entrada do corpo lambda.</span><span class="sxs-lookup"><span data-stu-id="80d8f-104">As the [lambda operator](#lambda-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="80d8f-105">Em uma [definição de corpo da expressão](#expression-body-definition), ele separa um nome de membro da implementação do membro.</span><span class="sxs-lookup"><span data-stu-id="80d8f-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="80d8f-106">Operador lambda</span><span class="sxs-lookup"><span data-stu-id="80d8f-106">Lambda operator</span></span>

<span data-ttu-id="80d8f-107">O token `=>` é chamado de operador lambda.</span><span class="sxs-lookup"><span data-stu-id="80d8f-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="80d8f-108">Ele é usado em *expressões lambda* para separar as variáveis de entrada no lado esquerdo do corpo lambda no lado direito.</span><span class="sxs-lookup"><span data-stu-id="80d8f-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="80d8f-109">As expressões lambda são expressões embutidas semelhantes aos métodos anônimos, mas mais flexíveis, elas são amplamente usadas em consultas LINQ que são expressas na sintaxe do método.</span><span class="sxs-lookup"><span data-stu-id="80d8f-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="80d8f-110">Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="80d8f-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="80d8f-111">O exemplo a seguir mostra duas maneiras de localizar e exibir o comprimento da cadeia de caracteres mais curta em uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="80d8f-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="80d8f-112">A primeira parte do exemplo aplica uma expressão lambda (`w => w.Length`) a cada elemento da matriz `words` e, em seguida, usa o método <xref:System.Linq.Enumerable.Min%2A> para encontrar o menor tamanho.</span><span class="sxs-lookup"><span data-stu-id="80d8f-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="80d8f-113">Para comparação, a segunda parte do exemplo mostra uma solução mais longa que usa a sintaxe de consulta para fazer o mesmo.</span><span class="sxs-lookup"><span data-stu-id="80d8f-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a><span data-ttu-id="80d8f-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="80d8f-114">Remarks</span></span>  
 <span data-ttu-id="80d8f-115">O operador `=>` tem a mesma precedência do operador de atribuição (`=`) e é associativo à direita.</span><span class="sxs-lookup"><span data-stu-id="80d8f-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="80d8f-116">Você pode especificar o tipo da variável de entrada explicitamente ou deixar que o compilador o infira, em ambos os casos, a variável é fortemente tipada no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="80d8f-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="80d8f-117">Quando você especificar um tipo, deverá colocar o nome do tipo e o nome da variável entre parênteses, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="80d8f-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="80d8f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80d8f-118">Example</span></span>  
 <span data-ttu-id="80d8f-119">O exemplo a seguir mostra como escrever uma expressão lambda para a sobrecarga do operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>, que utiliza dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="80d8f-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="80d8f-120">Como a expressão lambda tem mais de um parâmetro, os parâmetros devem ser colocados entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="80d8f-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="80d8f-121">O segundo parâmetro, `index`, representa o índice do elemento atual na coleção.</span><span class="sxs-lookup"><span data-stu-id="80d8f-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="80d8f-122">A expressão `Where` retorna todas as cadeias de caracteres cujos comprimentos são menores do que suas posições de índice na matriz.</span><span class="sxs-lookup"><span data-stu-id="80d8f-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a><span data-ttu-id="80d8f-123">Definição de corpo da expressão</span><span class="sxs-lookup"><span data-stu-id="80d8f-123">Expression body definition</span></span>

<span data-ttu-id="80d8f-124">Uma definição de corpo da expressão fornece uma implementação de um membro em um formato legível e altamente condensado.</span><span class="sxs-lookup"><span data-stu-id="80d8f-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="80d8f-125">Ela tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="80d8f-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="80d8f-126">em que *expression* é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="80d8f-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="80d8f-127">Observe que *expression* pode ser uma *expressão de instrução* apenas se o tipo de retorno do membro é `void` ou se o membro é um construtor ou um finalizador.</span><span class="sxs-lookup"><span data-stu-id="80d8f-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="80d8f-128">Há suporte para definições de corpo da expressão para métodos e instruções get da propriedade do C# 6 em diante.</span><span class="sxs-lookup"><span data-stu-id="80d8f-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="80d8f-129">Há suporte para definições de corpo da expressão para construtores, finalizadores, instruções de set da propriedade e indexadores do C# 7 em diante.</span><span class="sxs-lookup"><span data-stu-id="80d8f-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="80d8f-130">Veja abaixo uma definição de corpo da expressão para um método `Person.ToString`:</span><span class="sxs-lookup"><span data-stu-id="80d8f-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="80d8f-131">É uma versão abreviada da seguinte definição de método:</span><span class="sxs-lookup"><span data-stu-id="80d8f-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="80d8f-132">Para obter informações mais detalhadas sobre definições de corpo da expressão, confira [Membros com corpo da expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="80d8f-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80d8f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80d8f-133">See Also</span></span>

- [<span data-ttu-id="80d8f-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="80d8f-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)   
- [<span data-ttu-id="80d8f-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="80d8f-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)   
- [<span data-ttu-id="80d8f-136">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="80d8f-136">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- <span data-ttu-id="80d8f-137">[Membros com corpo da expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="80d8f-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>
