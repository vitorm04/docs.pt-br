---
title: "A c&#243;pia do par&#226;metro &#39;&lt;parametername&gt;&#39; do valor &#39;ByRef&#39; de volta para o argumento correspondente &#233; restrita do tipo &#39;&lt;typename1&gt;&#39; para o tipo &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32053"
  - "vbc32053"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32053"
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A c&#243;pia do par&#226;metro &#39;&lt;parametername&gt;&#39; do valor &#39;ByRef&#39; de volta para o argumento correspondente &#233; restrita do tipo &#39;&lt;typename1&gt;&#39; para o tipo &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um procedimento é chamado com um argumento que amplia a tipo de parâmetro de correspondente, e conversão do parâmetro para o argumento o restringe.  
  
 Quando você define uma classe ou estrutura, você pode definri um ou mais operadores de conversão para converter aquela tipo classe ou estrutura para outros tipos.  Você também pode definir operadores de conversão reversa para converter aqueles outros tipos de volta para seu tipo de classe ou estrutura.  Quando você usa sua classe ou tipo de estrutura numa chamada de procedimento, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode usar esses operadores de conversão para converter o tipo de um argumento para o tipo de seu parâmetro correspondente.  
  
 Se você passar o argumento [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] algumas vezes copia o valor do argumento para um variável local no procedimento em vez de passar uma referência.  Nesse caso, quando o procedimento retona, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve copiar o valor da variável local de volta para o argumento no código que chamou.  
  
 Se um valor de argumento `ByRef` é copiado no procedimento e o argumento e parâmetro são do mesmo tipo, não é necessária nenhuma conversão.  Mas se os tipos são diferentes, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve converter em ambas as direções.  Se um dos tipos é sua classe ou tipo de estrutura, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve convertê\-lo tanto de quanto para o outro tipo.  Se um dessas conversões está ampliando, a conversão reversa pode estar restringindo.  
  
 **Identificação do erro:**  BC32053  
  
### Para corrigir este erro  
  
-   Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, dessa forma o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa fazer nenhuma conversão.  
  
-   Se você precisar chamar o procedimento com um tipo de argumento diferente do tipo de parâmetro mas não precisa de retornar um valor no argumento chamante, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.  
  
-   Se você precisar retornar um valor para o argumento de chamada, defina o operador de conversão inversa como [Widening](../../../visual-basic/language-reference/modifiers/widening.md), se possível.  
  
## Consulte também  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passando argumentos por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)