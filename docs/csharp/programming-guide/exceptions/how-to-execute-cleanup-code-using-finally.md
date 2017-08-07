---
title: "Como executar código de limpeza usando finally (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b1f7bccacf20a9322f4de75740cdc34b4a97fa4c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Como executar código de limpeza usando finally (Guia de Programação em C#)
O propósito de uma instrução `finally` é garantir que a limpeza necessária de objetos, normalmente objetos que estão mantendo recursos externos, ocorra imediatamente, mesmo que uma exceção seja lançada. Um exemplo dessa limpeza é chamar <xref:System.IO.Stream.Close%2A> em um <xref:System.IO.FileStream> imediatamente após o uso, em vez de esperar que o objeto passe pela coleta de lixo feita pelo Common Language Runtime, da seguinte maneira:  
  
 [!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Para transformar o código anterior em uma instrução `try-catch-finally`, o código de limpeza é separado do código funcional, da seguinte maneira.  
  
 [!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]  
  
 Como uma exceção pode ocorrer a qualquer momento no bloco `try` antes da chamada `OpenWrite()` ou a própria chamada `OpenWrite()` poderia falhar, não há garantia de que o arquivo esteja aberto ao tentarmos fechá-lo. O bloco `finally` adiciona uma verificação para verificar se o objeto <xref:System.IO.FileStream> não é `null` antes de chamar o método <xref:System.IO.Stream.Close%2A>. Sem a verificação de `null`, o bloco `finally` poderia lançar sua própria <xref:System.NullReferenceException>, mas o lançamento de exceções em blocos `finally` deve ser evitado, se possível.  
  
 Uma conexão de banco de dados é outra boa candidata a ser fechada em um bloco `finally`. Como o número de conexões permitidas para um servidor de banco de dados é, às vezes, limitado, você deve fechar conexões de banco de dados assim que possível. Se uma exceção for lançada antes de fechar a conexão, este seria outro caso em que o uso do bloco `finally` é melhor que esperar pela coleta de lixo.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Exceções e tratamento de exceções](../../../csharp/programming-guide/exceptions/index.md)   
 [Tratamento de exceções](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)

