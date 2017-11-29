---
title: Hello atividade personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b05608ca0704483f4318342a733ce363c0a66fc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="e4cf0-102">Hello atividade personalizado</span><span class="sxs-lookup"><span data-stu-id="e4cf0-102">Hello World Custom Activity</span></span>
<span data-ttu-id="e4cf0-103">Este exemplo demonstra vários recursos chave de [!INCLUDE[wf](../../../../includes/wf-md.md)], incluindo como criar uma atividade personalizado simples.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-103">This sample demonstrates several key features of [!INCLUDE[wf](../../../../includes/wf-md.md)], including how to create a simple custom activity.</span></span> <span data-ttu-id="e4cf0-104">Alguns dos recursos demonstrados nesse exemplo são criando uma atividade personalizado em C# e estão usando `in` e argumentos de `out` (<xref:System.Activities.InArgument> e <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="e4cf0-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4cf0-105">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e4cf0-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e4cf0-107">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4cf0-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="e4cf0-109">Criando um fluxo de trabalho no código</span><span class="sxs-lookup"><span data-stu-id="e4cf0-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="e4cf0-110">Nesse exemplo, duas atividades personalizados são criadas usando o código em c.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="e4cf0-111">Ambas as atividades personalizados herdam direta ou indiretamente de <xref:System.Activities.Activity%601> para retornar um único valor.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="e4cf0-112">A vantagem de usar o valor de retorno genérico, em vez de herdar da classe não genérico de <xref:System.Activities.Activity> , é que quaisquer atividades (como <xref:System.Activities.Statements.Assign>) podem acessar o valor de retorno quando usadas como parte de uma atividade composto.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="e4cf0-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="e4cf0-113">AppendString</span></span>  
 <span data-ttu-id="e4cf0-114">Esta atividade herda de <xref:System.Activities.Activity%601>, e usa uma atividade de <xref:System.Activities.Statements.Assign> que concatene duas cadeias de caracteres juntos.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="e4cf0-115">Preceda a cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e4cf0-115">Prepend String</span></span>  
 <span data-ttu-id="e4cf0-116">Esta atividade herda diretamente de <xref:System.Activities.CodeActivity%601>, e criar a funcionalidade semelhante à atividade de `AppendString` , que usa a lógica implementada no código em vez de ser composta de uma atividade preexistente.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="e4cf0-117">Os seguintes arquivos são incluídos no projeto.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="e4cf0-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="e4cf0-118">AppendString.cs</span></span>  
 <span data-ttu-id="e4cf0-119">A atividade personalizado que acrescenta cadeias de caracteres juntos.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="e4cf0-120">Ele usa uma cadeia de caracteres e a combina com uma cadeia de caracteres de texto literal "hello world diz" para formar uma mensagem completa como saída.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="e4cf0-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="e4cf0-121">PrependString.cs</span></span>  
 <span data-ttu-id="e4cf0-122">Esta atividade prefixar uma cadeia de caracteres predefinida a uma cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="e4cf0-123">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="e4cf0-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="e4cf0-124">Um fluxo de trabalho que usa as atividades personalizado de `AppendString` e de `PrependString` .</span><span class="sxs-lookup"><span data-stu-id="e4cf0-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="e4cf0-125">Module.vb</span><span class="sxs-lookup"><span data-stu-id="e4cf0-125">Program.cs</span></span>  
 <span data-ttu-id="e4cf0-126">Um programa que executa o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e4cf0-127">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="e4cf0-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="e4cf0-128">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e4cf0-129">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e4cf0-130">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="e4cf0-130">To run the solution, press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cf0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4cf0-131">See Also</span></span>
