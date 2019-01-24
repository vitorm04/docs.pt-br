---
title: '&lt;Retorna&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 4dcf8e9aee6edecbda2874a6e07fbe6e3772b18b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580519"
---
# <a name="ltreturnsgt-visual-basic"></a>&lt;Retorna&gt; (Visual Basic)
Especifica o valor de retorno da propriedade ou função.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Uma descrição do valor retornado.  
  
## <a name="remarks"></a>Comentários  
 Use o `<returns>` marca no comentário para uma declaração de método descrever o valor de retorno.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<returns>` marca para explicar o que o `DoesRecordExist` retornos de função.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
