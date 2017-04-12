---
title: "&lt;permissão&gt; (Visual Basic) | Documentos do Microsoft"
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
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
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
ms.openlocfilehash: 117b631aed1020465ca49e6577b5c435be0815d4
ms.lasthandoff: 03/13/2017

---
# <a name="ltpermissiongt-visual-basic"></a>&lt;permissão&gt; (Visual Basic)
Especifica uma permissão necessária para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `member`  
 Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e converte `member` para o nome canônico de elemento na saída XML. Coloque `member` entre aspas ("").  
  
 `description`  
 Uma descrição do acesso ao membro.  
  
## <a name="remarks"></a>Comentários  
 Use o `<permission>` marca para documentar o acesso de um membro. Use o <xref:System.Security.PermissionSet>classe para especificar o acesso a um membro.</xref:System.Security.PermissionSet>  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<permission>` marca para descrever o que o <xref:System.Security.Permissions.FileIOPermission>é necessária para o `ReadFile` método.</xref:System.Security.Permissions.FileIOPermission>  
  
 [!code-vb[VbVbcnXmlDocComments&#7;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
