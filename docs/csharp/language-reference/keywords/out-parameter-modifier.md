---
title: "Modificador de parâmetro out (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a>Modificador de parâmetro out (Referência de C#)
A palavra-chave `out` faz com que os argumentos sejam passados por referência. É como a palavra-chave [ref](../../../csharp/language-reference/keywords/ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada. Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`. Por exemplo:  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante. Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](../../../csharp/language-reference/keywords/out-generic-modifier.md).
  
 Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método. No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.  
  
 Embora as palavras-chave `ref` e `out` causem comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no momento da compilação. Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método terá um argumento `ref` e o outro utilizará um argumento `out`. Por exemplo, o código a seguir, não será compilado:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
No entanto, a sobrecarga será válida se um método usar um argumento `ref` ou `out` e o outro não usar nenhum, da seguinte forma:  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.  
  
 Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Não é possível usar as palavras-chave `ref` e `out` para os seguintes tipos de métodos:  
  
-   Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).  
  
-   Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  

## <a name="declaring-out-arguments"></a>Declarando argumentos `out`   

 Declarar um método com argumentos `out` é útil quando você deseja que um método retorne vários valores. O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método. Observe que o terceiro argumento é atribuído a null. Isso permite que os métodos retornem valores opcionalmente.  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 O [padrão Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) envolve retornar um `bool` para indicar se uma operação teve êxito ou falhou, bem como retornar o valor produzido pela operação em um argumento `out`. Diversos métodos de análise, como o método [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), usam esse padrão.
   
## <a name="calling-a-method-with-an-out-argument"></a>Chamando um método com um argumento `out`

No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`. O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

A partir do C#7, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada. Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método. O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
No exemplo anterior, a variável `number` é fortemente tipada como um `int`. Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)
