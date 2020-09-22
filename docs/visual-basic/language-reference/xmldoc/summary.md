---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 471d3ddb5cf5a234cb77de6d1d93309faf754359
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865836"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)

Especifica o resumo do membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parâmetros  

 `description`  
 Um resumo do objeto.  
  
## <a name="remarks"></a>Comentários  

 Use a `<summary>` marca para descrever um tipo ou um membro de tipo. Use [\<remarks>](remarks.md) para adicionar informações complementares a uma descrição de tipo.  
  
 O texto da `<summary>` marca é a única fonte de informações sobre o tipo no IntelliSense e também é exibido no Pesquisador de objetos. Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [-Doc](../../reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  

 Este exemplo usa a `<summary>` marca para descrever o `ResetCounter` método e a `Counter` propriedade.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Marcações de Comentário XML](index.md)
