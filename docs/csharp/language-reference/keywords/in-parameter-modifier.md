---
title: Modificador de parâmetro in (referência do C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a>Modificador de parâmetro in (referência do C#)

A palavra-chave `in` faz com que os argumentos sejam passados por referência. É como as palavras-chave [ref](ref.md) ou [out](out-parameter-modifier.md), exceto que os argumentos `in` não podem ser modificados pelo método chamado. Os argumentos `ref` podem ser modificados e os argumentos `out` precisam ser modificados pelo chamador, e essas modificações poderão ser observadas no contexto da chamada.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

O exemplo anterior demonstra que o modificador `in` é desnecessário no site da chamada. Ele apenas é necessário na declaração do método.

> [!NOTE] 
> A palavra-chave `in` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é contravariante, como parte de uma instrução `foreach` ou como parte de uma cláusula `join` em uma consulta LINQ. Para obter mais informações sobre o uso da palavra-chave `in` nesses contextos, confira [in](in.md) que fornece links para todos os tipos de uso.
  
 As variáveis passadas como argumentos `in` precisam ser inicializadas antes de serem passadas em uma chamada de método. No entanto, o método chamado não pode atribuir um valor nem modificar o argumento.  
  
 Embora as palavras-chave `in`, `ref` e `out` causem um comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no tempo de compilação. Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`. Por exemplo, o código a seguir, não será compilado:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
A sobrecarga baseada na presença de `in` é permitida, mas gera um aviso do compilador:  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

As propriedades ou constantes podem ser passadas como parâmetros `in`, porque o método de chamada não pode modificar seus valores.
  
Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:  
  
- Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).  
  
- Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  

Normalmente, os argumentos `in` são declarados para evitar as operações de cópia necessárias para passar argumentos por valor. Isso é mais útil quando os argumentos são tipos de valor, como estruturas, em que as operações de cópia são mais dispendiosas do que a passagem por referência.

> [!WARNING]
>  Os parâmetros `in` podem ser ainda mais dispendiosos se usados de forma incorreta. O compilador pode não saber se os métodos do membro modificam o estado do struct. Quando o compilador não pode garantir que o objeto não será modificado, ele cria uma cópia defensivamente e chama as referências de membro usando essa cópia. Todas as modificações possíveis são feitas nessa cópia de defesa. As duas maneiras de evitar essas cópias são passar parâmetros `in` como argumentos `in` ou definir estruturas como `readonly struct`.

## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Semântica de referência com Tipos de valor](../../../csharp/reference-semantics-with-value-types.md)
