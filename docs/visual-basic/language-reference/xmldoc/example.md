---
title: '&lt;exemplo&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e34b75f4ce924a35dd5396b449730316025a9f35
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltexamplegt-visual-basic"></a>&lt;exemplo&gt; (Visual Basic)
Especifica um exemplo para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do exemplo de código.  
  
## <a name="remarks"></a>Comentários  
 O `<example>` marca permite que você especifique um exemplo de como usar um método ou outro membro da biblioteca. Normalmente, isso envolve o uso da marca [\<code>](../../../visual-basic/language-reference/xmldoc/code.md).  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<example>` marca para incluir um exemplo para usar o `ID` campo.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
