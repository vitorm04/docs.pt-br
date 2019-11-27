---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 8f28ecc33eea99150509bb4bade047489b4b826b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352312"
---
# <a name="para-visual-basic"></a>\<para > (Visual Basic)
Especifica que o conteúdo é formatado como um parágrafo.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `content`  
 O texto do parágrafo.  
  
## <a name="remarks"></a>Comentários  
 A marca de `<para>` é para uso dentro de uma marca, como [\<> de resumo](../../../visual-basic/language-reference/xmldoc/summary.md), [\<comentários >](../../../visual-basic/language-reference/xmldoc/remarks.md)ou [\<retorna >](../../../visual-basic/language-reference/xmldoc/returns.md)e permite que você adicione estrutura ao texto.  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<para>` para dividir a seção de comentários do método `UpdateRecord` em dois parágrafos.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
