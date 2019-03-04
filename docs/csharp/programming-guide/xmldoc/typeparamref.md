---
title: <typeparamref> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 0ee9e3571ab601f56ddee2fd9a02bb19f50bac62
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967354"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre parâmetros de tipo em tipos e métodos genéricos, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).  
  
 Use essa marca para habilitar os consumidores do arquivo de documentação a formatar a palavra de alguma forma distinta, por exemplo, em itálico.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
