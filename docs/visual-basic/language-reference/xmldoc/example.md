---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 510b00d2220b9c65b0e2b8fa3ead70925a9f54ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821914"
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
