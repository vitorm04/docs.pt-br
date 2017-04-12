---
title: "&lt;Consulte também&gt; (Visual Basic) | Documentos do Microsoft"
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
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: 10
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
ms.openlocfilehash: 837cbcaaa4fc35824c69dadf5a19aa3bbdef9c2f
ms.lasthandoff: 03/13/2017

---
# <a name="ltseealsogt-visual-basic"></a>&lt;Consulte também&gt; (Visual Basic)
Especifica um link que aparece na seção Consulte também.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento na saída XML. `member`deve aparecer entre aspas duplas ("").  
  
## <a name="remarks"></a>Comentários  
 Use o `<seealso>` marca para especificar o texto que você deseja que apareça em uma seção Consulte também. Use [ \<consulte >](../../../visual-basic/language-reference/xmldoc/see.md) para especificar um link de dentro do texto.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<seealso>` marca no `DoesRecordExist` seção para se referir a comentários a `UpdateRecord` método.  
  
 [!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
