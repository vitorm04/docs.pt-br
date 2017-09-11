---
title: "Criando e lançando exceções (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5f49b0911aa94480988987f209bc73d187451620
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a><span data-ttu-id="36bea-102">Criando e lançando exceções (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="36bea-102">Creating and Throwing Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="36bea-103">As exceções são usadas para indicar que ocorreu um erro durante a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="36bea-103">Exceptions are used to indicate that an error has occurred while running the program.</span></span> <span data-ttu-id="36bea-104">Objetos de exceção que descrevem um erro são criados e, em seguida, *lançados* com a palavra-chave [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="36bea-104">Exception objects that describe an error are created and then *thrown* with the [throw](../../../csharp/language-reference/keywords/throw.md) keyword.</span></span> <span data-ttu-id="36bea-105">Então, o tempo de execução procura o manipulador de exceção mais compatível.</span><span class="sxs-lookup"><span data-stu-id="36bea-105">The runtime then searches for the most compatible exception handler.</span></span>  
  
 <span data-ttu-id="36bea-106">Os programadores devem lançar exceções quando uma ou mais das seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="36bea-106">Programmers should throw exceptions when one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="36bea-107">O método não pode concluir sua funcionalidade definida.</span><span class="sxs-lookup"><span data-stu-id="36bea-107">The method cannot complete its defined functionality.</span></span>  
  
     <span data-ttu-id="36bea-108">Por exemplo, se um parâmetro para um método tem um valor inválido:</span><span class="sxs-lookup"><span data-stu-id="36bea-108">For example, if a parameter to a method has an invalid value:</span></span>  
  
     <span data-ttu-id="36bea-109">[!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="36bea-109">[!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]</span></span>  
  
-   <span data-ttu-id="36bea-110">É feita uma chamada inadequada a um objeto, com base no estado do objeto.</span><span class="sxs-lookup"><span data-stu-id="36bea-110">An inappropriate call to an object is made, based on the object state.</span></span>  
  
     <span data-ttu-id="36bea-111">Um exemplo pode ser a tentativa de gravar em um arquivo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="36bea-111">One example might be trying to write to a read-only file.</span></span> <span data-ttu-id="36bea-112">Em casos em que um estado do objeto não permite uma operação, lance uma instância de <xref:System.InvalidOperationException> ou um objeto com base em uma derivação dessa classe.</span><span class="sxs-lookup"><span data-stu-id="36bea-112">In cases where an object state does not allow an operation, throw an instance of <xref:System.InvalidOperationException> or an object based on a derivation of this class.</span></span> <span data-ttu-id="36bea-113">Este é um exemplo de um método que gera um objeto <xref:System.InvalidOperationException>:</span><span class="sxs-lookup"><span data-stu-id="36bea-113">This is an example of a method that throws an <xref:System.InvalidOperationException> object:</span></span>  
  
     <span data-ttu-id="36bea-114">[!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="36bea-114">[!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]</span></span>  
  
-   <span data-ttu-id="36bea-115">Quando um argumento para um método causa uma exceção.</span><span class="sxs-lookup"><span data-stu-id="36bea-115">When an argument to a method causes an exception.</span></span>  
  
     <span data-ttu-id="36bea-116">Nesse caso, a exceção original deve ser capturada e uma instância de <xref:System.ArgumentException> deve ser criada.</span><span class="sxs-lookup"><span data-stu-id="36bea-116">In this case, the original exception should be caught and an <xref:System.ArgumentException> instance should be created.</span></span> <span data-ttu-id="36bea-117">A exceção original deve ser passada para o construtor do <xref:System.ArgumentException> como o parâmetro <xref:System.Exception.InnerException%2A>:</span><span class="sxs-lookup"><span data-stu-id="36bea-117">The original exception should be passed to the constructor of the <xref:System.ArgumentException> as the <xref:System.Exception.InnerException%2A> parameter:</span></span>  
  
     <span data-ttu-id="36bea-118">[!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="36bea-118">[!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]</span></span>  
  
 <span data-ttu-id="36bea-119">As exceções contêm uma propriedade chamada <xref:System.Exception.StackTrace%2A>.</span><span class="sxs-lookup"><span data-stu-id="36bea-119">Exceptions contain a property named <xref:System.Exception.StackTrace%2A>.</span></span> <span data-ttu-id="36bea-120">Essa cadeia de caracteres contém o nome dos métodos na pilha de chamadas atual, junto com o nome de arquivo e o número de linha em que a exceção foi lançada para cada método.</span><span class="sxs-lookup"><span data-stu-id="36bea-120">This string contains the name of the methods on the current call stack, together with the file name and line number where the exception was thrown for each method.</span></span> <span data-ttu-id="36bea-121">Um objeto <xref:System.Exception.StackTrace%2A> é criado automaticamente pelo CLR (Common Language Runtime) no ponto da instrução `throw`, de modo que as exceções devem ser lançadas do ponto em que o rastreamento de pilha deve começar.</span><span class="sxs-lookup"><span data-stu-id="36bea-121">A <xref:System.Exception.StackTrace%2A> object is created automatically by the common language runtime (CLR) from the point of the `throw` statement, so that exceptions must be thrown from the point where the stack trace should begin.</span></span>  
  
 <span data-ttu-id="36bea-122">Todas as exceções contêm uma propriedade chamada <xref:System.Exception.Message%2A>.</span><span class="sxs-lookup"><span data-stu-id="36bea-122">All exceptions contain a property named <xref:System.Exception.Message%2A>.</span></span> <span data-ttu-id="36bea-123">Essa cadeia de caracteres deve ser definida para explicar o motivo da exceção.</span><span class="sxs-lookup"><span data-stu-id="36bea-123">This string should be set to explain the reason for the exception.</span></span> <span data-ttu-id="36bea-124">Observe que as informações que são sensíveis à segurança não devem ser colocadas no texto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="36bea-124">Note that information that is sensitive to security should not be put in the message text.</span></span> <span data-ttu-id="36bea-125">Além <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contém uma propriedade chamada <xref:System.ArgumentException.ParamName%2A> que deve ser definida como o nome do argumento que causou a exceção a ser lançada.</span><span class="sxs-lookup"><span data-stu-id="36bea-125">In addition to <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contains a property named <xref:System.ArgumentException.ParamName%2A> that should be set to the name of the argument that caused the exception to be thrown.</span></span> <span data-ttu-id="36bea-126">No caso de um setter de propriedade <xref:System.ArgumentException.ParamName%2A> deve ser definido como `value`.</span><span class="sxs-lookup"><span data-stu-id="36bea-126">In the case of a property setter, <xref:System.ArgumentException.ParamName%2A> should be set to `value`.</span></span>  
  
 <span data-ttu-id="36bea-127">Os membros de métodos públicos e protegidos devem lançar exceções sempre que não puderem concluir suas funções pretendidas.</span><span class="sxs-lookup"><span data-stu-id="36bea-127">Public and protected methods members should throw exceptions whenever they cannot complete their intended functions.</span></span> <span data-ttu-id="36bea-128">A classe de exceção que é lançada deve ser a exceção mais específica disponível que se adapta às condições do erro.</span><span class="sxs-lookup"><span data-stu-id="36bea-128">The exception class that is thrown should be the most specific exception available that fits the error conditions.</span></span> <span data-ttu-id="36bea-129">Essas exceções devem ser documentadas como parte da funcionalidade de classe e as classes derivadas ou as atualizações da classe original devem manter o mesmo comportamento para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="36bea-129">These exceptions should be documented as part of the class functionality, and derived classes or updates to the original class should retain the same behavior for backward compatibility.</span></span>  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a><span data-ttu-id="36bea-130">Coisas a serem evitadas ao lançar exceções</span><span class="sxs-lookup"><span data-stu-id="36bea-130">Things to Avoid When Throwing Exceptions</span></span>  
 <span data-ttu-id="36bea-131">A lista a seguir identifica as práticas a serem evitadas ao lançar exceções:</span><span class="sxs-lookup"><span data-stu-id="36bea-131">The following list identifies practices to avoid when throwing exceptions:</span></span>  
  
-   <span data-ttu-id="36bea-132">As exceções não devem ser usadas para alterar o fluxo de um programa, como parte da execução normal.</span><span class="sxs-lookup"><span data-stu-id="36bea-132">Exceptions should not be used to change the flow of a program as part of ordinary execution.</span></span> <span data-ttu-id="36bea-133">As exceções só devem ser usadas para relatar e tratar condições de erro.</span><span class="sxs-lookup"><span data-stu-id="36bea-133">Exceptions should only be used to report and handle error conditions.</span></span>  
  
-   <span data-ttu-id="36bea-134">As exceções não devem ser retornadas como um valor retornado ou um parâmetro em vez de serem lançadas.</span><span class="sxs-lookup"><span data-stu-id="36bea-134">Exceptions should not be returned as a return value or parameter instead of being thrown.</span></span>  
  
-   <span data-ttu-id="36bea-135">Não lance <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName> ou <xref:System.IndexOutOfRangeException?displayProperty=fullName> intencionalmente de seu próprio código-fonte.</span><span class="sxs-lookup"><span data-stu-id="36bea-135">Do not throw <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName>, or <xref:System.IndexOutOfRangeException?displayProperty=fullName> intentionally from your own source code.</span></span>  
  
-   <span data-ttu-id="36bea-136">Não crie exceções que podem ser lançadas no modo de depuração, mas não no modo de versão.</span><span class="sxs-lookup"><span data-stu-id="36bea-136">Do not create exceptions that can be thrown in debug mode but not release mode.</span></span> <span data-ttu-id="36bea-137">Em vez disso, use o Debug Assert para identificar erros em tempo de execução durante a fase de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="36bea-137">To identify run-time errors during the development phase, use Debug Assert instead.</span></span>  
  
## <a name="defining-exception-classes"></a><span data-ttu-id="36bea-138">Definindo classes de exceção</span><span class="sxs-lookup"><span data-stu-id="36bea-138">Defining Exception Classes</span></span>  
 <span data-ttu-id="36bea-139">Os programas podem lançar uma classe de exceção predefinida no namespace <xref:System> (exceto quando observado anteriormente) ou criar suas próprias classes de exceção, derivando de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="36bea-139">Programs can throw a predefined exception class in the <xref:System> namespace (except where previously noted), or create their own exception classes by deriving from <xref:System.Exception>.</span></span> <span data-ttu-id="36bea-140">AS classes derivadas devem definir pelo menos quatro construtores: um construtor padrão, um que define a propriedade de mensagem e um que define as propriedades <xref:System.Exception.Message%2A> e <xref:System.Exception.InnerException%2A>.</span><span class="sxs-lookup"><span data-stu-id="36bea-140">The derived classes should define at least four constructors: one default constructor, one that sets the message property, and one that sets both the <xref:System.Exception.Message%2A> and <xref:System.Exception.InnerException%2A> properties.</span></span> <span data-ttu-id="36bea-141">O quarto construtor é usado para serializar a exceção.</span><span class="sxs-lookup"><span data-stu-id="36bea-141">The fourth constructor is used to serialize the exception.</span></span> <span data-ttu-id="36bea-142">Novas classes de exceção devem ser serializáveis.</span><span class="sxs-lookup"><span data-stu-id="36bea-142">New exception classes should be serializable.</span></span> <span data-ttu-id="36bea-143">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="36bea-143">For example:</span></span>  
  
 <span data-ttu-id="36bea-144">[!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="36bea-144">[!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]</span></span>  
  
 <span data-ttu-id="36bea-145">Novas propriedades só devem ser adicionadas à classe de exceção quando os dados que elas fornecem são úteis para resolver a exceção.</span><span class="sxs-lookup"><span data-stu-id="36bea-145">New properties should only be added to the exception class when the data they provide is useful to resolving the exception.</span></span> <span data-ttu-id="36bea-146">Se forem adicionadas novas propriedades à classe de exceção derivada, `ToString()` deverá ser substituído para retornar as informações adicionadas.</span><span class="sxs-lookup"><span data-stu-id="36bea-146">If new properties are added to the derived exception class, `ToString()` should be overridden to return the added information.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="36bea-147">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="36bea-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="36bea-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36bea-148">See Also</span></span>  
 <span data-ttu-id="36bea-149">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="36bea-149">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="36bea-150">[Exceções e tratamento de exceções](../../../csharp/programming-guide/exceptions/index.md) </span><span class="sxs-lookup"><span data-stu-id="36bea-150">[Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md) </span></span>  
 <span data-ttu-id="36bea-151">[Hierarquia de exceções](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b) </span><span class="sxs-lookup"><span data-stu-id="36bea-151">[Exception Hierarchy](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b) </span></span>  
 [<span data-ttu-id="36bea-152">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="36bea-152">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)

