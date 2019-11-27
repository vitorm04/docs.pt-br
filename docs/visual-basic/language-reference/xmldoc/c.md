---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348504"
---
# <a name="c-visual-basic"></a>\<c > (Visual Basic)
Indica que o texto dentro de uma descrição é o código.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---|---|  
|`text`|O texto que você deseja indicar como código.|  
  
## <a name="remarks"></a>Comentários  
 A marca `<c>` fornece uma maneira de indicar que o texto dentro de uma descrição deve ser marcado como código. Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<c>` na seção de resumo para indicar que `Counter` é o código.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
