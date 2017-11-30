---
title: "Práticas recomendadas para exceções"
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
helpviewer_keywords: exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87f9287c3714416ee5d6b63f3c9db311bb97b131
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2017
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="aa845-102">Práticas recomendadas para exceções</span><span class="sxs-lookup"><span data-stu-id="aa845-102">Best practices for exceptions</span></span>

<span data-ttu-id="aa845-103">Um aplicativo bem projetado sabe tratar erros e exceções para evitar falhas.</span><span class="sxs-lookup"><span data-stu-id="aa845-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="aa845-104">Esta seção descreve as práticas recomendadas para tratar e criar exceções.</span><span class="sxs-lookup"><span data-stu-id="aa845-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks"></a><span data-ttu-id="aa845-105">Usar blocos try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="aa845-105">Use try/catch/finally blocks</span></span>

<span data-ttu-id="aa845-106">Use blocos `try`/`catch`/`finally` em torno de código que potencialmente possa gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-106">Use `try`/`catch`/`finally` blocks around code that can potentially generate an exception.</span></span> 

<span data-ttu-id="aa845-107">Sempre ordene exceções em blocos `catch` da mais específica para a menos específica.</span><span class="sxs-lookup"><span data-stu-id="aa845-107">In `catch` blocks, always order exceptions from the most specific to the least specific.</span></span>

<span data-ttu-id="aa845-108">Use um bloco `finally` para limpar os recursos, independentemente de você poder recuperá-los ou não.</span><span class="sxs-lookup"><span data-stu-id="aa845-108">Use a `finally` block to clean up resources, whether you can recover or not.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="aa845-109">Tratar de condições comuns sem gerar exceções</span><span class="sxs-lookup"><span data-stu-id="aa845-109">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="aa845-110">Para condições que têm boa probabilidade de ocorrer mas que podem disparar uma exceção, considere tratá-las de uma maneira que evite essa exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-110">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="aa845-111">Por exemplo, se você tentar fechar uma conexão que já está fechada, você obterá um `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="aa845-111">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="aa845-112">Você pode evitar isso usando uma instrução `if` para verificar o estado da conexão antes de tentar fechá-la.</span><span class="sxs-lookup"><span data-stu-id="aa845-112">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="aa845-113">Se você não verificar estado da conexão antes de fechar, você poderá capturar a exceção `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="aa845-113">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="aa845-114">O método a escolher depende da frequência com que você espera que o evento ocorra.</span><span class="sxs-lookup"><span data-stu-id="aa845-114">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="aa845-115">Use o tratamento de exceções se o evento não ocorrer muito frequentemente, ou seja, se o evento é realmente excepcional e indica um erro (como um fim de arquivo inesperado).</span><span class="sxs-lookup"><span data-stu-id="aa845-115">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="aa845-116">Quando você usa o tratamento de exceções, menos código é executado em condições normais.</span><span class="sxs-lookup"><span data-stu-id="aa845-116">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="aa845-117">Verifique a existência de condições de erro no código se o evento ocorrer rotineiramente e puder ser considerado parte da execução normal.</span><span class="sxs-lookup"><span data-stu-id="aa845-117">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="aa845-118">Quando você verifica se há condições de erro comuns, menos código é executado porque você evita exceções.</span><span class="sxs-lookup"><span data-stu-id="aa845-118">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="aa845-119">Projetar classes de modo que as exceções possam ser evitadas</span><span class="sxs-lookup"><span data-stu-id="aa845-119">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="aa845-120">Uma classe pode fornecer métodos ou propriedades que permitem que você evite fazer uma chamada que dispararia uma exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-120">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="aa845-121">Por exemplo, uma classe <xref:System.IO.FileStream> fornece métodos que ajudam a determinar se ao final do arquivo foi atingido.</span><span class="sxs-lookup"><span data-stu-id="aa845-121">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="aa845-122">Elas podem ser usadas para evitar exceções geradas quando você faz a leitura após o fim do arquivo.</span><span class="sxs-lookup"><span data-stu-id="aa845-122">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="aa845-123">O exemplo a seguir mostra como ler até o final de um arquivo sem disparar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-123">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="aa845-124">Outra maneira de evitar exceções é retornar nulo para casos muito comuns de erro, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-124">Another way to avoid exceptions is to return null for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="aa845-125">Um caso extremamente comum de erro pode ser considerado um fluxo normal de controle.</span><span class="sxs-lookup"><span data-stu-id="aa845-125">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="aa845-126">Ao retornar nulo nesses casos, você minimiza o impacto no desempenho de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa845-126">By returning null in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="aa845-127">Gerar exceções em vez de retornar um código de erro</span><span class="sxs-lookup"><span data-stu-id="aa845-127">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="aa845-128">Exceções asseguram que falhas não passem despercebidas porque o código de chamada não verificou um código de retorno.</span><span class="sxs-lookup"><span data-stu-id="aa845-128">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span> 

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="aa845-129">Usar os tipos de exceção do .NET predefinidos</span><span class="sxs-lookup"><span data-stu-id="aa845-129">Use the predefined .NET exception types</span></span>

