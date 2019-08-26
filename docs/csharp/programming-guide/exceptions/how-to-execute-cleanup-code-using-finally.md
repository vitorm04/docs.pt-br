---
title: 'Como: executar código de limpeza usando finally – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e6adbb864b0450cdd1dbfcc56abdbad2034c5c7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590253"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Como: executar código de limpeza usando finally (Guia de Programação em C#)
O propósito de uma instrução `finally` é garantir que a limpeza necessária de objetos, normalmente objetos que estão mantendo recursos externos, ocorra imediatamente, mesmo que uma exceção seja lançada. Um exemplo dessa limpeza é chamar <xref:System.IO.Stream.Close%2A> em um <xref:System.IO.FileStream> imediatamente após o uso, em vez de esperar que o objeto passe pela coleta de lixo feita pelo Common Language Runtime, da seguinte maneira:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Exemplo  
 Para transformar o código anterior em uma instrução `try-catch-finally`, o código de limpeza é separado do código funcional, da seguinte maneira.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Como uma exceção pode ocorrer a qualquer momento no bloco `try` antes da chamada `OpenWrite()` ou a própria chamada `OpenWrite()` poderia falhar, não há garantia de que o arquivo esteja aberto ao tentarmos fechá-lo. O bloco `finally` adiciona uma verificação para verificar se o objeto <xref:System.IO.FileStream> não é `null` antes de chamar o método <xref:System.IO.Stream.Close%2A>. Sem a verificação de `null`, o bloco `finally` poderia lançar sua própria <xref:System.NullReferenceException>, mas o lançamento de exceções em blocos `finally` deve ser evitado, se possível.  
  
 Uma conexão de banco de dados é outra boa candidata a ser fechada em um bloco `finally`. Como o número de conexões permitidas para um servidor de banco de dados é, às vezes, limitado, você deve fechar conexões de banco de dados assim que possível. Se uma exceção for lançada antes de fechar a conexão, este seria outro caso em que o uso do bloco `finally` é melhor que esperar pela coleta de lixo.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Exceções e manipulação de exceções](./index.md)
- [Tratamento de Exceção](./exception-handling.md)
- [Instrução using](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
