---
title: Manipulando e lançando exceções
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 82e314dacc9fb2657a3a7088a928b59d00282a5d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="54186-102">Tratando e gerando exceções no .NET</span><span class="sxs-lookup"><span data-stu-id="54186-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="54186-103">Aplicativos devem ser capazes de tratar de erros que ocorrem durante a execução de uma maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="54186-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="54186-104">O .NET fornece um modelo para notificar aplicativos sobre erros de maneira uniforme: operações do .NET indicam falhas por meio da geração de exceções.</span><span class="sxs-lookup"><span data-stu-id="54186-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="54186-105">Exceções</span><span class="sxs-lookup"><span data-stu-id="54186-105">Exceptions</span></span>

<span data-ttu-id="54186-106">Uma exceção é qualquer condição de erro ou comportamento inesperado encontrado por um programa em execução.</span><span class="sxs-lookup"><span data-stu-id="54186-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="54186-107">Exceções podem ser geradas devido a uma falha em seu código ou no código que você chama (como uma biblioteca compartilhada), recursos do sistema operacional não disponíveis, condições inesperadas encontradas pelo tempo de execução (como código que não pode ser verificado) e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="54186-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that cannot be verified), and so on.</span></span> <span data-ttu-id="54186-108">Seu aplicativo pode se recuperar de algumas dessas condições, mas não de outras.</span><span class="sxs-lookup"><span data-stu-id="54186-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="54186-109">Embora você possa se recuperar da maioria das exceções de aplicativo, não é possível recuperar-se da maioria das exceções de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="54186-109">Although you can recover from most application exceptions, you cannot recover from most runtime exceptions.</span></span>

<span data-ttu-id="54186-110">No .NET, uma exceção é um objeto herdado da classe <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="54186-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="54186-111">Uma exceção é lançada de uma área do código em que ocorreu um problema.</span><span class="sxs-lookup"><span data-stu-id="54186-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="54186-112">A exceção é passada pilha acima até que o aplicativo trate dela ou o programa seja encerrado.</span><span class="sxs-lookup"><span data-stu-id="54186-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="54186-113">Métodos de tratamento de exceção vs. tratamento de erro tradicional</span><span class="sxs-lookup"><span data-stu-id="54186-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="54186-114">Tradicionalmente, o modelo de tratamento de erro da linguagem confiava na forma exclusiva da linguagem de detectar erros e localizar manipuladores para eles ou no mecanismo de tratamento de erro fornecido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="54186-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="54186-115">A maneira como o .NET implementa o tratamento de exceção oferece as seguintes vantagens:</span><span class="sxs-lookup"><span data-stu-id="54186-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="54186-116">O lançamento e tratamento de exceção funciona da mesma maneira para linguagens de programação .NET.</span><span class="sxs-lookup"><span data-stu-id="54186-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="54186-117">Não requer nenhuma sintaxe de linguagem específica para tratamento de exceção, mas permite que cada linguagem defina sua própria sintaxe.</span><span class="sxs-lookup"><span data-stu-id="54186-117">Does not require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="54186-118">Exceções podem ser geradas pelos limites de processo e até mesmo de computador.</span><span class="sxs-lookup"><span data-stu-id="54186-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="54186-119">O código de tratamento de exceção pode ser adicionado a um aplicativo para aumentar a confiabilidade do programa.</span><span class="sxs-lookup"><span data-stu-id="54186-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="54186-120">As exceções oferecem vantagens sobre outros métodos de notificação de erro, como códigos de retorno.</span><span class="sxs-lookup"><span data-stu-id="54186-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="54186-121">Falhas não passam despercebidas porque se uma exceção for lançada e você não tratar dela, o tempo de execução encerra o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54186-121">Failures do not go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="54186-122">Valores inválidos não continuam a se propagar através do sistema como resultado do código que não consegue verificar se há um código de retorno de falha.</span><span class="sxs-lookup"><span data-stu-id="54186-122">Invalid values do not continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span> 

## <a name="common-exceptions"></a><span data-ttu-id="54186-123">Exceções comuns</span><span class="sxs-lookup"><span data-stu-id="54186-123">Common Exceptions</span></span>

