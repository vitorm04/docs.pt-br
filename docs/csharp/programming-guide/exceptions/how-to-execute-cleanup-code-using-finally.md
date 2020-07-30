---
title: Como executar o código de limpeza usando o guia de programação finally-C#
description: Saiba como executar o código de limpeza usando uma instrução ' Finally '. As instruções finally garantem que qualquer limpeza necessária de objetos ocorra imediatamente.
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 148c1f9fba67659a07c667bb15619d6f3f7c3b2f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302016"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="41346-104">Como executar o código de limpeza usando finally (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="41346-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="41346-105">O propósito de uma instrução `finally` é garantir que a limpeza necessária de objetos, normalmente objetos que estão mantendo recursos externos, ocorra imediatamente, mesmo que uma exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="41346-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="41346-106">Um exemplo dessa limpeza é chamar <xref:System.IO.Stream.Close%2A> em um <xref:System.IO.FileStream> imediatamente após o uso, em vez de esperar que o objeto passe pela coleta de lixo feita pelo Common Language Runtime, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="41346-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="41346-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41346-107">Example</span></span>  
 <span data-ttu-id="41346-108">Para transformar o código anterior em uma instrução `try-catch-finally`, o código de limpeza é separado do código funcional, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="41346-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="41346-109">Como uma exceção pode ocorrer a qualquer momento no bloco `try` antes da chamada `OpenWrite()` ou a própria chamada `OpenWrite()` poderia falhar, não há garantia de que o arquivo esteja aberto ao tentarmos fechá-lo.</span><span class="sxs-lookup"><span data-stu-id="41346-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="41346-110">O bloco `finally` adiciona uma verificação para verificar se o objeto <xref:System.IO.FileStream> não é `null` antes de chamar o método <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="41346-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="41346-111">Sem a verificação de `null`, o bloco `finally` poderia lançar sua própria <xref:System.NullReferenceException>, mas o lançamento de exceções em blocos `finally` deve ser evitado, se possível.</span><span class="sxs-lookup"><span data-stu-id="41346-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="41346-112">Uma conexão de banco de dados é outra boa candidata a ser fechada em um bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="41346-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="41346-113">Como o número de conexões permitidas para um servidor de banco de dados é, às vezes, limitado, você deve fechar conexões de banco de dados assim que possível.</span><span class="sxs-lookup"><span data-stu-id="41346-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="41346-114">Se uma exceção for lançada antes de fechar a conexão, este seria outro caso em que o uso do bloco `finally` é melhor que esperar pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="41346-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41346-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="41346-115">See also</span></span>

- [<span data-ttu-id="41346-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="41346-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41346-117">Exceções e tratamento de exceções</span><span class="sxs-lookup"><span data-stu-id="41346-117">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="41346-118">Tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="41346-118">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="41346-119">Instrução using</span><span class="sxs-lookup"><span data-stu-id="41346-119">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="41346-120">try-catch</span><span class="sxs-lookup"><span data-stu-id="41346-120">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="41346-121">try-finally</span><span class="sxs-lookup"><span data-stu-id="41346-121">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="41346-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="41346-122">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
