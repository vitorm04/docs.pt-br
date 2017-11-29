---
title: Como usar blocos finally
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b303582a62f211091b1ebee0e88cf380da8b03d9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-finally-blocks"></a>Como usar blocos finally

Quando ocorre uma exceção, a execução é interrompida e o controle é dado ao manipulador de exceção apropriado. Geralmente, isso significa que linhas de código que você espera que sejam executadas são ignoradas. A limpeza de alguns recursos, assim como o fechamento de um arquivo, precisará ser feita mesmo se uma exceção for gerada. Para fazer isso, você pode usar um bloco `finally`. Um bloco `finally` sempre é executado, independentemente de uma exceção ser ou não gerada.

O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma <xref:System.ArgumentOutOfRangeException>. O método `Main` cria duas matrizes e tenta copiar uma para a outra. A ação gera um <xref:System.ArgumentOutOfRangeException> e o erro é gravado no console. Este bloco `finally` é executado independentemente resultado da ação de cópia.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Consulte também  
[Exceções](index.md)   
