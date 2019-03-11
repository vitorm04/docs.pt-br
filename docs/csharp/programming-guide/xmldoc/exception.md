---
title: <exception> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 4036b53674eb680c2df3136e8dd6d8165514dbb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487681"
---
# <a name="exception-c-programming-guide"></a>\<exception> (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parâmetros  
 cref = " `member`"  
 Uma referência a uma exceção que está disponível no ambiente de compilação atual. O compilador verifica se a exceção apresentada existe e move o `member` para o nome de elemento canônico no XML de saída. `member` deve ser exibido entre aspas duplas (" ").  
  
 Para obter mais informações sobre como criar uma referência cref para um tipo genérico, consulte [\<see>](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Uma descrição da exceção.  
  
## <a name="remarks"></a>Comentários  
 A marca \<exception> permite que você especifique quais exceções podem ser lançadas. Essa marca pode ser aplicada às definições de métodos, propriedades, eventos e indexadores.  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
 Para obter mais informações sobre o tratamento de exceção, consulte [Exceções e tratamento de exceção](../../../csharp/programming-guide/exceptions/index.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
