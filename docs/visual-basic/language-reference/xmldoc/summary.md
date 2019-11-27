---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352196"
---
# <a name="summary-visual-basic"></a>> de Resumo de \<(Visual Basic)
Especifica o resumo do membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `description`  
 Um resumo do objeto.  
  
## <a name="remarks"></a>Comentários  
 Use a marca `<summary>` para descrever um tipo ou um membro de tipo. Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) para adicionar mais informações a uma descrição de tipo.  
  
 O texto para a marca de `<summary>` é a única fonte de informações sobre o tipo no IntelliSense e também é exibido no Pesquisador de objetos. Para obter informações sobre o pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<summary>` para descrever o método `ResetCounter` e a propriedade `Counter`.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
