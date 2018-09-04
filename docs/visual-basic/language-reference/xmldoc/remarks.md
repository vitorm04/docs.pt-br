---
title: '&lt;comentários&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 97fca8758d9c21ac0b8f15bf9d5831750fbabe77
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557070"
---
# <a name="ltremarksgt-visual-basic"></a>&lt;comentários&gt; (Visual Basic)
Especifica uma seção de comentários para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do membro.  
  
## <a name="remarks"></a>Comentários  
 Use o `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).  
  
 Essas informações são exibidas no Pesquisador de objetos. Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<remarks>` marca para explicar o que o `UpdateRecord` que o método.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
