---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563866"
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
Indica que o texto dentro uma descrição é o código.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---|---|  
|`text`|O texto que você deseja indicar como código.|  
  
## <a name="remarks"></a>Comentários  
 O `<c>` marcação oferece uma maneira de indicar que o texto dentro uma descrição deve ser marcado como código. Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<c>` marca na seção de resumo para indicar que `Counter` é o código.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
