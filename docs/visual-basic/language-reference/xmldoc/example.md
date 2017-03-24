---
title: '&lt;exemplo&gt; (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
caps.latest.revision: 9
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
ms.openlocfilehash: 279b9e675e358ce8d5aa2171984c0e48afe66558
ms.lasthandoff: 03/13/2017

---
# <a name="ltexamplegt-visual-basic"></a>&lt;exemplo&gt; (Visual Basic)
Especifica um exemplo para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do código de exemplo.  
  
## <a name="remarks"></a>Comentários  
 O `<example>` marca permite que você especifique um exemplo de como usar um método ou outro membro da biblioteca. Isso normalmente envolve usar a [ \<código >](../../../visual-basic/language-reference/xmldoc/code.md) marca.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<example>` tag para incluir um exemplo para usar o `ID` campo.  
  
 [!code-vb[VbVbcnXmlDocComments n º&2;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
