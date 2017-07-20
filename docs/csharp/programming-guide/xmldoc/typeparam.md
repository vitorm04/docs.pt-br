---
title: "&lt;typeparam&gt; (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeparam
dev_langs:
- CSharp
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: 19
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
ms.openlocfilehash: af6acdc6dc8513d796210273d6437cd27b583358
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="lttypeparamgt-c-programming-guide"></a>&lt;typeparam&gt; (Guia de Programação em C#)
## <a name="syntax"></a>Sintaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").  
  
 `description`  
 Uma descrição do parâmetro de tipo.  
  
## <a name="remarks"></a>Comentários  
 A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo. Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.  
  
 Para obter mais informações, consulte [Genéricos](../../../csharp/programming-guide/generics/index.md).  
  
 O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](http://msdn.microsoft.com/en-us/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda).  
  
 Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
