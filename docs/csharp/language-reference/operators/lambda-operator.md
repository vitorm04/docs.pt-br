---
title: "Operador =&gt; (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "=>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Operador lambda [C#]"
  - "Operador => [C#]"
  - "as expressões lambda [c#], = > operador"
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Operador =&gt; (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `=>` token é chamado de operador lambda. Ele é usado no *expressões lambda* para separar as variáveis de entrada no lado esquerdo do corpo lambda no lado direito. Expressões lambda são embutidas expressões semelhantes aos métodos anônimos, mas mais flexível; elas são usadas amplamente em consultas LINQ que são expressos em sintaxe de método. Para obter mais informações, consulte [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 O exemplo a seguir mostra duas maneiras de localizar e exibir o comprimento da cadeia de caracteres mais curta em uma matriz de cadeias de caracteres. A primeira parte do exemplo se aplica a uma expressão lambda \(`w => w.Length`\) a cada elemento do `words` matriz e, em seguida, usa o <xref:System.Linq.Enumerable.Min%2A> método para descobrir o tamanho menor. Para comparação, a segunda parte do exemplo mostra uma solução mais que usa a sintaxe de consulta para fazer a mesma coisa.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## Comentários  
 O `=>` operador tem a mesma precedência de operador de atribuição \(`=`\) e é associativo direito.  
  
 Você pode especificar o tipo da variável de entrada explicitamente ou deixar que o compilador inferir em ambos os casos, a variável é fortemente tipada em tempo de compilação. Quando você especifica um tipo, você deverá colocar o nome do tipo e o nome da variável entre parênteses, como mostra o exemplo a seguir.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## Exemplo  
 O exemplo a seguir mostra como escrever uma expressão lambda para a sobrecarga de operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> que leva dois argumentos. Como a expressão lambda tem mais de um parâmetro, os parâmetros devem ser colocados entre parênteses. O segundo parâmetro, `index`, representa o índice do elemento atual na coleção. O `Where` expressão retorna todas as strings comprimentos forem menores do que as posições de índice na matriz.  
  
```c#  
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
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)