---
title: "&lt;exceção&gt; (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
dev_langs:
- CSharp
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: 16
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
ms.openlocfilehash: 2ab14da86cd85eabda58aa2e1177f9f8136e3ee2
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="ltexceptiongt-c-programming-guide"></a>&lt;exceção&gt; (Guia de programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parâmetros  
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
 [!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
