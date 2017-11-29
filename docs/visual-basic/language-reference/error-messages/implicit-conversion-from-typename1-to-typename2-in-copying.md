---
title: "Conversão implícita de &#39; &lt;typename1&gt;&#39; para &#39;&lt; typename2&gt;&#39; ao copiar o valor de &#39; ByRef &#39; parâmetro &#39; &lt;parametername&gt;&#39; volta para o argumento correspondente."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Conversão implícita de &#39; &lt;typename1&gt;&#39; para &#39;&lt; typename2&gt;&#39; ao copiar o valor de &#39; ByRef &#39; parâmetro &#39; &lt;parametername&gt;&#39; volta para o argumento correspondente.
Um procedimento é chamado com um [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumento de um tipo diferente do seu parâmetro correspondente.  
  
 Se você passar um argumento `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] algumas vezes copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência. Nesse caso, quando o procedimento retorna, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve copiar o valor da variável local novamente para o argumento no código de chamada.  
  
 Se um `ByRef` o valor do argumento é copiado para o procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária. Porém, se os tipos forem diferentes, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve converter em ambas as direções. Porque você não pode usar `CType` ou qualquer um dos outros conversão palavras-chave em um argumento de procedimento ou parâmetro, tal conversão sempre está implícito.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC41999  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, portanto [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não precisa fazer nenhuma conversão.  
  
-   Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro, mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parâmetros e Argumentos de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Passando Argumentos por Valor e por Referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
