---
title: '&lt;para&gt; (Visual Basic) | Documentos do Microsoft'
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
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: 9
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 98ffc0635c3fcd97b5e5aa3ed6b573d15f7e79ef
ms.lasthandoff: 03/13/2017

---
# <a name="ltparagt-visual-basic"></a>&lt;para&gt; (Visual Basic)
Especifica que o conteúdo é formatado como um parágrafo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<para>content</para>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `content`  
 O texto do parágrafo.  
  
## <a name="remarks"></a>Comentários  
 O `<para>` marca é para uso dentro de uma marca, como [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<comentários >](../../../visual-basic/language-reference/xmldoc/remarks.md), ou [ \<retorna >](../../../visual-basic/language-reference/xmldoc/returns.md)e permite que você adicione estrutura ao texto.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<para>` marca para dividir a seção comentários para o `UpdateRecord` método em dois parágrafos.  
  
 [!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