<span data-ttu-id="54186-124">A tabela a seguir lista algumas exceções comuns com exemplos do que pode causá-las.</span><span class="sxs-lookup"><span data-stu-id="54186-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="54186-125">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="54186-125">Exception type</span></span> | <span data-ttu-id="54186-126">Tipo base</span><span class="sxs-lookup"><span data-stu-id="54186-126">Base type</span></span> | <span data-ttu-id="54186-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="54186-127">Description</span></span> | <span data-ttu-id="54186-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54186-128">Example</span></span> |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | <span data-ttu-id="54186-129">A classe base para todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="54186-129">Base class for all exceptions.</span></span> | <span data-ttu-id="54186-130">Nenhuma (use uma classe derivada dessa exceção).</span><span class="sxs-lookup"><span data-stu-id="54186-130">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="54186-131">Gerada pelo tempo de execução somente quando uma matriz é indexada incorretamente.</span><span class="sxs-lookup"><span data-stu-id="54186-131">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="54186-132">Indexar uma matriz fora do intervalo válido: `arr[arr.Length+1]`</span><span class="sxs-lookup"><span data-stu-id="54186-132">Indexing an array outside its valid range: `arr[arr.Length+1]`</span></span> |
| <xref:System.NullReferenceException> | <xref:System.Exception> | <span data-ttu-id="54186-133">Gerada pelo tempo de execução somente quando um objeto nulo é referenciado.</span><span class="sxs-lookup"><span data-stu-id="54186-133">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | <span data-ttu-id="54186-134">Gerada por métodos quando em um estado inválido.</span><span class="sxs-lookup"><span data-stu-id="54186-134">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="54186-135">Chamar `Enumerator.GetNext()` após a remoção de um item da coleção subjacente.</span><span class="sxs-lookup"><span data-stu-id="54186-135">Calling `Enumerator.GetNext()` after removing an Item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <xref:System.Exception> | <span data-ttu-id="54186-136">A classe base para todas as exceções de argumento.</span><span class="sxs-lookup"><span data-stu-id="54186-136">Base class for all argument exceptions.</span></span> | <span data-ttu-id="54186-137">Nenhuma (use uma classe derivada dessa exceção).</span><span class="sxs-lookup"><span data-stu-id="54186-137">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | <span data-ttu-id="54186-138">Gerada por métodos que não permitem que um argumento seja nulo.</span><span class="sxs-lookup"><span data-stu-id="54186-138">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="54186-139">Gerada por métodos que verificam se os argumentos estão em um determinado intervalo.</span><span class="sxs-lookup"><span data-stu-id="54186-139">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="54186-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54186-140">See Also</span></span>

* [<span data-ttu-id="54186-141">Classe e propriedades da exceção</span><span class="sxs-lookup"><span data-stu-id="54186-141">Exception Class and Properties</span></span>](exception-class-and-properties.md)
* [<span data-ttu-id="54186-142">Como usar o bloco try-catch para capturar exceções</span><span class="sxs-lookup"><span data-stu-id="54186-142">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [<span data-ttu-id="54186-143">Como usar exceções específicas em um bloco catch</span><span class="sxs-lookup"><span data-stu-id="54186-143">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
* [<span data-ttu-id="54186-144">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="54186-144">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
* [<span data-ttu-id="54186-145">Como criar exceções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="54186-145">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
* [<span data-ttu-id="54186-146">Usando manipuladores de exceção filtrados por usuário</span><span class="sxs-lookup"><span data-stu-id="54186-146">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
* [<span data-ttu-id="54186-147">Como usar blocos finally</span><span class="sxs-lookup"><span data-stu-id="54186-147">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
* [<span data-ttu-id="54186-148">Manipulando exceções de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="54186-148">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
* [<span data-ttu-id="54186-149">Práticas recomendadas para exceções</span><span class="sxs-lookup"><span data-stu-id="54186-149">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)

<span data-ttu-id="54186-150">Para saber mais sobre o funcionamento de exceções no .NET, veja [O que todo desenvolvedor precisa saber sobre exceções no tempo de execução](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="54186-150">To learn more about how exceptions work in .NET, see [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
