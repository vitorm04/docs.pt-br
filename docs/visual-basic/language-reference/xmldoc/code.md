---
title: '&lt;código&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: e66aebe35dd8f6443fefe3b07842b37270159e6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475979"
---
# <a name="ltcodegt-visual-basic"></a>&lt;código&gt; (Visual Basic)
Indica que o texto de várias linhas de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `content`  
 O texto para marcar como código.  
  
## <a name="remarks"></a>Comentários  
 Use o `<code>` marca para indicar várias linhas como código. Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o \<código > marca para incluir o código de exemplo para usar o `ID` campo.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