<span data-ttu-id="aa845-130">Apresente uma nova classe de exceção apenas quando a predefinida não se aplicar.</span><span class="sxs-lookup"><span data-stu-id="aa845-130">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="aa845-131">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aa845-131">For example:</span></span>

- <span data-ttu-id="aa845-132">Gere uma exceção <xref:System.InvalidOperationException> se uma propriedade de definição ou chamada de método não for adequada para o estado atual do objeto.</span><span class="sxs-lookup"><span data-stu-id="aa845-132">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="aa845-133">Gere uma exceção <xref:System.ArgumentException> ou uma das classes predefinidas que derivam de <xref:System.ArgumentException> se parâmetros inválidos forem passados.</span><span class="sxs-lookup"><span data-stu-id="aa845-133">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="aa845-134">Terminar os nomes das classes de exceção com a palavra `Exception`</span><span class="sxs-lookup"><span data-stu-id="aa845-134">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="aa845-135">Quando uma exceção personalizada for necessária, nomeie-a adequadamente e derive-a da classe <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="aa845-135">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="aa845-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aa845-136">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="aa845-137">Incluir três construtores em classes de exceção personalizada</span><span class="sxs-lookup"><span data-stu-id="aa845-137">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="aa845-138">Use pelo menos três os construtores comuns ao criar suas próprias classes de exceção: o construtor padrão, um construtor que recebe uma mensagem de cadeia de caracteres e uma exceção interna.</span><span class="sxs-lookup"><span data-stu-id="aa845-138">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="aa845-139"><xref:System.Exception.%23ctor>, que usa valores padrão.</span><span class="sxs-lookup"><span data-stu-id="aa845-139"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="aa845-140"><xref:System.Exception.%23ctor%28System.String%29>, que aceita uma mensagem de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="aa845-140"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="aa845-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, que aceita uma mensagem de cadeia de caracteres e a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="aa845-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="aa845-142">Para ver um exemplo, veja [Como criar exceções definidas pelo usuário](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="aa845-142">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="aa845-143">Certifique-se de que os dados de exceção estão disponíveis quando o código é executado remotamente</span><span class="sxs-lookup"><span data-stu-id="aa845-143">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="aa845-144">Ao criar exceções definidas pelo usuário, assegure que os metadados para as exceções estejam disponíveis para códigos executando remotamente.</span><span class="sxs-lookup"><span data-stu-id="aa845-144">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="aa845-145">Por exemplo, em implementações de .NET que dão suporte a domínios de aplicativos, exceções podem ocorrer em domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="aa845-145">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="aa845-146">Suponha que o Domínio de Aplicativo A crie o Domínio de aplicativo B, o qual executa o código que gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-146">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="aa845-147">Para que o Domínio de Aplicativo A capture e trate corretamente a exceção, ele deverá ser capaz de localizar o assembly que contém a exceção gerada pelo Domínio de Aplicativo B. Se o Domínio de Aplicativo B gerar uma exceção contida em um assembly em sua base de aplicativo, mas não na base de aplicativo do Domínio de Aplicativo A, o Domínio de Aplicativo A não será capaz de localizar a exceção e o Common Language Runtime gerará uma exceção <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="aa845-147">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="aa845-148">Para evitar essa situação, você pode implantar o assembly que contém as informações de exceção de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="aa845-148">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="aa845-149">Coloque o assembly em uma base de aplicativos comum compartilhada por ambos os domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="aa845-149">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="aa845-150">\- ou -</span><span class="sxs-lookup"><span data-stu-id="aa845-150">\- or -</span></span>

- <span data-ttu-id="aa845-151">Se os domínios não compartilham uma base de aplicativos comum, assine o assembly que contém as informações de exceção com um nome forte e implante o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="aa845-151">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="include-a-localized-description-string-in-every-exception"></a><span data-ttu-id="aa845-152">Incluir uma cadeia de caracteres de descrição localizada em cada exceção</span><span class="sxs-lookup"><span data-stu-id="aa845-152">Include a localized description string in every exception</span></span>

<span data-ttu-id="aa845-153">A mensagem de erro que o usuário recebe é derivada da cadeia de caracteres de descrição da exceção que foi gerada, em vez do nome da classe de exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-153">The error message that the user sees is derived from the description string of the exception that was thrown, and not from the name of the exception class.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="aa845-154">Usar mensagens de erro gramaticalmente corretas</span><span class="sxs-lookup"><span data-stu-id="aa845-154">Use grammatically correct error messages</span></span>

<span data-ttu-id="aa845-155">Escreva frases claras e inclua pontuação final.</span><span class="sxs-lookup"><span data-stu-id="aa845-155">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="aa845-156">Cada sentença em uma cadeia de caracteres descrição de uma exceção deve terminar com um ponto final.</span><span class="sxs-lookup"><span data-stu-id="aa845-156">Each sentence in a description string of an exception should end in a period.</span></span> <span data-ttu-id="aa845-157">Por exemplo, "a tabela de log estourou."</span><span class="sxs-lookup"><span data-stu-id="aa845-157">For example, "The log table has overflowed."</span></span> <span data-ttu-id="aa845-158">seria uma cadeia de caracteres de descrição apropriada.</span><span class="sxs-lookup"><span data-stu-id="aa845-158">would be an appropriate description string.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="aa845-159">Em exceções personalizadas, forneça propriedades adicionais conforme necessário</span><span class="sxs-lookup"><span data-stu-id="aa845-159">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="aa845-160">Forneça propriedades adicionais para uma exceção (além da cadeia de caracteres de descrição) somente quando houver um cenário programático no qual as informações adicionais serão úteis.</span><span class="sxs-lookup"><span data-stu-id="aa845-160">Provide additional properties for an exception (in addition to the description string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="aa845-161">Por exemplo, o <xref:System.IO.FileNotFoundException> fornece a propriedade <xref:System.IO.FileNotFoundException.FileName>.</span><span class="sxs-lookup"><span data-stu-id="aa845-161">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="aa845-162">Posicionar instruções throw de modo que o rastreamento de pilha seja útil</span><span class="sxs-lookup"><span data-stu-id="aa845-162">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="aa845-163">O rastreamento de pilha começa na instrução na qual a exceção é lançada e termina na instrução `catch` que captura a exceção.</span><span class="sxs-lookup"><span data-stu-id="aa845-163">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="aa845-164">Usar métodos de construtor de exceção</span><span class="sxs-lookup"><span data-stu-id="aa845-164">Use exception builder methods</span></span>

<span data-ttu-id="aa845-165">É comum uma classe lançar a mesma exceção em locais diferentes em sua implementação.</span><span class="sxs-lookup"><span data-stu-id="aa845-165">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="aa845-166">Para evitar excesso de código, use métodos auxiliares que criam a exceção e a retornam.</span><span class="sxs-lookup"><span data-stu-id="aa845-166">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="aa845-167">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="aa845-167">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="aa845-168">Em alguns casos, é mais adequado usar o construtor da exceção para compilá-la.</span><span class="sxs-lookup"><span data-stu-id="aa845-168">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="aa845-169">Um exemplo é uma classe de exceção global como <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="aa845-169">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a><span data-ttu-id="aa845-170">Limpar resultados intermediários ao lançar uma exceção</span><span class="sxs-lookup"><span data-stu-id="aa845-170">Clean up intermediate results when throwing an exception</span></span>

<span data-ttu-id="aa845-171">Os chamadores devem ser capazes de pressupor que não haverá efeitos colaterais quando uma exceção for gerada de um método.</span><span class="sxs-lookup"><span data-stu-id="aa845-171">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="aa845-172">Por exemplo, se você tiver um código que transfere dinheiro retirando-o de uma conta e depositando em outra e uma exceção for gerada ao executar o depósito, você não desejará que a retirada permaneça em vigor.</span><span class="sxs-lookup"><span data-stu-id="aa845-172">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="aa845-173">Uma maneira de lidar com essa situação é capturar todas as exceções geradas pela transação do depósito e reverter a retirada.</span><span class="sxs-lookup"><span data-stu-id="aa845-173">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

<span data-ttu-id="aa845-174">Este exemplo ilustra o uso de `throw` para gerar novamente a exceção original, que pode tornar mais fácil para os chamadores ver a causa real do problema sem a necessidade de examinar a propriedade <xref:System.Exception.InnerException>.</span><span class="sxs-lookup"><span data-stu-id="aa845-174">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="aa845-175">Uma alternativa é gerar uma nova exceção e incluir a exceção original como a exceção interna:</span><span class="sxs-lookup"><span data-stu-id="aa845-175">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a><span data-ttu-id="aa845-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa845-176">See Also</span></span>  
[<span data-ttu-id="aa845-177">Exceções</span><span class="sxs-lookup"><span data-stu-id="aa845-177">Exceptions</span></span>](index.md)
