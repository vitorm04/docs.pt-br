---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875174"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)

Especifica a descrição de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parâmetros  

 `property-description`  
 Uma descrição da propriedade.  
  
## <a name="remarks"></a>Comentários  

 Use a `<value>` marca para descrever uma propriedade. Observe que quando você adiciona uma propriedade usando o assistente de código no ambiente de desenvolvimento do Visual Studio, ela adicionará uma [\<summary>](summary.md) marca para a nova propriedade. Em seguida, você deve adicionar manualmente uma `<value>` marca para descrever o valor que a propriedade representa.  
  
 Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  

 Este exemplo usa a `<value>` marca para descrever o valor que a `Counter` Propriedade mantém.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Marcações de Comentário XML](index.md)
