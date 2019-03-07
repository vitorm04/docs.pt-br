---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 670064084d3297a54b2860da3fe3acab00fa3ed8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469177"
---
# <a name="returns-visual-basic"></a>\<Retorna > (Visual Basic)
Especifica o valor de retorno da propriedade ou função.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do valor retornado.  
  
## <a name="remarks"></a>Comentários  
 Use o `<returns>` marca no comentário para uma declaração de método descrever o valor de retorno.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<returns>` marca para explicar o que o `DoesRecordExist` retornos de função.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
