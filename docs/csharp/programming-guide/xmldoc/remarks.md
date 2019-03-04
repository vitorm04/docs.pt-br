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
ms.openlocfilehash: 3e6625c55a6f5c29fb55bff2eb87959f3237652e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975843"
---
# <a name="remarks-c-programming-guide"></a>\<remarks> (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Description`  
 Uma descrição do membro.  
  
## <a name="remarks"></a>Comentários  
 A marca \<remarks> é usada para adicionar informações sobre o tipo, complementando as informações especificadas com [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md). Essas informações são exibidas na janela do Pesquisador de Objetos.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
