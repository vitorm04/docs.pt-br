---
title: '&lt;lista&gt; (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2e879fa04eba5c01e383d53bf390f64b0cda49f7
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="ltlistgt-visual-basic"></a>&lt;lista&gt; (Visual Basic)
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
 O tipo da lista. Deve ser um "marcador" para uma lista com marcadores, "number" para uma lista numerada ou "table" para uma tabela de duas colunas.  
  
 `term`  
 Somente usado quando `type` é "table". Um termo para definir, que é definido na marca de descrição.  
  
 `description`  
 Quando `type` é "marcador" ou "número", `description` é um item na lista quando `type` é "table" `description` é a definição de `term`.  
  
## <a name="remarks"></a>Comentários  
 O `<listheader>` bloco define o título de uma tabela ou uma definição de lista. Ao definir uma tabela, você só precisa fornecer uma entrada para `term` no título.  
  
 Cada item na lista é especificado com um `<item>` bloco. Ao criar uma lista de definições, você deve especificar ambos `term` e `description`. No entanto, para uma tabela, uma lista com marcadores ou uma lista numerada, você só precisa fornecer uma entrada para `description`.  
  
 Uma lista ou tabela pode ter tantas `<item>` bloqueia conforme necessário.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<list>` tag para definir uma lista com marcadores na seção comentários.  
  
 [!code-vb[VbVbcnXmlDocComments n º&5;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
