---
title: Melhores práticas para exceções – .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: d212ba9beaa0ccc229204045c5a8174381440dfc
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860159"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="23259-102">Práticas recomendadas para exceções</span><span class="sxs-lookup"><span data-stu-id="23259-102">Best practices for exceptions</span></span>

<span data-ttu-id="23259-103">Um aplicativo bem projetado sabe tratar erros e exceções para evitar falhas.</span><span class="sxs-lookup"><span data-stu-id="23259-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="23259-104">Esta seção descreve as práticas recomendadas para tratar e criar exceções.</span><span class="sxs-lookup"><span data-stu-id="23259-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="23259-105">Usar blocos try/catch/finally para se recuperar de erros ou liberar recursos</span><span class="sxs-lookup"><span data-stu-id="23259-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="23259-106">Use blocos `try`/`catch` ao redor de código que pode potencialmente gerar uma exceção ***e*** seu código pode se recuperar dessa exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="23259-107">Em blocos `catch`, sempre ordene as exceções da mais derivada para a menos derivada.</span><span class="sxs-lookup"><span data-stu-id="23259-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="23259-108">Todas as exceções derivam de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="23259-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="23259-109">Exceções mais derivadas não são manipuladas por uma cláusula catch é precedido por uma cláusula catch de uma classe de exceção base.</span><span class="sxs-lookup"><span data-stu-id="23259-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="23259-110">Quando seu código não pode se recuperar de uma exceção, não use cláusula catch nessa exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="23259-111">Habilite métodos adicionais na pilha de chamadas para se recuperar se possível.</span><span class="sxs-lookup"><span data-stu-id="23259-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="23259-112">Limpe os recursos alocados com instruções `using` ou blocos `finally`.</span><span class="sxs-lookup"><span data-stu-id="23259-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="23259-113">Prefira instruções `using` para limpar recursos automaticamente quando exceções forem lançadas.</span><span class="sxs-lookup"><span data-stu-id="23259-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="23259-114">Use blocos `finally` para limpar os recursos que não implementam <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="23259-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="23259-115">O código em uma cláusula `finally` quase sempre é executado, mesmo quando exceções são geradas.</span><span class="sxs-lookup"><span data-stu-id="23259-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="23259-116">Tratar de condições comuns sem gerar exceções</span><span class="sxs-lookup"><span data-stu-id="23259-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="23259-117">Para condições que têm boa probabilidade de ocorrer mas que podem disparar uma exceção, considere tratá-las de uma maneira que evite essa exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="23259-118">Por exemplo, se você tentar fechar uma conexão que já está fechada, você obterá um `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="23259-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="23259-119">Você pode evitar isso usando uma instrução `if` para verificar o estado da conexão antes de tentar fechá-la.</span><span class="sxs-lookup"><span data-stu-id="23259-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="23259-120">Se você não verificar estado da conexão antes de fechar, você poderá capturar a exceção `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="23259-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="23259-121">O método a escolher depende da frequência com que você espera que o evento ocorra.</span><span class="sxs-lookup"><span data-stu-id="23259-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="23259-122">Use o tratamento de exceções se o evento não ocorrer muito frequentemente, ou seja, se o evento é realmente excepcional e indica um erro (como um fim de arquivo inesperado).</span><span class="sxs-lookup"><span data-stu-id="23259-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="23259-123">Quando você usa o tratamento de exceções, menos código é executado em condições normais.</span><span class="sxs-lookup"><span data-stu-id="23259-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="23259-124">Verifique a existência de condições de erro no código se o evento ocorrer rotineiramente e puder ser considerado parte da execução normal.</span><span class="sxs-lookup"><span data-stu-id="23259-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="23259-125">Quando você verifica se há condições de erro comuns, menos código é executado porque você evita exceções.</span><span class="sxs-lookup"><span data-stu-id="23259-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="23259-126">Projetar classes de modo que as exceções possam ser evitadas</span><span class="sxs-lookup"><span data-stu-id="23259-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="23259-127">Uma classe pode fornecer métodos ou propriedades que permitem que você evite fazer uma chamada que dispararia uma exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="23259-128">Por exemplo, uma classe <xref:System.IO.FileStream> fornece métodos que ajudam a determinar se ao final do arquivo foi atingido.</span><span class="sxs-lookup"><span data-stu-id="23259-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="23259-129">Elas podem ser usadas para evitar exceções geradas quando você faz a leitura após o fim do arquivo.</span><span class="sxs-lookup"><span data-stu-id="23259-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="23259-130">O exemplo a seguir mostra como ler até o final de um arquivo sem disparar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="23259-131">Outra maneira de evitar exceções é retornar nulo (ou padrão) para casos muito comuns de erro, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="23259-132">Um caso extremamente comum de erro pode ser considerado um fluxo normal de controle.</span><span class="sxs-lookup"><span data-stu-id="23259-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="23259-133">Ao retornar nulo (ou padrão) nesses casos, você minimiza o impacto no desempenho de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23259-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="23259-134">Para tipos de valor, convém considerar o uso de `Nullable<T>` ou padrão como indicador de erro para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23259-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="23259-135">Ao usar `Nullable<Guid>`, `default` se torna `null` em vez de `Guid.Empty`.</span><span class="sxs-lookup"><span data-stu-id="23259-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="23259-136">Algumas vezes, adicionar `Nullable<T>` pode deixar mais claro quando um valor está presente ou ausente.</span><span class="sxs-lookup"><span data-stu-id="23259-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="23259-137">Outras vezes, adicionar `Nullable<T>` pode criar casos extras que não precisam ser verificados e só servem para criar possíveis fontes de erros.</span><span class="sxs-lookup"><span data-stu-id="23259-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span> 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="23259-138">Gerar exceções em vez de retornar um código de erro</span><span class="sxs-lookup"><span data-stu-id="23259-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="23259-139">Exceções asseguram que falhas não passem despercebidas porque o código de chamada não verificou um código de retorno.</span><span class="sxs-lookup"><span data-stu-id="23259-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="23259-140">Usar os tipos de exceção do .NET predefinidos</span><span class="sxs-lookup"><span data-stu-id="23259-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="23259-141">Apresente uma nova classe de exceção apenas quando a predefinida não se aplicar.</span><span class="sxs-lookup"><span data-stu-id="23259-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="23259-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="23259-142">For example:</span></span>

