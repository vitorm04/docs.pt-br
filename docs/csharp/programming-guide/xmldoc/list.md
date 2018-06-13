---
title: '&lt;list&gt; (Guia de Programação em C#)'
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 768490424403f1235873a681ffba3367e3f128b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337724"
---
# <a name="ltlistgt-c-programming-guide"></a>&lt;list&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `term`  
 Um termo a se definir, que será definido em `description`.  
  
 `description`  
 Um item em uma lista com marcadores ou numerada ou uma definição de um `term`.  
  
## <a name="remarks"></a>Comentários  
 O bloco \<listheader> é usado para definir a linha de cabeçalho de uma tabela ou lista de definição. Ao definir uma tabela, é necessário fornecer uma entrada para o termo no título.  
  
 Cada item na lista é especificado com um bloco \<item>. Ao criar uma lista de definições, é necessário especificar `term` e `description`. No entanto, para uma tabela, lista com marcadores ou lista numerada, será necessário fornecer apenas uma entrada para `description`.  
  
 Uma lista ou tabela pode ter quantos blocos \<item> forem necessários.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
