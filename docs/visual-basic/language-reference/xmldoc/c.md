---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523934"
---
# <a name="c-visual-basic"></a>> de \<c (Visual Basic)
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
