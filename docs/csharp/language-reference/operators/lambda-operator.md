---
title: "Operador =&gt; (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a75967e61d2c674e87e321de1fb6e4062cca4f19
ms.lasthandoff: 03/13/2017

---
# <a name="gt-operator-c-reference"></a>Operador =&gt; (Referência de C#)
O token `=>` é chamado de operador lambda. Ele é usado em *expressões lambda* para separar as variáveis de entrada no lado esquerdo do corpo lambda no lado direito. As expressões lambda são expressões embutidas semelhantes aos métodos anônimos, mas mais flexíveis, elas são amplamente usadas em consultas LINQ que são expressas na sintaxe do método. Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 O exemplo a seguir mostra duas maneiras de localizar e exibir o comprimento da cadeia de caracteres mais curta em uma matriz de cadeias de caracteres. A primeira parte do exemplo aplica uma expressão lambda (`w => w.Length`) a cada elemento da matriz `words` e, em seguida, usa o método <xref:System.Linq.Enumerable.Min%2A> para encontrar o menor tamanho. Para comparação, a segunda parte do exemplo mostra uma solução mais longa que usa a sintaxe de consulta para fazer o mesmo.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="remarks"></a>Comentários  
 O operador `=>` tem a mesma precedência do operador de atribuição (`=`) e é associativo à direita.  
  
 Você pode especificar o tipo da variável de entrada explicitamente ou deixar que o compilador o infira, em ambos os casos, a variável é fortemente tipada no tempo de compilação. Quando você especificar um tipo, deverá colocar o nome do tipo e o nome da variável entre parênteses, como mostra o exemplo a seguir.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como escrever uma expressão lambda para a sobrecarga do operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> que utiliza dois argumentos. Como a expressão lambda tem mais de um parâmetro, os parâmetros devem ser colocados entre parênteses. O segundo parâmetro, `index`, representa o índice do elemento atual na coleção. A expressão `Where` retorna todas as cadeias de caracteres cujos comprimentos são menores do que suas posições de índice na matriz.  
  
```cs  
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
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
