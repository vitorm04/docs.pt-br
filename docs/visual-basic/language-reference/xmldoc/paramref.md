---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 1ef8d76699534a7408912424bcdea651d8314364
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283979"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
Formata uma palavra como um parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro ao qual você deseja se referir. Coloque o nome entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 O `<paramref>` marca oferece uma maneira para indicar que uma palavra é um parâmetro. O arquivo XML pode ser processado para formatar esse parâmetro de alguma forma distinta.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<paramref>` marca para referir-se a `id` parâmetro.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
