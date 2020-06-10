---
title: Como criar exceções definidas pelo usuário
description: Saiba como criar exceções definidas pelo usuário, que são uma alternativa à hierarquia de classes de exceção derivadas da classe base de exceção no .NET.
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
ms.openlocfilehash: 14eb6246ba4347f33766f7dff36463f2bf996330
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662791"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="65d63-103">Como criar exceções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="65d63-103">How to create user-defined exceptions</span></span>

<span data-ttu-id="65d63-104">O .NET fornece uma hierarquia de classes de exceção derivada, em última análise, da classe base <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="65d63-104">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="65d63-105">No entanto, se nenhuma das exceções predefinidas atender às suas necessidades, será possível criar suas próprias classes de exceção derivando da classe <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="65d63-105">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="65d63-106">Ao criar suas próprias exceções, encerre o nome de classe de exceção definida pelo usuário com a palavra "Exception" e implemente os três construtores comuns, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="65d63-106">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="65d63-107">O exemplo define uma nova classe de exceção chamada `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="65d63-107">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="65d63-108">A classe é derivada de <xref:System.Exception> e inclui três construtores.</span><span class="sxs-lookup"><span data-stu-id="65d63-108">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="65d63-109">Em situações nas quais você está usando a comunicação remota, você deve garantir que os metadados para todas as exceções definidas pelo usuário estejam disponíveis no servidor (computador chamado) e para o cliente (o objeto de proxy ou chamador).</span><span class="sxs-lookup"><span data-stu-id="65d63-109">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="65d63-110">Para obter mais informações, consulte [Práticas recomendadas para exceções](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="65d63-110">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65d63-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="65d63-111">See also</span></span>

- [<span data-ttu-id="65d63-112">Exceções</span><span class="sxs-lookup"><span data-stu-id="65d63-112">Exceptions</span></span>](index.md)
