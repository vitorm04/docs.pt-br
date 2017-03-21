---
title: "Copiar o valor do parâmetro &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot;para o argumento correspondente limita do tipo&quot;&lt;typename1&gt;&quot; no tipo&quot;&lt;typename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84574006b2e2ccc669fdd83ebfb6eec06b00f041
ms.lasthandoff: 03/13/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Copiar o valor do parâmetro 'ByRef' '&lt;parametername&gt;'para o argumento correspondente limita do tipo'&lt;typename1&gt;' no tipo'&lt;typename2&gt;'
Um procedimento é chamado com um argumento que amplia para o tipo de parâmetro correspondente e a conversão do parâmetro para o argumento é restritiva.  
  
 Quando você define uma classe ou estrutura, você pode definir um ou mais operadores de conversão para converter esse tipo de classe ou estrutura para outros tipos. Você também pode definir operadores de conversão reversa para converter esses tipos de volta para sua classe ou tipo de estrutura. Quando você usa o tipo de classe ou estrutura em uma chamada de procedimento [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode usar esses operadores de conversão para converter o tipo de um argumento para o tipo de seu parâmetro correspondente.  
  
 Se você passar o argumento [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] algumas vezes copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência. Nesse caso, quando o procedimento retorna, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve copiar o valor da variável local novamente para o argumento no código de chamada.  
  
 Se um `ByRef` o valor do argumento é copiado no procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária. Mas se os tipos forem diferentes, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve converter em ambas as direções. Se um dos tipos é o tipo de classe ou estrutura, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve convertê-lo para e de outro tipo. Se uma dessas conversões está ampliando, a conversão reversa pode estar restringindo.  
  
 **ID do erro:** BC32053  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, dessa forma [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa fazer nenhuma conversão.  
  
-   Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.  
  
-   Se você precisar retornar um valor para o argumento de chamada, defina o operador de conversão inversa como [Widening](../../../visual-basic/language-reference/modifiers/widening.md), se possível.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Argumentos e parâmetros de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passando argumentos por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [Como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