- <span data-ttu-id="23259-143">Gere uma exceção <xref:System.InvalidOperationException> se uma propriedade de definição ou chamada de método não for adequada para o estado atual do objeto.</span><span class="sxs-lookup"><span data-stu-id="23259-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="23259-144">Gere uma exceção <xref:System.ArgumentException> ou uma das classes predefinidas que derivam de <xref:System.ArgumentException> se parâmetros inválidos forem passados.</span><span class="sxs-lookup"><span data-stu-id="23259-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="23259-145">Terminar os nomes das classes de exceção com a palavra `Exception`</span><span class="sxs-lookup"><span data-stu-id="23259-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="23259-146">Quando uma exceção personalizada for necessária, nomeie-a adequadamente e derive-a da classe <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="23259-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="23259-147">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="23259-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="23259-148">Incluir três construtores em classes de exceção personalizada</span><span class="sxs-lookup"><span data-stu-id="23259-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="23259-149">Use pelo menos três os construtores comuns ao criar suas próprias classes de exceção: o construtor sem parâmetros, um construtor que recebe uma mensagem de cadeia de caracteres e uma exceção interna.</span><span class="sxs-lookup"><span data-stu-id="23259-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="23259-150"><xref:System.Exception.%23ctor>, que usa valores padrão.</span><span class="sxs-lookup"><span data-stu-id="23259-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

