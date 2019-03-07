---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8d1c2a958fa148238eaeedb9c2af3df2cb86d33d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502595"
---
# <a name="example-visual-basic"></a>\<exemplo > (Visual Basic)
Especifica um exemplo para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do exemplo de código.  
  
## <a name="remarks"></a>Comentários  
 O `<example>` marca permite que você especifique um exemplo de como usar um método ou outro membro da biblioteca. Normalmente, isso envolve o uso da marca [\<code>](../../../visual-basic/language-reference/xmldoc/code.md).  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<example>` tag para incluir um exemplo para usar o `ID` campo.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
