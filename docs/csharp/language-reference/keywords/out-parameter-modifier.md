---
title: Modificador de parâmetro out – Referência de C#
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 704b66e6cdec5caa47f85ed8e3acbd2a6a73b730
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598237"
---
# <a name="out-parameter-modifier-c-reference"></a>Modificador de parâmetro out (Referência de C#)
A palavra-chave `out` faz com que os argumentos sejam passados por referência. Ela torna o parâmetro formal um alias para o argumento, que deve ser uma variável. Em outras palavras, qualquer operação no parâmetro é feita no argumento. É como a palavra-chave [ref](ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada. Também é como a palavra-chave [in](in-parameter-modifier.md), exceto que `in` não permite que o método chamado modifique o valor do argumento. Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`. Por exemplo:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante. Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](out-generic-modifier.md).
  
Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método. No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.  
  
As palavras-chave `in`, `ref` e `out` não são consideradas parte da assinatura do método para fins de resolução de sobrecarga. Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`. Por exemplo, o código a seguir, não será compilado:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
A sobrecarga será válida, no entanto, se um método usar um argumento `ref`, `in` ou `out` e o outro não tiver nenhum desses modificadores, desta forma:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

O compilador escolherá a melhor sobrecarga correspondendo os modificadores de parâmetro no site de chamada aos modificadores de parâmetro usados na chamada do método.
 
Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.
  
Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:  
  
- Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).  
  
- Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  

## <a name="declaring-out-parameters"></a>Declarando parâmetros `out`   

Declarar um método com argumentos `out` é uma solução clássica para retornar vários valores. Começando com o C# 7.0, considere [tuplas](../../tuples.md) para cenários semelhantes. O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método. Observe que o terceiro argumento é atribuído a null. Isso permite que os métodos retornem valores opcionalmente.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Chamando um método com um argumento `out`

No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`. O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Começando com o C#7.0, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada. Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método. O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
No exemplo anterior, a variável `number` é fortemente tipada como um `int`. Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
- [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)
