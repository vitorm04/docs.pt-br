---
title: '&lt;valor&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602452"
---
# <a name="ltvaluegt-visual-basic"></a>&lt;valor&gt; (Visual Basic)
Especifica a descrição de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `property-description`  
 Uma descrição da propriedade.  
  
## <a name="remarks"></a>Comentários  
 Use o `<value>` marcas para descrever uma propriedade. Observe que quando você adiciona uma propriedade usando o Assistente de código no ambiente de desenvolvimento do Visual Studio, ele adicionará um [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade. Você deve adicionar manualmente um `<value>` marcas para descrever o valor que representa a propriedade.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<value>` marcas para descrever qual valor o `Counter` isenções de propriedade.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
