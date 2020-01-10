---
title: <remarks> – Guia de Programação em C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 2391a8ee0bb55402ff5183c837e36d04a39e6555
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711695"
---
# <a name="remarks-c-programming-guide"></a>\<remarks> (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Description`  
 Uma descrição do membro.  
  
## <a name="remarks"></a>Comentários  
 A marca \<remarks> é usada para adicionar informações sobre o tipo, complementando as informações especificadas com [\<summary>](./summary.md). Essas informações são exibidas na janela do Pesquisador de Objetos.  
  
 Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
