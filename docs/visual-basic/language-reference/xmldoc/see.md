---
title: '&lt;consulte&gt; (Visual Basic) | Documentos do Microsoft'
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
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: 10
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
ms.openlocfilehash: cc8980875a8e956f884cf7f71c48f1b9eb359dff
ms.lasthandoff: 03/13/2017

---
# <a name="ltseegt-visual-basic"></a>&lt;consulte&gt; (Visual Basic)
Especifica um link para outro membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento na saída XML. `member`deve aparecer entre aspas duplas ("").  
  
## <a name="remarks"></a>Comentários  
 Use o `<see>` marca para especificar um link de dentro do texto. Use [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar o texto que você pode aparecer em uma seção "Consulte também".  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<see>` marca no `UpdateRecord` seção para se referir a comentários a `DoesRecordExist` método.  
  
 [!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
