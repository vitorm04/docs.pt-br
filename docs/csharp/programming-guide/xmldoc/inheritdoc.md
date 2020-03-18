---
title: <inheritdoc> – Guia de Programação em C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156942"
---
# <a name="inheritdoc-c-programming-guide"></a>\<herdar> (Guia de Programação C#)

## <a name="syntax"></a>Sintaxe  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>Herdar Doc

Herde comentários XML de classes básicas, interfaces e métodos semelhantes. Isso elimina a cópia e a cola indesejadas de comentários XML duplicados e mantém automaticamente os comentários XML sincronizados.
  
## <a name="remarks"></a>Comentários  
Adicione seus comentários XML em classes básicas ou interfaces e deixe o InheritDoc copiar os comentários para implementar classes.

Adicione seus comentários XML aos seus métodos síncronos e deixe o InheritDoc copiar os comentários para suas versões assíncronas dos mesmos métodos.  

Se você quiser copiar os comentários de um `cref` membro específico, você pode usar o atributo para especificar o membro.
  
## <a name="examples"></a>Exemplos
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Tags recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
