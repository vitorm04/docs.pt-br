---
title: InvokeMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b90ebec929b310442cde2be8d96386e016a9bbb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="invokemethod"></a><span data-ttu-id="0193c-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="0193c-102">InvokeMethod</span></span>
<span data-ttu-id="0193c-103">Este exemplo mostra as diferentes maneiras de usar a atividade de <xref:System.Activities.Statements.InvokeMethod> para chamar métodos de uma classe.</span><span class="sxs-lookup"><span data-stu-id="0193c-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="0193c-104">Um método pertence a uma classe e representa um conjunto contido de operações.</span><span class="sxs-lookup"><span data-stu-id="0193c-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="0193c-105">A atividade de <xref:System.Activities.Statements.InvokeMethod> oferece a você a capacidade de chamar métodos contra objetos, ou tipos de passar os parâmetros, e para obter o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="0193c-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="0193c-106">Os métodos podem ser chamados de forma síncrona ou de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="0193c-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="0193c-107">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="0193c-107">Sample Details</span></span>  
 <span data-ttu-id="0193c-108">Este exemplo usa a atividade de <xref:System.Activities.Statements.InvokeMethod> para executar os seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="0193c-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="0193c-109">Chamar um método de instância sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0193c-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="0193c-110">Chamar um método de instância com dois parâmetros (<xref:System.String> e <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="0193c-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="0193c-111">Chamar um método de instância com dois parâmetros (<xref:System.String> e <xref:System.Int32>) e uma matriz de parâmetros de tipo <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="0193c-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="0193c-112">Chamar um método de instância com dois parâmetros de tipo <xref:System.Int32> e um resultado de tipo <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="0193c-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="0193c-113">Nesse cenário, o valor do resultado é associado a uma variável e usado em outra atividade.</span><span class="sxs-lookup"><span data-stu-id="0193c-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="0193c-114">É exibido no console usando a atividade de <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="0193c-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="0193c-115">Chamar um método estático com dois parâmetros de tipo <xref:System.String> e <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="0193c-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="0193c-116">Chamar um método de instância com um parâmetro de tipo genérico <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0193c-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="0193c-117">Chamar um método estático com dois parâmetros de tipo genéricos <xref:System.String> e <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="0193c-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="0193c-118">Chamar um método de instância que tem um parâmetro passado por referência de tipo <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0193c-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="0193c-119">Nesse cenário, o parâmetro de referência é associado a uma variável (`outParam`) e usado em outra atividade.</span><span class="sxs-lookup"><span data-stu-id="0193c-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="0193c-120">É exibido no console usando a atividade de <xref:System.Activities.Statements.WriteLine> .</span><span class="sxs-lookup"><span data-stu-id="0193c-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="0193c-121">Chamar um método de instância assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0193c-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="0193c-122">Chamar dois diferentes métodos na mesma instância de um objeto usando duas atividades de <xref:System.Activities.Statements.InvokeMethod> .</span><span class="sxs-lookup"><span data-stu-id="0193c-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="0193c-123">Armazenar um valor em uma instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="0193c-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="0193c-124">Recuperar um valor de uma instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="0193c-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="0193c-125">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="0193c-125">To use this sample</span></span>  
 <span data-ttu-id="0193c-126">Este exemplo é fornecido em duas versões.</span><span class="sxs-lookup"><span data-stu-id="0193c-126">This sample is provided in two versions.</span></span> <span data-ttu-id="0193c-127">A primeira versão este exemplo demonstra o uso de <xref:System.Activities.Statements.InvokeMethod> com o código em c usando a programação de [!INCLUDE[wf](../../../../includes/wf-md.md)] modelo e pode ser encontrada na pasta de CodedWorkflow \ CS.</span><span class="sxs-lookup"><span data-stu-id="0193c-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the [!INCLUDE[wf](../../../../includes/wf-md.md)] programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="0193c-128">A segunda versão demonstra o uso de <xref:System.Activities.Statements.InvokeMethod> usando XAML e pode ser encontrada na pasta de DesignerWorkflow \ CS.</span><span class="sxs-lookup"><span data-stu-id="0193c-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="0193c-129">Para executar o exemplo codificado de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0193c-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="0193c-130">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InvokeMethodUsage.sln na pasta de CodedWorkflow \ CS.</span><span class="sxs-lookup"><span data-stu-id="0193c-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="0193c-131">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="0193c-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0193c-132">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="0193c-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="0193c-133">Para executar o exemplo de fluxo de trabalho do designer</span><span class="sxs-lookup"><span data-stu-id="0193c-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="0193c-134">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InvokeMethodUsage.sln na pasta de DesignerWorkflow \ CS.</span><span class="sxs-lookup"><span data-stu-id="0193c-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="0193c-135">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="0193c-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0193c-136">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="0193c-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0193c-137">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0193c-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0193c-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0193c-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0193c-139">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0193c-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0193c-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0193c-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`