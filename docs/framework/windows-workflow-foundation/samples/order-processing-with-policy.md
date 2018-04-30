---
title: Processamento de aplicativos com a política
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f99db44a636a5255990f734d34266b3b2e4a678b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="9498b-102">Processamento de aplicativos com a política</span><span class="sxs-lookup"><span data-stu-id="9498b-102">Order Processing with Policy</span></span>
<span data-ttu-id="9498b-103">O exemplo de política de processamento de aplicativos demonstra alguns dos principais recursos introduzidos em [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] do Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="9498b-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="9498b-104">A seguinte funcionalidade é novo para o mecanismo de regras WF:</span><span class="sxs-lookup"><span data-stu-id="9498b-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="9498b-105">Suporte para a sobrecarga de operador.</span><span class="sxs-lookup"><span data-stu-id="9498b-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="9498b-106">Suporte para o operador de `new` , permitindo que os usuários criem novos objetos e matrizes de regras WF.</span><span class="sxs-lookup"><span data-stu-id="9498b-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="9498b-107">Suporte para que os métodos de extensão da experiência do usuário em chamando métodos de extensão de regras WF compatível com os estilos de codificação C#.</span><span class="sxs-lookup"><span data-stu-id="9498b-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9498b-108">Esse exemplo requer que [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] está instalado para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="9498b-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]<span data-ttu-id="9498b-109"> é necessário para abrir arquivos de projeto e de solução.</span><span class="sxs-lookup"><span data-stu-id="9498b-109"> is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="9498b-110">O exemplo demonstra um projeto de `OrderProcessingPolicy` a que um pedido de cliente, que consiste em uma lista numerada de itens disponíveis e um código postal, é inserido.</span><span class="sxs-lookup"><span data-stu-id="9498b-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="9498b-111">A ordem é processado com êxito se ambas as entradas estão corretas; caso contrário, a diretiva cria objetos de erro, utilizando um operador sobrecarregado de `+` e um método de extensão predefinido para informar ao usuário de erros.</span><span class="sxs-lookup"><span data-stu-id="9498b-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9498b-112">Para obter mais informações sobre métodos de extensão, consulte [c# versão 3.0 especificação](http://go.microsoft.com/fwlink/?LinkId=95402).</span><span class="sxs-lookup"><span data-stu-id="9498b-112">For more information about extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="9498b-113">O exemplo é composto de projetos seguintes:</span><span class="sxs-lookup"><span data-stu-id="9498b-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="9498b-114">`OrderErrorLibrary` é uma biblioteca de classe que define `OrderError` e classes de `OrderErrorCollection` .</span><span class="sxs-lookup"><span data-stu-id="9498b-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="9498b-115">Uma instância de `OrderError` é criada quando uma entrada inválida está inserido.</span><span class="sxs-lookup"><span data-stu-id="9498b-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="9498b-116">A biblioteca também fornece um método de extensão na classe de `OrderErrorCollection` a saída a propriedade de `ErrorText` em todos os objetos de `OrderError` em `OrderErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="9498b-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="9498b-117">O projeto de `OrderProcessingPolicy` é um aplicativo de console de WF que define uma única atividade de `PolicyFromFile` .</span><span class="sxs-lookup"><span data-stu-id="9498b-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="9498b-118">A atividade tem as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="9498b-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="9498b-119">Essa regra que valida o número de item está entre 1 e 6, inclusive.</span><span class="sxs-lookup"><span data-stu-id="9498b-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="9498b-120">Se o número de item está dentro do intervalo válido, a regra não fará nada (diferente da impressão no console).</span><span class="sxs-lookup"><span data-stu-id="9498b-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="9498b-121">Se o número de item não está entre 1 e 6, a regra de `invalidItemNum` faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9498b-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="9498b-122">Cria um novo objeto de `OrderError` , passando o número de item inserido, e defina as propriedades de `ErrorText` e de `CustomerName` no objeto.</span><span class="sxs-lookup"><span data-stu-id="9498b-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="9498b-123">Cria um objeto de `invalidItemNumErrorCollection` .</span><span class="sxs-lookup"><span data-stu-id="9498b-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="9498b-124">Adicione a instância recém-criado de `OrderError` a `invalidItemNumErrorCollection`.</span><span class="sxs-lookup"><span data-stu-id="9498b-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="9498b-125">Isso demonstra suporte para o operador de `new` , com o qual você pode instanciar objetos dentro das regras.</span><span class="sxs-lookup"><span data-stu-id="9498b-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="9498b-126">Essa regra valida que o código postal tem 5 dígitos, e está no intervalo de 600 a 99998.</span><span class="sxs-lookup"><span data-stu-id="9498b-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="9498b-127">Se o código postal está dentro do intervalo válido, a regra não fará nada (diferente da impressão no console).</span><span class="sxs-lookup"><span data-stu-id="9498b-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="9498b-128">Se o comprimento do código postal é menor que 5, ou o código postal não está entre 00600 e 99998, a regra de `invalidZip` faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9498b-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="9498b-129">Cria um objeto de `OrderError` , passando o código postal inserido, e defina as propriedades de `ErrorText` e de `CustomerName` no objeto.</span><span class="sxs-lookup"><span data-stu-id="9498b-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="9498b-130">Cria um objeto de `invalidZipCodeErrorCollection` .</span><span class="sxs-lookup"><span data-stu-id="9498b-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="9498b-131">Adicione a instância recém-criado de `OrderError` a `invalidZipCodeErrorCollection`recém-criado.</span><span class="sxs-lookup"><span data-stu-id="9498b-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="9498b-132">Essa regra demonstra novamente suporte para o operador de `new` , que permite que você crie uma instância de objetos dentro das regras.</span><span class="sxs-lookup"><span data-stu-id="9498b-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="9498b-133">Essa regra verifica para ver se houver erros adicionado por duas regras anteriores dos dois objetos `OrderErrorCollection` e `invalidItemNumErrorCollection`de `invalidIZipCodeErrorCollection` .</span><span class="sxs-lookup"><span data-stu-id="9498b-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="9498b-134">Se ocorreram erros ( `invalidItemNumErrorCollection` ou `invalidZipCodeErrorCollection` não são `null`), a regra faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9498b-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="9498b-135">Chama o sobrecarregado `+` operador para copiar o conteúdo de `invalidItemNumErrorCollection` e `invalidZipCodeErrorCollection` para um `invalidOrdersCollection``OrderErrorCollection` instância.</span><span class="sxs-lookup"><span data-stu-id="9498b-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="9498b-136">Chama o método de extensão de `PrintOrderErrors` em `invalidOrdersCollection` e saída que a propriedade de `ErrorText` em qualquer `orderError` objetos em `invalidOrdersCollection`.</span><span class="sxs-lookup"><span data-stu-id="9498b-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="9498b-137">O operador sobrecarregado `+` em `OrderErrorCollection` é definido na classe de `OrderErrorCollection` , no projeto de `OrderErrorLibrary` .</span><span class="sxs-lookup"><span data-stu-id="9498b-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="9498b-138">Leva dois objetos de `OrderErrorCollection` e os combina em um objeto de `OrderErrorCollection` .</span><span class="sxs-lookup"><span data-stu-id="9498b-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="9498b-139">O método de extensão de `PrintOrderErrors` também é definido no projeto de `OrderErrorLibrary` .</span><span class="sxs-lookup"><span data-stu-id="9498b-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="9498b-140">Métodos de extensão é um novo recurso C# que habilita os desenvolvedores para adicionar novos métodos ao contrato pública de um tipo existente de CLR, sem ter que derivar uma classe deles ou recompilar o tipo original.</span><span class="sxs-lookup"><span data-stu-id="9498b-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="9498b-141">Quando você executa o exemplo você será solicitado para digitar um nome, ao número de item de item a ser comprado, e um código postal.</span><span class="sxs-lookup"><span data-stu-id="9498b-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="9498b-142">Essa informação é verificada nas regras definidas na atividade de política.</span><span class="sxs-lookup"><span data-stu-id="9498b-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="9498b-143">O seguinte é saída de exemplo do programa.</span><span class="sxs-lookup"><span data-stu-id="9498b-143">The following is sample output from the program.</span></span>  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9498b-144">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9498b-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9498b-145">Abra o arquivo de projeto de OrderProcessingPolicy.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9498b-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9498b-146">Há dois diferentes projetos na solução: `OrderErrorLibrary` e `OrderProcessingPolicy`.</span><span class="sxs-lookup"><span data-stu-id="9498b-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="9498b-147">As classes e métodos dos usos de projeto de `OrderProcessingPolicy` definidos em `OrderErrorLibrary`.</span><span class="sxs-lookup"><span data-stu-id="9498b-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="9498b-148">Compilar todos os projetos.</span><span class="sxs-lookup"><span data-stu-id="9498b-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="9498b-149">Clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="9498b-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9498b-150">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9498b-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9498b-151">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="9498b-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9498b-152">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9498b-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9498b-153">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="9498b-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`