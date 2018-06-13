---
title: '&lt;c&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 623412bae7d2bf58e53dd8290108773d157dd747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329229"
---
# <a name="ltcgt-c-programming-guide"></a>&lt;c&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `text`  
 O texto que você deseja indicar como código.  
  
## <a name="remarks"></a>Comentários  
 A marca \<c> oferece uma maneira de indicar que o texto em uma descrição deve ser marcado como código. Use [\<code>](../../../csharp/programming-guide/xmldoc/code.md) para indicar várias linhas como código.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
