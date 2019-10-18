---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524733"
---
# <a name="para-visual-basic"></a>> de \<para (Visual Basic)
Especifica que o conteúdo é formatado como um parágrafo.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `content`  
 O texto do parágrafo.  
  
## <a name="remarks"></a>Comentários  
 A marca de `<para>` é para uso dentro de uma marca, como [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)ou [\<returns > e](../../../visual-basic/language-reference/xmldoc/returns.md)permite que você adicione a estrutura ao texto.  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<para>` para dividir a seção de comentários do método `UpdateRecord` em dois parágrafos.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
