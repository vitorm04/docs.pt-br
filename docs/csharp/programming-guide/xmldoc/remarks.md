---
title: <remarks> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 508201fed57fce93b64691de55dce45780adc13c
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523350"
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
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
