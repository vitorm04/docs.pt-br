---
title: "&lt;código&gt; (Visual Basic) | Documentos do Microsoft"
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
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: 10
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
ms.openlocfilehash: ad9437d2d3f84ab3cb441a9424eba00844358c39
ms.lasthandoff: 03/13/2017

---
# <a name="ltcodegt-visual-basic"></a>&lt;código&gt; (Visual Basic)
Indica que o texto de várias linhas de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `content`  
 O texto para marcar como código.  
  
## <a name="remarks"></a>Comentários  
 Use o `<code>` marca para indicar várias linhas como código. Use [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o \<código > tag para incluir o código de exemplo para usar o `ID` campo.  
  
 [!code-vb[VbVbcnXmlDocComments n º&2;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
