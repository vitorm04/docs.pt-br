---
title: <code> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d4e887e3bbbc01e4cef5278f67b8c4afe273bf28
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524039"
---
# <a name="code-visual-basic"></a>> de \<code (Visual Basic)
Indica que o texto tem várias linhas de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `content`  
 O texto a ser marcado como código.  
  
## <a name="remarks"></a>Comentários  
 Use a marca `<code>` para indicar várias linhas como código. Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca de > \<code para incluir código de exemplo para usar o campo `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
