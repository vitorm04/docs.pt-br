---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 5aab2307a1967ea660282c7b324eaddfe798a155
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857873"
---
# <a name="value-visual-basic"></a>\<valor > (Visual Basic)
Especifica a descrição de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `property-description`  
 Uma descrição da propriedade.  
  
## <a name="remarks"></a>Comentários  
 Use o `<value>` marca para descrever uma propriedade. Observe que quando você adiciona uma propriedade usando o Assistente de código no ambiente de desenvolvimento do Visual Studio, ele adicionará um [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade. Você deve adicionar manualmente um `<value>` marca para descrever o valor que representa a propriedade.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<value>` marca para descrever qual valor o `Counter` isenções de propriedade.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
