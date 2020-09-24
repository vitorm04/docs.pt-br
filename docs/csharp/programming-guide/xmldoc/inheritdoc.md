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
ms.openlocfilehash: 8c416275254892efdb9f15cd2ae0af5634c82357
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184086"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (Guia de programação C#)

## <a name="syntax"></a>Sintaxe  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>InheritDoc

Herde comentários XML de classes base, interfaces e métodos semelhantes. Isso elimina a cópia indesejada e a colagem de comentários XML duplicados e mantém automaticamente os comentários XML sincronizados.
  
## <a name="remarks"></a>Comentários  

Adicione seus comentários XML em classes ou interfaces base e deixe que InheritDoc Copie os comentários para a implementação de classes.

Adicione seus comentários XML aos seus métodos síncronos e deixe que InheritDoc Copie os comentários para suas versões assíncronas dos mesmos métodos.  

Se você quiser copiar os comentários de um membro específico, poderá usar o `cref` atributo para especificar o membro.
  
## <a name="examples"></a>Exemplos

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Confira também

- [Guia de programação C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
