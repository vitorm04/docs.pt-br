---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: fa11c713a5ed5793b50865753f8bcdeaabf56e83
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999301"
---
# <a name="ltparagt-visual-basic"></a>&lt;para&gt; (Visual Basic)
Especifica que o conteúdo é formatado como um parágrafo.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `content`  
 O texto do parágrafo.  
  
## <a name="remarks"></a>Comentários  
 O `<para>` marca é para uso dentro de uma marca, como [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), ou [ \<retorna >](../../../visual-basic/language-reference/xmldoc/returns.md), e permite que você adicione estrutura ao texto.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<para>` marca para dividir a seção comentários para o `UpdateRecord` método em dois parágrafos.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