* <span data-ttu-id="23259-151"><xref:System.Exception.%23ctor%28System.String%29>, que aceita uma mensagem de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="23259-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

* <span data-ttu-id="23259-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, que aceita uma mensagem de cadeia de caracteres e a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="23259-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="23259-153">Para obter um exemplo, consulte [ Como criar exceções definidas pelo usuário](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="23259-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="23259-154">Certifique-se de que os dados de exceção estão disponíveis quando o código é executado remotamente</span><span class="sxs-lookup"><span data-stu-id="23259-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="23259-155">Ao criar exceções definidas pelo usuário, assegure que os metadados para as exceções estejam disponíveis para códigos executando remotamente.</span><span class="sxs-lookup"><span data-stu-id="23259-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="23259-156">Por exemplo, em implementações do .NET que dão suporte a Domínios de Aplicativo, podem ocorrer exceções entre Domínios de Aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23259-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="23259-157">Suponha que o Domínio de Aplicativo A crie o Domínio de aplicativo B, o qual executa o código que gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="23259-158">Para que o Domínio de Aplicativo A capture e trate corretamente a exceção, ele deverá ser capaz de localizar o assembly que contém a exceção gerada pelo Domínio de Aplicativo B. Se o Domínio de Aplicativo B gerar uma exceção contida em um assembly em sua base de aplicativo, mas não na base de aplicativo do Domínio de Aplicativo A, o Domínio de Aplicativo A não será capaz de localizar a exceção e o Common Language Runtime gerará uma exceção <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="23259-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="23259-159">Para evitar essa situação, você pode implantar o assembly que contém as informações de exceção de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="23259-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="23259-160">Coloque o assembly em uma base de aplicativos comum compartilhada por ambos os domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="23259-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="23259-161">\- ou -</span><span class="sxs-lookup"><span data-stu-id="23259-161">\- or -</span></span>

- <span data-ttu-id="23259-162">Se os domínios não compartilham uma base de aplicativos comum, assine o assembly que contém as informações de exceção com um nome forte e implante o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="23259-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="23259-163">Usar mensagens de erro gramaticalmente corretas</span><span class="sxs-lookup"><span data-stu-id="23259-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="23259-164">Escreva frases claras e inclua pontuação final.</span><span class="sxs-lookup"><span data-stu-id="23259-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="23259-165">Cada sentença na cadeia de caracteres atribuída à propriedade <xref:System.Exception.Message?displayProperty=nameWithType> deve terminar com um ponto.</span><span class="sxs-lookup"><span data-stu-id="23259-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="23259-166">Por exemplo, "A tabela de log estourou".</span><span class="sxs-lookup"><span data-stu-id="23259-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="23259-167">seria uma cadeia de caracteres de mensagem adequada.</span><span class="sxs-lookup"><span data-stu-id="23259-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="23259-168">Incluir uma mensagem de cadeia de caracteres localizada em cada exceção</span><span class="sxs-lookup"><span data-stu-id="23259-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="23259-169">A mensagem de erro que o usuário recebe é derivada da propriedade <xref:System.Exception.Message?displayProperty=nameWithType> da exceção que foi gerada, e não do nome da classe de exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="23259-170">Normalmente, você atribui um valor à propriedade <xref:System.Exception.Message?displayProperty=nameWithType> passando a cadeia de caracteres de mensagem para o argumento `message` de um [Construtor de exceção](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="23259-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="23259-171">Para aplicativos localizados, você deverá fornecer uma cadeia de caracteres de mensagem localizada para toda exceção que seu aplicativo puder gerar.</span><span class="sxs-lookup"><span data-stu-id="23259-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="23259-172">Use arquivos de recurso para fornecer mensagens de erro localizadas.</span><span class="sxs-lookup"><span data-stu-id="23259-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="23259-173">Para obter informações sobre como localizar aplicativos e recuperar cadeias de caracteres localizadas, veja [Recursos em aplicativos de área de trabalho](../../framework/resources/index.md) e <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="23259-173">For information on localizing applications and retrieving localized strings, see [Resources in Desktop Apps](../../framework/resources/index.md) and <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="23259-174">Em exceções personalizadas, forneça propriedades adicionais conforme necessário</span><span class="sxs-lookup"><span data-stu-id="23259-174">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="23259-175">Forneça propriedades adicionais para uma exceção (além da cadeia de caracteres de mensagem personalizada) somente quando houver um cenário programático no qual as informações adicionais serão úteis.</span><span class="sxs-lookup"><span data-stu-id="23259-175">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="23259-176">Por exemplo, o <xref:System.IO.FileNotFoundException> fornece a propriedade <xref:System.IO.FileNotFoundException.FileName>.</span><span class="sxs-lookup"><span data-stu-id="23259-176">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="23259-177">Posicionar instruções throw de modo que o rastreamento de pilha seja útil</span><span class="sxs-lookup"><span data-stu-id="23259-177">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="23259-178">O rastreamento de pilha começa na instrução na qual a exceção é lançada e termina na instrução `catch` que captura a exceção.</span><span class="sxs-lookup"><span data-stu-id="23259-178">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="23259-179">Usar métodos de construtor de exceção</span><span class="sxs-lookup"><span data-stu-id="23259-179">Use exception builder methods</span></span>

<span data-ttu-id="23259-180">É comum uma classe lançar a mesma exceção em locais diferentes em sua implementação.</span><span class="sxs-lookup"><span data-stu-id="23259-180">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="23259-181">Para evitar excesso de código, use métodos auxiliares que criam a exceção e a retornam.</span><span class="sxs-lookup"><span data-stu-id="23259-181">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="23259-182">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="23259-182">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="23259-183">Em alguns casos, é mais adequado usar o construtor da exceção para compilá-la.</span><span class="sxs-lookup"><span data-stu-id="23259-183">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="23259-184">Um exemplo é uma classe de exceção global como <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="23259-184">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="23259-185">Restaurar o estado quando os métodos não são concluídos devido a exceções</span><span class="sxs-lookup"><span data-stu-id="23259-185">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="23259-186">Os chamadores devem ser capazes de pressupor que não haverá efeitos colaterais quando uma exceção for gerada de um método.</span><span class="sxs-lookup"><span data-stu-id="23259-186">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="23259-187">Por exemplo, se você tiver um código que transfere dinheiro retirando-o de uma conta e depositando em outra e uma exceção for gerada ao executar o depósito, você não desejará que a retirada permaneça em vigor.</span><span class="sxs-lookup"><span data-stu-id="23259-187">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

<span data-ttu-id="23259-188">O método acima não gera nenhuma exceção diretamente, mas deverá ser escrito de forma defensiva para que, se a operação de depósito falhar, a retirada seja invertida.</span><span class="sxs-lookup"><span data-stu-id="23259-188">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="23259-189">Uma maneira de lidar com essa situação é capturar todas as exceções geradas pela transação do depósito e reverter a retirada.</span><span class="sxs-lookup"><span data-stu-id="23259-189">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

<span data-ttu-id="23259-190">Este exemplo ilustra o uso de `throw` para gerar novamente a exceção original, que pode tornar mais fácil para os chamadores ver a causa real do problema sem a necessidade de examinar a propriedade <xref:System.Exception.InnerException>.</span><span class="sxs-lookup"><span data-stu-id="23259-190">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="23259-191">Uma alternativa é gerar uma nova exceção e incluir a exceção original como a exceção interna:</span><span class="sxs-lookup"><span data-stu-id="23259-191">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a><span data-ttu-id="23259-192">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23259-192">See also</span></span>

- [<span data-ttu-id="23259-193">Exceções</span><span class="sxs-lookup"><span data-stu-id="23259-193">Exceptions</span></span>](index.md)
