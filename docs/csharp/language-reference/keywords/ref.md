---
title: "ref (Referência de C#)"
ms.date: 2017-05-30
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 003125ca6218d42a919d8bb592b5454a7cb387c7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ref-c-reference"></a>ref (Referência de C#)

A palavra-chave `ref` indica um valor que é passado por referência. Ele é usado em três contextos diferentes: 

- Em uma assinatura de método e em uma chamada de método, para passar um argumento a um método por referência. Consulte [Passar um argumento por referência](#passing-an-argument-by-reference) para obter mais informações.

- Em uma assinatura de método para retornar um valor para o chamador por referência. Para obter mais informações, consulte [Valores retornados por referência](#reference-return-values).

- Em um corpo de membro, para indicar que um valor retornado por referência é armazenado localmente como uma referência que o chamador pretende modificar. Consulte [Ref locals](#ref-locals) para obter mais informações.

## <a name="passing-an-argument-by-reference"></a>Passando um argumento por referência

Quando usado na lista de parâmetros do método, a palavra-chave `ref` indica que um argumento é passado por referência, não por valor. O efeito de passar por referência é que qualquer alteração no argumento do método chamado será refletida no método chamado. Por exemplo, se o chamador passa uma expressão variável local ou uma expressão de acesso do elemento de matriz e o método chamado substituir o objeto ao qual o parâmetro ref se refere, então a variável local do chamador ou o elemento da matriz fará agora referência ao novo objeto quando o método retornar.

> [!NOTE]
>  Não confunda o conceito de passar por referência com o conceito de tipos de referência. Os dois conceitos não são iguais. Um parâmetro de método pode ser modificado por `ref`, independentemente de ele ser um tipo de valor ou um tipo de referência. Não há nenhuma conversão boxing de um tipo de valor quando ele é passado por referência.  

Para usar um parâmetro `ref`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `ref`, como mostrado no exemplo a seguir.  

[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

Um argumento que é passado para um parâmetro `ref` deve ser inicializado antes de ser passado. Isso é diferente dos parâmetros [out](out.md), cujos argumentos não precisam ser inicializados explicitamente antes de serem passados.

Os membros de uma classe não podem ter assinaturas que diferem somente por `ref` e `out`. Ocorrerá um erro de compilador se a única diferença entre os dois membros de um tipo for que um deles possui um parâmetro `ref` e o outro possui um parâmetro `out`. O código a seguir, por exemplo, não é compilado.  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 No entanto, pode haver sobrecarga quando um método tiver um parâmetro `ref` ou `out` e o outro tiver um parâmetro de valor, conforme mostrado no exemplo a seguir.
  
 [!code-cs[ref e sobrecargas](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 Em outras situações que exigem correspondência de assinatura, como ocultar ou substituir, `ref` e `out` fazem parte da assinatura e não são correspondentes.  
  
 Propriedades não são variáveis. Elas são métodos e não podem ser passadas para parâmetros `ref`.  
  
 Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Não é possível usar as palavras-chave `ref` e `out` para os seguintes tipos de métodos:  
  
-   Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).  
  
-   Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  
  
## <a name="passing-an-argument-by-reference-an-example"></a>Passando um argumento por referência: um exemplo

Os exemplos anteriores passam tipos de valor por referência. Você também pode usar a palavra-chave `ref` para passar tipos de referência por referência. Passar um tipo de referência por referência permite que o método chamado substitua o objeto ao qual se refere o parâmetro de referência no chamador. O local de armazenamento do objeto é passado para o método como o valor do parâmetro de referência. Se você alterar o valor no local de armazenamento do parâmetro (para apontar para um novo objeto), irá alterar também o local de armazenamento ao qual se refere o chamador. O exemplo a seguir passa uma instância de um tipo de referência como um parâmetro `ref`.   
  
 [!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

Para obter mais informações sobre como passar tipos de referência por valor e por referência, consulte [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Valores retornados por referência

Valores retornados por referência (ou ref returns) são valores que um método retorna por referência para o chamador. Ou seja, o chamador pode modificar o valor retornado por um método e essa alteração será refletida no estado do objeto que contém o método. 

Um valor retornado por referência é definido usando a palavra-chave `ref`:

- Na assinatura do método. Por exemplo, a seguinte método assinatura indica por que o método `GetCurrentPrice` retorna um valor <xref:System.Decimal> por referência.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Antes de cada instrução `return` no método. Por exemplo:
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

Para que o chamador modifique o estado de um objeto, o valor retornado de referência deve ser armazenado em uma variável que é definida explicitamente como um [ref local](#ref-locals). 

Para obter um exemplo, consulte [Um exemplo de ref returns e ref locals](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Ref locals

Uma variável de ref local é usada para fazer referência a valores retornados usando `ref return`.  Uma variável de ref local deve ser inicializada e atribuída a um valor retornado ref local. Todas as modificações ao valor do ref local são refletidas no estado do objeto cujo método retornou o valor por referência.

Você define um ref local usando a palavra-chave `ref` antes da declaração de variável, bem como imediatamente antes da chamada para o método que retorna o valor por referência. 

Por exemplo, a instrução a seguir define um valor de ref local que é retornado por um método chamado `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Observe que a palavra-chave `ref` deve ser usada em ambos os locais ou o compilador gera o erro CS8172, "Não é possível inicializar uma variável por referência com um valor". 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>Um exemplo de ref returns e ref locals

O exemplo a seguir define uma classe `Book` que tem dois campos <xref:System.String>, `Title` e `Author`. Ele também define uma classe `BookCollection` que inclui uma matriz privada de objetos `Book`. Objetos de catálogo individuais são retornados por referência chamando o respectivo método `GetBookByTitle`.

[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

Quando o chamador armazena o valor retornado pelo método `GetBookByTitle` como um ref local, as alterações que o chamador faz ao valor retornado são refletidas no objeto `BookCollection`, conforme mostra o exemplo a seguir.

[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Passando Parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)   
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)

