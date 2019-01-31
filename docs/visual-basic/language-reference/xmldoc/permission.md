---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: a8914e6d8fbce3e99ff92d9e4968e85a0f0ad7d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263635"
---
# <a name="permission-visual-basic"></a>\<permissão > (Visual Basic)
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
 Este exemplo usa o `<permission>` marca para descrever o que o <xref:System.Security.Permissions.FileIOPermission> é necessária para o `ReadFile` método.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
