---
title: '&lt;permissão&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 4fafebf94be350951672f01f2d17bd00d4bab69a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601989"
---
# <a name="ltpermissiongt-visual-basic"></a>&lt;permissão&gt; (Visual Basic)
Especifica uma permissão necessária para o membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `member`  
 Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída. Coloque `member` entre aspas ("").  
  
 `description`  
 Uma descrição do acesso ao membro.  
  
## <a name="remarks"></a>Comentários  
 Use o `<permission>` marca para documentar o acesso de um membro. Use o <xref:System.Security.PermissionSet> classe para especificar o acesso a um membro.  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<permission>` marcas para descrever que o <xref:System.Security.Permissions.FileIOPermission> é necessária para o `ReadFile` método.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
