---
title: "Conversão implícita de &quot;&lt;typename1&gt;&quot;para&quot;&lt;typename2&gt;&quot;ao copiar o valor do parâmetro &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot; para o argumento correspondente. | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
dev_langs:
- VB
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: e397241aab78e17ea4efde0ea682d0e237fb8f8a
ms.lasthandoff: 03/13/2017

---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>Conversão implícita de '&lt;typename1&gt;'para'&lt;typename2&gt;'ao copiar o valor do parâmetro 'ByRef' '&lt;parametername&gt;' para o argumento correspondente.
Um procedimento é chamado com um [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumento de um tipo diferente do seu parâmetro correspondente.  
  
 Se você passar um argumento `ByRef`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] algumas vezes copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência. Nesse caso, quando o procedimento retorna, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve copiar o valor da variável local novamente para o argumento no código de chamada.  
  
 Se um `ByRef` o valor do argumento é copiado no procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária. Mas se os tipos forem diferentes, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve converter em ambas as direções. Porque você não pode usar `CType` ou qualquer um dos outras conversão palavras-chave em um argumento de procedimento ou parâmetro, essa conversão é sempre implícita.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC41999  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, dessa forma [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa fazer nenhuma conversão.  
  
-   Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Argumentos e parâmetros de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passando argumentos por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
