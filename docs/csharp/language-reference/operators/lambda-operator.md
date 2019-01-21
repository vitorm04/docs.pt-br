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
# <a name="gt-operator-c-reference"></a>Operador =&gt; (Referência de C#)

O operador `=>` pode ser usado de duas maneiras no C#:

- Assim como o [operador lambda](#lambda-operator) em uma [expressão lambda](../../lambda-expressions.md), ele separa as variáveis de entrada do corpo lambda.
 
- Em uma [definição de corpo da expressão](#expression-body-definition), ele separa um nome de membro da implementação do membro. 

## <a name="lambda-operator"></a>Operador lambda

O token `=>` é chamado de operador lambda. Ele é usado em *expressões lambda* para separar as variáveis de entrada no lado esquerdo do corpo lambda no lado direito. As expressões lambda são expressões embutidas semelhantes aos métodos anônimos, mas mais flexíveis, elas são amplamente usadas em consultas LINQ que são expressas na sintaxe do método. Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 O exemplo a seguir mostra duas maneiras de localizar e exibir o comprimento da cadeia de caracteres mais curta em uma matriz de cadeias de caracteres. A primeira parte do exemplo aplica uma expressão lambda (`w => w.Length`) a cada elemento da matriz `words` e, em seguida, usa o método <xref:System.Linq.Enumerable.Min%2A> para encontrar o menor tamanho. Para comparação, a segunda parte do exemplo mostra uma solução mais longa que usa a sintaxe de consulta para fazer o mesmo.  
  
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
  
### <a name="remarks"></a>Comentários  
 O operador `=>` tem a mesma precedência do operador de atribuição (`=`) e é associativo à direita.  
  
 Você pode especificar o tipo da variável de entrada explicitamente ou deixar que o compilador o infira, em ambos os casos, a variável é fortemente tipada no tempo de compilação. Quando você especificar um tipo, deverá colocar o nome do tipo e o nome da variável entre parênteses, como mostra o exemplo a seguir.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como escrever uma expressão lambda para a sobrecarga do operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>, que utiliza dois argumentos. Como a expressão lambda tem mais de um parâmetro, os parâmetros devem ser colocados entre parênteses. O segundo parâmetro, `index`, representa o índice do elemento atual na coleção. A expressão `Where` retorna todas as cadeias de caracteres cujos comprimentos são menores do que suas posições de índice na matriz.  
  
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
## <a name="expression-body-definition"></a>Definição de corpo da expressão

Uma definição de corpo da expressão fornece uma implementação de um membro em um formato legível e altamente condensado. Ela tem a seguinte sintaxe geral:

```csharp
member => expression;
```
em que *expression* é uma expressão válida. Observe que *expression* pode ser uma *expressão de instrução* apenas se o tipo de retorno do membro é `void` ou se o membro é um construtor ou um finalizador.

Há suporte para definições de corpo da expressão para métodos e instruções get da propriedade do C# 6 em diante. Há suporte para definições de corpo da expressão para construtores, finalizadores, instruções de set da propriedade e indexadores do C# 7 em diante.

Veja abaixo uma definição de corpo da expressão para um método `Person.ToString`:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

É uma versão abreviada da seguinte definição de método:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
Para obter informações mais detalhadas sobre definições de corpo da expressão, confira [Membros com corpo da expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)   
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
- [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- [Membros com corpo da expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).
