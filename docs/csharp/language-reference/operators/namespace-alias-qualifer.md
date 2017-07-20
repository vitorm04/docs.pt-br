---
title: "Operador :: (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 21
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
ms.openlocfilehash: 12a0265d430a5a110d8c73107a48b36e0ab15405
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>Operador :: (Referência de C#)
O qualificador alias de namespace (`::`) é usado para pesquisar identificadores. Ele sempre está posicionado entre dois identificadores, como neste exemplo:  
  
 [!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a>Comentários  
 O qualificador alias de namespace pode ser `global`. Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.  
  
## <a name="for-more-information"></a>Para obter mais informações  
 Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:  
  
-   [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. Operador](../../../csharp/language-reference/operators/member-access-operator.md)   
 [Alias extern](../../../csharp/language-reference/keywords/extern-alias.md)
