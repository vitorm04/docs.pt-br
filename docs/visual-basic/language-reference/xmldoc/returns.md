---
title: '&lt;Retorna&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6130a6fabe450900fe19ef4d361654508f907ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltreturnsgt-visual-basic"></a>&lt;Retorna&gt; (Visual Basic)
Especifica o valor de retorno da propriedade ou função.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do valor retornado.  
  
## <a name="remarks"></a>Comentários  
 Use o `<returns>` marca de comentário de uma declaração de método descrever o valor de retorno.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<returns>` marca para explicar o que o `DoesRecordExist` função retorna.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
