---
title: Tratando e gerando exceções no .NET
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263e6394a57ec3e7ef00eb79671d9b8ac47e724f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "43883775"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="fca5b-102">Tratando e gerando exceções no .NET</span><span class="sxs-lookup"><span data-stu-id="fca5b-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="fca5b-103">Aplicativos devem ser capazes de tratar de erros que ocorrem durante a execução de uma maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="fca5b-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="fca5b-104">O .NET fornece um modelo para notificar aplicativos sobre erros de maneira uniforme: operações do .NET indicam falhas por meio da geração de exceções.</span><span class="sxs-lookup"><span data-stu-id="fca5b-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="fca5b-105">Exceções</span><span class="sxs-lookup"><span data-stu-id="fca5b-105">Exceptions</span></span>

<span data-ttu-id="fca5b-106">Uma exceção é qualquer condição de erro ou comportamento inesperado encontrado por um programa em execução.</span><span class="sxs-lookup"><span data-stu-id="fca5b-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="fca5b-107">Exceções podem ser geradas devido a uma falha em seu código ou no código que você chama (como uma biblioteca compartilhada), recursos do sistema operacional não disponíveis, condições inesperadas encontradas pelo tempo de execução (como código que não pode ser verificado) e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="fca5b-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="fca5b-108">Seu aplicativo pode se recuperar de algumas dessas condições, mas não de outras.</span><span class="sxs-lookup"><span data-stu-id="fca5b-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="fca5b-109">Embora você possa se recuperar da maioria das exceções de aplicativo, não é possível recuperar-se da maioria das exceções de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fca5b-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="fca5b-110">No .NET, uma exceção é um objeto herdado da classe <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fca5b-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fca5b-111">Uma exceção é lançada de uma área do código em que ocorreu um problema.</span><span class="sxs-lookup"><span data-stu-id="fca5b-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="fca5b-112">A exceção é passada pilha acima até que o aplicativo trate dela ou o programa seja encerrado.</span><span class="sxs-lookup"><span data-stu-id="fca5b-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="fca5b-113">Métodos de tratamento de exceção vs. tratamento de erro tradicional</span><span class="sxs-lookup"><span data-stu-id="fca5b-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="fca5b-114">Tradicionalmente, o modelo de tratamento de erro da linguagem confiava na forma exclusiva da linguagem de detectar erros e localizar manipuladores para eles ou no mecanismo de tratamento de erro fornecido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fca5b-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="fca5b-115">A maneira como o .NET implementa o tratamento de exceção oferece as seguintes vantagens:</span><span class="sxs-lookup"><span data-stu-id="fca5b-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="fca5b-116">O lançamento e tratamento de exceção funciona da mesma maneira para linguagens de programação .NET.</span><span class="sxs-lookup"><span data-stu-id="fca5b-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="fca5b-117">Não requer nenhuma sintaxe de linguagem específica para tratamento de exceção, mas permite que cada linguagem defina sua própria sintaxe.</span><span class="sxs-lookup"><span data-stu-id="fca5b-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="fca5b-118">Exceções podem ser geradas pelos limites de processo e até mesmo de computador.</span><span class="sxs-lookup"><span data-stu-id="fca5b-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="fca5b-119">O código de tratamento de exceção pode ser adicionado a um aplicativo para aumentar a confiabilidade do programa.</span><span class="sxs-lookup"><span data-stu-id="fca5b-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="fca5b-120">As exceções oferecem vantagens sobre outros métodos de notificação de erro, como códigos de retorno.</span><span class="sxs-lookup"><span data-stu-id="fca5b-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="fca5b-121">Falhas não passam despercebidas porque se uma exceção for lançada e você não tratar dela, o tempo de execução encerra o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fca5b-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="fca5b-122">Valores inválidos não continuam a se propagar através do sistema como resultado do código que não consegue verificar se há um código de retorno de falha.</span><span class="sxs-lookup"><span data-stu-id="fca5b-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="fca5b-123">Exceções comuns</span><span class="sxs-lookup"><span data-stu-id="fca5b-123">Common exceptions</span></span>

<span data-ttu-id="fca5b-124">A tabela a seguir lista algumas exceções comuns com exemplos do que pode causá-las.</span><span class="sxs-lookup"><span data-stu-id="fca5b-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="fca5b-125">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="fca5b-125">Exception type</span></span> | <span data-ttu-id="fca5b-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="fca5b-126">Description</span></span> | <span data-ttu-id="fca5b-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fca5b-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="fca5b-128">A classe base para todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="fca5b-128">Base class for all exceptions.</span></span> | <span data-ttu-id="fca5b-129">Nenhuma (use uma classe derivada dessa exceção).</span><span class="sxs-lookup"><span data-stu-id="fca5b-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="fca5b-130">Gerada pelo tempo de execução somente quando uma matriz é indexada incorretamente.</span><span class="sxs-lookup"><span data-stu-id="fca5b-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="fca5b-131">Indexar uma matriz fora do intervalo válido:</span><span class="sxs-lookup"><span data-stu-id="fca5b-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="fca5b-132">Gerada pelo tempo de execução somente quando um objeto nulo é referenciado.</span><span class="sxs-lookup"><span data-stu-id="fca5b-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="fca5b-133">Gerada por métodos quando em um estado inválido.</span><span class="sxs-lookup"><span data-stu-id="fca5b-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="fca5b-134">Chamar `Enumerator.MoveNext()` após a remoção de um item da coleção subjacente.</span><span class="sxs-lookup"><span data-stu-id="fca5b-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="fca5b-135">A classe base para todas as exceções de argumento.</span><span class="sxs-lookup"><span data-stu-id="fca5b-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="fca5b-136">Nenhuma (use uma classe derivada dessa exceção).</span><span class="sxs-lookup"><span data-stu-id="fca5b-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="fca5b-137">Gerada por métodos que não permitem que um argumento seja nulo.</span><span class="sxs-lookup"><span data-stu-id="fca5b-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="fca5b-138">Gerada por métodos que verificam se os argumentos estão em um determinado intervalo.</span><span class="sxs-lookup"><span data-stu-id="fca5b-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="fca5b-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fca5b-139">See also</span></span>

- [<span data-ttu-id="fca5b-140">Classe e propriedades da exceção</span><span class="sxs-lookup"><span data-stu-id="fca5b-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)  
- [<span data-ttu-id="fca5b-141">Como usar o bloco try-catch para capturar exceções</span><span class="sxs-lookup"><span data-stu-id="fca5b-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
- [<span data-ttu-id="fca5b-142">Como usar exceções específicas em um bloco catch</span><span class="sxs-lookup"><span data-stu-id="fca5b-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)  
- [<span data-ttu-id="fca5b-143">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="fca5b-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)  
- [<span data-ttu-id="fca5b-144">Como criar exceções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="fca5b-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)  
- [<span data-ttu-id="fca5b-145">Usando manipuladores de exceção filtrados por usuário</span><span class="sxs-lookup"><span data-stu-id="fca5b-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)  
- [<span data-ttu-id="fca5b-146">Como usar blocos finally</span><span class="sxs-lookup"><span data-stu-id="fca5b-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)  
- [<span data-ttu-id="fca5b-147">Manipulando exceções de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="fca5b-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)  
- [<span data-ttu-id="fca5b-148">Práticas recomendadas para exceções</span><span class="sxs-lookup"><span data-stu-id="fca5b-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)  
- <span data-ttu-id="fca5b-149">[O que todo desenvolvedor precisa saber sobre exceções no tempo de execução](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="fca5b-149">[What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
