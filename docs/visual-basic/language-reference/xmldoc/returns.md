---
title: '&lt;Retorna&gt; (Visual Basic) | Documentos do Microsoft'
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
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: 9
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
ms.openlocfilehash: 0506d3b19a1b495eb4055c7a5682bf1d46db8567
ms.lasthandoff: 03/13/2017

---
# <a name="ltreturnsgt-visual-basic"></a>&lt;Retorna&gt; (Visual Basic)
Especifica o valor de retorno da propriedade ou função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do valor de retorno.  
  
## <a name="remarks"></a>Comentários  
 Use o `<returns>` marca de comentário para uma declaração de método descrever o valor de retorno.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<returns>` marca para explicar o que o `DoesRecordExist` retornos de função.  
  
 [!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
