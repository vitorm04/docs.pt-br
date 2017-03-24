---
title: "&lt;comentários&gt; (Visual Basic) | Documentos do Microsoft"
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
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
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
ms.openlocfilehash: 89f8d321505b528d07fd04780cec06fb65b0e05e
ms.lasthandoff: 03/13/2017

---
# <a name="ltremarksgt-visual-basic"></a>&lt;comentários&gt; (Visual Basic)
Especifica uma seção de comentários para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do membro.  
  
## <a name="remarks"></a>Comentários  
 Use o `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).  
  
 Essas informações aparecem no Pesquisador de objetos. Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<remarks>` marca para explicar o que o `UpdateRecord` método faz.  
  
 [!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
