---
title: <permission> – Guia de Programação em C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 67e9d398d1bb43d480f8ca56733106e0f0a22731
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696565"
---
# <a name="permission-c-programming-guide"></a>\<permission> (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parâmetros  
 cref = " `member`"  
 Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e converte `member` no nome de elemento canônico no XML de saída. *member* deve ser exibido entre aspas duplas (" ").  
  
 Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [\<consulte>](./see.md).  
  
 `description`  
 Uma descrição do acesso ao membro.  
  
## <a name="remarks"></a>Comentários  
 A marca \<permissão > permite documentar o acesso de um membro. A classe <xref:System.Security.PermissionSet> permite que você especifique o acesso a um membro.  
  
 Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
