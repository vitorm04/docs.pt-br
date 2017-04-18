---
title: "Marcas XML recomendadas para comentários da documentação (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
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
ms.openlocfilehash: c6a47c12bc24864ef6ac9f80054becad98ec97f1
ms.lasthandoff: 03/13/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>marcações XML recomendadas para comentários da documentação (Visual Basic)
O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador pode processar comentários de documentação em seu código para um arquivo XML. Você pode usar ferramentas adicionais para processar o arquivo XML em documentação.  
  
 Comentários XML são permitidos em construções de código, como tipos e membros de tipo. Para tipos parciais, apenas uma parte do tipo pode ter comentários XML, embora não haja nenhuma restrição em comentar seus membros.  
  
> [!NOTE]
>  Comentários de documentação não podem ser aplicados a namespaces. O motivo é que um namespace pode abranger vários assemblies, e não todos os assemblies tenham que ser carregados ao mesmo tempo.  
  
 O compilador processa qualquer marca que é XML válido. As seguintes marcas fornecem funcionalidades comumente usadas na documentação do usuário.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<código >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<exemplo >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exceção >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<incluir >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permissão >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<comentários >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<Retorna >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<Consulte também >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<Resumo >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<valor >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> o compilador verifica a sintaxe.)  
  
> [!NOTE]
>  Se você quiser que colchetes angulares sejam exibido no texto de um comentário de documentação, use `<` e `>`. Por exemplo, a cadeia de caracteres `"<text in angle brackets>"` será exibido como `<text in angle``brackets>`.  
  
## <a name="see-also"></a>Consulte também  
 [Documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
