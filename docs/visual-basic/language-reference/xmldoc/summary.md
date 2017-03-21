---
title: '&lt;Resumo&gt; (Visual Basic) | Documentos do Microsoft'
ms.custom: 
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
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ad2053e21e58c49205fe869a484cb2dffd2169ee
ms.lasthandoff: 03/13/2017

---
# <a name="ltsummarygt-visual-basic"></a>&lt;Resumo&gt; (Visual Basic)
Especifica o resumo do membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `description`  
 Um resumo do objeto.  
  
## <a name="remarks"></a>Comentários  
 Use o `<summary>` marca para descrever um tipo ou um membro de tipo. Use [ \<comentários >](../../../visual-basic/language-reference/xmldoc/remarks.md) para adicionar informações suplementares a uma descrição de tipo.  
  
 O texto para o `<summary>` marca é a única fonte de informações sobre o tipo IntelliSense e também é exibida no Pesquisador de objetos. Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<summary>` marca para descrever o `ResetCounter` método e `Counter` propriedade.  
  
 [!code-vb[VbVbcnXmlDocComments n º&1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
