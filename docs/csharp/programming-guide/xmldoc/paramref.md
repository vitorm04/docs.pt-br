---
title: '&lt;paramref&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 0b0d49b90e097e23d3878281f9accda14b057720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325127"
---
# <a name="ltparamrefgt-c-programming-guide"></a>&lt;paramref&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro ao qual você deseja se referir. Coloque o nome entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 A marca \<paramref> fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um blogo \<summary> ou \<remarks> refere-se a um parâmetro. O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
