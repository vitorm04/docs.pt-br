---
title: "ref (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 353abf8a0c852acbbb2949f9640c1465dec8593b
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---

# <a name="ref-c-reference"></a>ref (Referência de C#)
A palavra-chave `ref` faz com que um argumento seja passado por referência, não por valor. O efeito de passar por referência é que qualquer alteração no parâmetro do método chamado será refletida no método chamado. Por exemplo, se o chamador passa uma expressão variável local ou uma expressão de acesso do elemento de matriz e o método chamado substituir o objeto ao qual o parâmetro ref se refere, então a variável local do chamador ou o elemento da matriz fará agora referência ao novo objeto.  
  
> [!NOTE]
>  Não confunda o conceito de passar por referência com o conceito de tipos de referência. Os dois conceitos não são iguais. Um parâmetro de método pode ser modificado por `ref`, independentemente de ele ser um tipo de valor ou um tipo de referência. Não há nenhuma conversão boxing de um tipo de valor quando ele é passado por referência.  
  
 Para usar um parâmetro `ref`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `ref`, como mostrado no exemplo a seguir.  
  
 [!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]  
  
 Um argumento que é passado para um parâmetro `ref` deve ser inicializado antes de ser passado. Isso é diferente dos parâmetros `out`, cujos argumentos não precisam ser inicializados explicitamente antes de serem passados. Para obter mais informações, consulte [out](../../../csharp/language-reference/keywords/out.md).  
  
 Os membros de uma classe não podem ter assinaturas que diferem somente por `ref` e `out`. Ocorrerá um erro de compilador se a única diferença entre os dois membros de um tipo for que um deles possui um parâmetro `ref` e o outro possui um parâmetro `out`. O código a seguir, por exemplo, não é compilado.  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]  
  
 No entanto, pode haver sobrecarga quando um método tiver um parâmetro `ref` ou `out` e o outro tiver um parâmetro de valor, como mostrado no exemplo a seguir.  
  
 [!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]  
  
 Em outras situações que exigem correspondência de assinatura, como ocultar ou substituir, `ref` e `out` fazem parte da assinatura e não são correspondentes.  
  
 Propriedades não são variáveis. Elas são métodos e não podem ser passadas para parâmetros `ref`.  
  
 Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Não é possível usar as palavras-chave `ref` e `out` para os seguintes tipos de métodos:  
  
-   Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).  
  
-   Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  
  
## <a name="example"></a>Exemplo  
 Os exemplos anteriores demonstram o que acontece quando você passa tipos de valor por referência. Também é possível usar a palavra-chave `ref` para passar tipos de referência. Passar um tipo de referência por referência permite que o método chamado substitua o objeto no método de chamada ao qual se refere o parâmetro de referência. O local de armazenamento do objeto é passado para o método como o valor do parâmetro de referência. Se você alterar o valor no local de armazenamento do parâmetro (para apontar para um novo objeto), irá alterar também o local de armazenamento ao qual se refere o chamador. O exemplo a seguir passa uma instância de um tipo de referência como um parâmetro `ref`. Para obter mais informações sobre como passar tipos de referência por valor e por referência, consulte [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).  
  
 [!code-cs[csrefKeywordsMethodParams#8](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Passando Parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)   

 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
