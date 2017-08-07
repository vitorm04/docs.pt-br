---
title: "Como manipular uma exceção usando try-catch (Guia de programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: 14
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f6f714cd1b652845e77405ff74fbfc860e71dc21
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Como manipular uma exceção usando try/catch (Guia de Programação em C#)
A finalidade de um bloco [try-catch](../../../csharp/language-reference/keywords/try-catch.md) é capturar e manipular uma exceção gerada pelo código de trabalho. Algumas exceções podem ser manipuladas em um bloco `catch` e o problema pode ser resolvido sem que a exceção seja gerada novamente. No entanto, com mais frequência, a única coisa que você pode fazer é certificar-se de que a exceção apropriada seja gerada.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, <xref:System.IndexOutOfRangeException> não é a exceção mais apropriada: <xref:System.ArgumentOutOfRangeException> faz mais sentido para o método porque o erro é causado pelo argumento `index` passado pelo chamador.  
  
 [!code-cs[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Comentários  
 O código que causa uma exceção fica dentro do bloco `try`. A instrução `catch` é adicionada logo após para manipular `IndexOutOfRangeException`, se ocorrer. O bloco `catch` manipula o `IndexOutOfRangeException` e gera a exceção `ArgumentOutOfRangeException`, que é mais adequada. Para fornecer ao chamador tantas informações quanto possível, considere especificar a exceção original como o <xref:System.Exception.InnerException%2A> da nova exceção. Uma vez que a propriedade <xref:System.Exception.InnerException%2A> é [readonly](../../../csharp/language-reference/keywords/readonly.md), você precisa atribuí-la no construtor da nova exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Exceções e tratamento de exceções](../../../csharp/programming-guide/exceptions/index.md)   
 [Tratamento de Exceção](../../../csharp/programming-guide/exceptions/exception-handling.md)

