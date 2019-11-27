---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348487"
---
# <a name="example-visual-basic"></a>> de exemplo de \<(Visual Basic)
Especifica um exemplo para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do exemplo de código.  
  
## <a name="remarks"></a>Comentários  
 A marca `<example>` permite especificar um exemplo de como usar um método ou outro membro da biblioteca. Normalmente, isso envolve o uso da marca [\<code>](../../../visual-basic/language-reference/xmldoc/code.md).  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca de `<example>` para incluir um exemplo para usar o campo `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
