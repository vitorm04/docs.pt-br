---
title: <value> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 1a1a4beb4a3412fe7739a69ecd0fed650b332fb2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263932"
---
# <a name="value-c-programming-guide"></a>\<value> (Guia de programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `property-description`  
 Uma descrição da propriedade.  
  
## <a name="remarks"></a>Comentários  
 A marca \<value> permite descrever o valor que uma propriedade representa. Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para a nova propriedade. Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
