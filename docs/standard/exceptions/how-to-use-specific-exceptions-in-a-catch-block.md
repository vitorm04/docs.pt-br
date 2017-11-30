---
title: "Como usar exceções específicas em um bloco catch"
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
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="105e0-102">Como usar exceções específicas em um bloco catch</span><span class="sxs-lookup"><span data-stu-id="105e0-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="105e0-103">Em geral, é uma boa prática para capturar um tipo específico de exceção em vez de usar básico de programação `catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="105e0-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="105e0-104">Quando ocorre uma exceção, ela é passada para cima na pilha e, a cada bloco catch, é dada a oportunidade de tratá-la.</span><span class="sxs-lookup"><span data-stu-id="105e0-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="105e0-105">A ordem das instruções catch é importante.</span><span class="sxs-lookup"><span data-stu-id="105e0-105">The order of catch statements is important.</span></span> <span data-ttu-id="105e0-106">Coloque blocos catch direcionados para exceções específicas antes que um bloco catch de exceção geral ou o compilador possa emitir um erro.</span><span class="sxs-lookup"><span data-stu-id="105e0-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="105e0-107">O bloco catch adequado é determinado ao fazer a correspondência entre o tipo da exceção e o nome da exceção especificada no bloco catch.</span><span class="sxs-lookup"><span data-stu-id="105e0-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="105e0-108">Se não houver nenhum bloco catch específico, a exceção será detectada por um bloco catch geral, se houver.</span><span class="sxs-lookup"><span data-stu-id="105e0-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="105e0-109">O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="105e0-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="105e0-110">O exemplo cria uma classe chamada `Employee` com uma única propriedade, nível do funcionário (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="105e0-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="105e0-111">Um método, `PromoteEmployee`, utiliza um objeto e incrementa o nível do funcionário.</span><span class="sxs-lookup"><span data-stu-id="105e0-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="105e0-112">Um <xref:System.InvalidCastException> ocorre quando uma instância <xref:System.DateTime> é passada para o método `PromoteEmployee`.</span><span class="sxs-lookup"><span data-stu-id="105e0-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="105e0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="105e0-113">See Also</span></span>  
[<span data-ttu-id="105e0-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="105e0-114">Exceptions</span></span>](index.md)
