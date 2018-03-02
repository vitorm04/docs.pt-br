---
title: "Como usar o bloco try-catch para capturar exceções"
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
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 192f762872b112ea261d22251175db6867229437
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Como usar o bloco try/catch para capturar exceções

Coloque as seções do código que podem gerar exceções em um bloco `try` e coloque o código que trata de exceções em um bloco `catch`. O bloco `catch` é uma série de instruções que começam com a palavra-chave `catch`, seguido por um tipo de exceção e uma ação a ser tomada.

O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma possível exceção. O método `Main` contém um bloco `try` com uma instrução <xref:System.IO.StreamReader> que abre um arquivo de dados chamado `data.txt` e grava uma cadeia de caracteres do arquivo. Após o bloco `try` há um bloco `catch`, que captura qualquer exceção resultante do bloco `try`.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

O Common Language Runtime captura exceções que não são capturadas por um bloco catch. Dependendo de como o tempo de execução estiver configurado, uma caixa de diálogo de depuração será exibida ou o programa interromperá a execução e será exibida uma caixa de diálogo com as informações de exceção ou, ainda, um erro será impresso para stderr.

> [!NOTE] 
> Praticamente qualquer linha de código pode causar uma exceção, especialmente exceções geradas pelo próprio Common Language Runtime, como <xref:System.OutOfMemoryException>. A maioria dos aplicativos não precisa lidar com essas exceções, mas você deve estar ciente dessa possibilidade ao gravar bibliotecas para serem usadas por outros. Para obter sugestões sobre quando definir código em um bloco Try, veja [Práticas recomendadas para exceções](best-practices-for-exceptions.md).

## <a name="see-also"></a>Consulte também  
[Exceções](index.md)
