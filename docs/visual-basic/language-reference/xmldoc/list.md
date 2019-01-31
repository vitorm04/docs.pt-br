---
title: <list> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 522450e4efcecaf74968ddb492b536aa98dc0b13
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260276"
---
# <a name="list-visual-basic"></a>\<lista > (Visual Basic)
Define uma lista ou tabela.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 O tipo de lista. Deve ser "bullet" para uma lista com marcadores, "number" para uma lista numerada ou "table" para uma tabela de duas colunas.  
  
 `term`  
 Somente usado ao `type` é "table". Um termo para definir, que é definido na marca de descrição.  
  
 `description`  
 Quando `type` é "bullet" ou "number" `description` é um item na lista quando `type` é "table" `description` é a definição de `term`.  
  
## <a name="remarks"></a>Comentários  
 O `<listheader>` bloco define o título de uma tabela ou uma definição de lista. Ao definir uma tabela, você só precisará fornecer uma entrada para `term` no título.  
  
 Cada item na lista é especificado com um `<item>` bloco. Ao criar uma lista de definições, você deve especificar ambos `term` e `description`. No entanto, para uma tabela, lista com marcadores ou lista numerada, você só precisa fornecer uma entrada para `description`.  
  
 Uma lista ou tabela pode ter quantos `<item>` bloqueia conforme necessário.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<list>` marca para definir uma lista com marcadores na seção comentários.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
