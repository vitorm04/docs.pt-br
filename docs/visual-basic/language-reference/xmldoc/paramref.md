---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598656"
---
# <a name="ltparamrefgt-visual-basic"></a>&lt;paramref&gt; (Visual Basic)
Formata uma palavra como um parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro ao qual você deseja se referir. Coloque o nome entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 O `<paramref>` marca fornece uma maneira para indicar que uma palavra é um parâmetro. O arquivo XML pode ser processado para formatar esse parâmetro em alguma forma distinta.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<paramref>` marca para referir-se a `id` parâmetro.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
