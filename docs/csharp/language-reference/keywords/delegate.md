---
title: "delegate (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
dev_langs:
- CSharp
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
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
ms.openlocfilehash: cf100a5ad3adf001d5435ef6f67e2aa670456649
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-c-reference"></a>delegate (Referência de C#)
A declaração de um tipo de delegado é semelhante a uma assinatura de método. Ela tem um valor retornado e parâmetros de qualquer tipo:  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 Um `delegate` é um tipo de referência que pode ser usado para encapsular um método nomeado ou anônimo. Representantes são semelhantes a ponteiros de função em C++. No entanto, os representantes são fortemente tipados e seguros. Para aplicativos de representantes, consulte [Representantes](../../../csharp/programming-guide/delegates/index.md) e [Representantes genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
## <a name="remarks"></a>Comentários  
 Os representantes são a base dos [Eventos](../../../csharp/programming-guide/events/index.md).  
  
 Um delegado pode ser instanciado associando-o a um método nomeado ou anônimo. Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) e [Métodos nomeados](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
 O delegado deve ser instanciado com um método ou expressão lambda que tenha um tipo de retorno compatível e parâmetros de entrada. Para obter mais informações sobre o grau de variação permitido na assinatura do método, consulte [Variação em representantes](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca). Para uso com métodos anônimos, o delegado e o código a ser associado a ele são declarados juntos. As duas formas de instanciar representantes são discutidas nesta seção.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de Referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [Delegados com métodos nomeados vs. Métodos Anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)   
 [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
