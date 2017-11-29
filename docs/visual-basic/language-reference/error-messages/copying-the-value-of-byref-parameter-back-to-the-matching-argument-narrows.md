---
title: "Copiar o valor de &#39; ByRef &#39; parâmetro &#39; &lt;parametername&gt;&#39; volta para a correspondência restringe de argumento de tipo de &#39;&lt; typename1&gt;&#39; para o tipo &#39;&lt; typename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Copiar o valor de &#39; ByRef &#39; parâmetro &#39; &lt;parametername&gt;&#39; volta para a correspondência restringe de argumento de tipo de &#39;&lt; typename1&gt;&#39; para o tipo &#39;&lt; typename2&gt;&#39;
Um procedimento é chamado com um argumento que amplia para o tipo do parâmetro correspondente, e a conversão do parâmetro para o argumento é restritiva.  
  
 Quando você define uma classe ou estrutura, você pode definir um ou mais operadores de conversão para converter esse tipo de classe ou estrutura para outros tipos. Você também pode definir operadores de conversão inversa para converter esses tipos de volta para sua classe ou tipo de estrutura. Quando você usa o tipo de classe ou estrutura em uma chamada de procedimento, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pode usar esses operadores de conversão para converter o tipo de um argumento para o tipo de seu parâmetro correspondente.  
  
 Se você passar o argumento [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] algumas vezes copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência. Nesse caso, quando o procedimento retorna, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve copiar o valor da variável local novamente para o argumento no código de chamada.  
  
 Se um `ByRef` o valor do argumento é copiado para o procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária. Porém, se os tipos forem diferentes, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve converter em ambas as direções. Se um dos tipos é o tipo de classe ou estrutura, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve converter para e o outro tipo. Se um dessas conversões está ampliando, a conversão reversa pode estar restringindo.  
  
 **ID do erro:** BC32053  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, portanto [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não precisa fazer nenhuma conversão.  
  
-   Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro, mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.  
  
-   Se você precisar retornar um valor para o argumento de chamada, defina o operador de conversão inversa como [Widening](../../../visual-basic/language-reference/modifiers/widening.md), se possível.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parâmetros e Argumentos de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Procedimentos de Operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
