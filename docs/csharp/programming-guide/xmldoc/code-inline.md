---
title: "&lt;c&gt; (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- c
- <c>
dev_langs:
- CSharp
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f081851590fcc376eb3fbbe63dc7b1aa128a8db9
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

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
 [!code-cs[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
