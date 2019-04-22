---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 2938d485bf6c547c792431b93fc8959c9c36befa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821407"
---
# <a name="value-visual-basic"></a>\<valor > (Visual Basic)
Especifica a descrição de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `property-description`  
 Uma descrição da propriedade.  
  
## <a name="remarks"></a>Comentários  
 Use o `<value>` marca para descrever uma propriedade. Observe que quando você adiciona uma propriedade usando o Assistente de código no ambiente de desenvolvimento do Visual Studio, ele adicionará um [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md) marca para a nova propriedade. Você deve adicionar manualmente um `<value>` marca para descrever o valor que representa a propriedade.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<value>` marca para descrever qual valor o `Counter` isenções de propriedade.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
