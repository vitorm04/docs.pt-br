---
title: Como criar exceções definidas pelo usuário
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90bf9d6dbfebf8f7c1aa22e5844cf4e30b89b8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572795"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="683ae-102">Como criar exceções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="683ae-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="683ae-103">O .NET fornece uma hierarquia de classes de exceção derivada, em última análise, da classe base <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="683ae-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="683ae-104">No entanto, se nenhuma das exceções predefinidas atender às suas necessidades, será possível criar suas próprias classes de exceção derivando da classe <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="683ae-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="683ae-105">Ao criar suas próprias exceções, encerre o nome de classe de exceção definida pelo usuário com a palavra "Exception" e implemente os três construtores comuns, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="683ae-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="683ae-106">O exemplo define uma nova classe de exceção chamada `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="683ae-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="683ae-107">A classe é derivada de <xref:System.Exception> e inclui três construtores.</span><span class="sxs-lookup"><span data-stu-id="683ae-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="683ae-108">Em situações nas quais você está usando a comunicação remota, você deve garantir que os metadados para todas as exceções definidas pelo usuário estejam disponíveis no servidor (computador chamado) e para o cliente (o objeto de proxy ou chamador).</span><span class="sxs-lookup"><span data-stu-id="683ae-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="683ae-109">Para obter mais informações, consulte [Práticas recomendadas para exceções](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="683ae-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="683ae-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="683ae-110">See Also</span></span>  
[<span data-ttu-id="683ae-111">Exceções</span><span class="sxs-lookup"><span data-stu-id="683ae-111">Exceptions</span></span>](index.md)
