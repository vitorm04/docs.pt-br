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
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a><span data-ttu-id="9bab0-102">Como usar o bloco try/catch para capturar exceções</span><span class="sxs-lookup"><span data-stu-id="9bab0-102">How to use the try/catch block to catch exceptions</span></span>

<span data-ttu-id="9bab0-103">Coloque as seções do código que podem gerar exceções em um bloco `try` e coloque o código que trata de exceções em um bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-103">Place the sections of code that might throw exceptions in a `try` block and place code that handles exceptions in a `catch` block.</span></span> <span data-ttu-id="9bab0-104">O bloco `catch` é uma série de instruções que começam com a palavra-chave `catch`, seguido por um tipo de exceção e uma ação a ser tomada.</span><span class="sxs-lookup"><span data-stu-id="9bab0-104">The `catch` block is a series of statements beginning with the keyword `catch`, followed by an exception type and an action to be taken.</span></span>

<span data-ttu-id="9bab0-105">O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma possível exceção.</span><span class="sxs-lookup"><span data-stu-id="9bab0-105">The following code example uses a `try`/`catch` block to catch a possible exception.</span></span> <span data-ttu-id="9bab0-106">O método `Main` contém um bloco `try` com uma instrução <xref:System.IO.StreamReader> que abre um arquivo de dados chamado `data.txt` e grava uma cadeia de caracteres do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9bab0-106">The `Main` method contains a `try` block with a <xref:System.IO.StreamReader> statement that opens a data file called `data.txt` and writes a string from the file.</span></span> <span data-ttu-id="9bab0-107">Após o bloco `try` há um bloco `catch`, que captura qualquer exceção resultante do bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-107">Following the `try` block is a `catch` block that catches any exception that results from the `try` block.</span></span>

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

<span data-ttu-id="9bab0-108">O Common Language Runtime captura exceções que não são capturadas por um bloco catch.</span><span class="sxs-lookup"><span data-stu-id="9bab0-108">The common language runtime catches exceptions that are not caught by a catch block.</span></span> <span data-ttu-id="9bab0-109">Dependendo de como o tempo de execução estiver configurado, uma caixa de diálogo de depuração será exibida ou o programa interromperá a execução e será exibida uma caixa de diálogo com as informações de exceção ou, ainda, um erro será impresso para stderr.</span><span class="sxs-lookup"><span data-stu-id="9bab0-109">Depending on how the runtime is configured, a debug dialog box appears, or the program stops executing and a dialog box with exception information appears, or an error is printed out to STDERR.</span></span>

> [!NOTE] 
> <span data-ttu-id="9bab0-110">Praticamente qualquer linha de código pode causar uma exceção, especialmente exceções geradas pelo próprio Common Language Runtime, como <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="9bab0-110">Almost any line of code can cause an exception, particularly exceptions that are thrown by the common language runtime itself, such as <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="9bab0-111">A maioria dos aplicativos não precisa lidar com essas exceções, mas você deve estar ciente dessa possibilidade ao gravar bibliotecas para serem usadas por outros.</span><span class="sxs-lookup"><span data-stu-id="9bab0-111">Most applications don't have to deal with these exceptions, but you should be aware of this possibility when writing libraries to be used by others.</span></span> <span data-ttu-id="9bab0-112">Para obter sugestões sobre quando definir código em um bloco Try, veja [Práticas recomendadas para exceções](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="9bab0-112">For suggestions on when to set code in a Try block, see [Best Practices for Exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bab0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bab0-113">See Also</span></span>  
[<span data-ttu-id="9bab0-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="9bab0-114">Exceptions</span></span>](index.md)
