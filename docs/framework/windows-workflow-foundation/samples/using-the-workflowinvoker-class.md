---
title: Usando a classe de WorkflowInvoker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8bb6c4049b56702c8fad226c20884ff581ec6203
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="36e8b-102">Usando a classe de WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="36e8b-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="36e8b-103">Este exemplo demonstra como usar a classe de <xref:System.Activities.WorkflowInvoker> para chamar uma atividade como se fosse um método.</span><span class="sxs-lookup"><span data-stu-id="36e8b-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="36e8b-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="36e8b-104">Sample Details</span></span>  
 <span data-ttu-id="36e8b-105">Usar a classe de <xref:System.Activities.WorkflowInvoker> é a maneira mais simples para executar uma atividade.</span><span class="sxs-lookup"><span data-stu-id="36e8b-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="36e8b-106">É criada diretamente executando uma atividade como se fosse um chamada de método.</span><span class="sxs-lookup"><span data-stu-id="36e8b-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="36e8b-107">É um leve, alto executando, a API fácil de usar para uso em cenários onde a execução de uma atividade não requer a infraestrutura do controle fornecida por outras variações de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="36e8b-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="36e8b-108">O exemplo usa uma atividade personalizada que é derivada de <xref:System.Activities.CodeActivity%601>< Int32\> chamado `Add` que adiciona dois <xref:System.Activities.InArgument%601>, `X` e `Y`e retorna um `Result` <xref:System.Activities.OutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="36e8b-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="36e8b-109">(<xref:System.Activities.CodeActivity%601>\<T > derivado <xref:System.Activities.Activity%601>< T\>, que tem um <xref:System.Activities.OutArgument%601> \<T > denominado `Result`.) Um `Dictionary` \<de cadeia de caracteres, objeto > é usado para passar argumentos para uma atividade que está sendo invocada pelo <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="36e8b-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="36e8b-110">A chave do dicionário corresponde ao nome de um argumento na chamada atividade.</span><span class="sxs-lookup"><span data-stu-id="36e8b-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="36e8b-111">O valor associado com uma chave específica é associado ao argumento identificado por chave.</span><span class="sxs-lookup"><span data-stu-id="36e8b-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="36e8b-112">O exemplo chama <xref:System.Activities.WorkflowInvoker.Invoke%2A> e passa um dicionário que contém valores para `X` e `Y`.</span><span class="sxs-lookup"><span data-stu-id="36e8b-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="36e8b-113">A classe de <xref:System.Activities.WorkflowInvoker> associa esses valores para os argumentos de atividade de `Add` , executa a atividade, e retorna o resultado.</span><span class="sxs-lookup"><span data-stu-id="36e8b-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="36e8b-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="36e8b-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="36e8b-115">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Invoker.sln.</span><span class="sxs-lookup"><span data-stu-id="36e8b-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="36e8b-116">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="36e8b-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="36e8b-117">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="36e8b-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="36e8b-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="36e8b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="36e8b-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="36e8b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="36e8b-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="36e8b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="36e8b-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="36e8b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`