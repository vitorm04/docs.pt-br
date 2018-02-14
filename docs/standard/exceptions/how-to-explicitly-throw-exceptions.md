---
title: "Como lançar exceções explicitamente"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="b52e9-102">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="b52e9-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="b52e9-103">Você pode gerar uma exceção explicitamente usando a instrução `throw`.</span><span class="sxs-lookup"><span data-stu-id="b52e9-103">You can explicitly throw an exception using the `throw` statement.</span></span> <span data-ttu-id="b52e9-104">Você também pode lançar novamente uma exceção capturada usando a instrução `throw`.</span><span class="sxs-lookup"><span data-stu-id="b52e9-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="b52e9-105">É uma boa prática adicionar informações a uma exceção que é lançada novamente para fornecer mais informações durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="b52e9-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="b52e9-106">O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma possível <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="b52e9-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="b52e9-107">Após o bloco `try`, há um bloco `catch` que captura a <xref:System.IO.FileNotFoundException> e grava uma mensagem no console se o arquivo de dados não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="b52e9-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="b52e9-108">A próxima instrução é a instrução `throw`, que gera uma nova <xref:System.IO.FileNotFoundException> e adiciona informações de texto à exceção.</span><span class="sxs-lookup"><span data-stu-id="b52e9-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="b52e9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b52e9-109">See Also</span></span>  
[<span data-ttu-id="b52e9-110">Exceções</span><span class="sxs-lookup"><span data-stu-id="b52e9-110">Exceptions</span></span>](index.md)
