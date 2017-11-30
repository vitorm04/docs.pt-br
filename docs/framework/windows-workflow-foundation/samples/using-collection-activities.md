---
title: "Usando atividades de coleção"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84218f16f846e640baea663efc7153a40a6c764a
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="using-collection-activities"></a><span data-ttu-id="29fb8-102">Usando atividades de coleção</span><span class="sxs-lookup"><span data-stu-id="29fb8-102">Using Collection Activities</span></span>
<span data-ttu-id="29fb8-103">Este exemplo demonstra como usar as atividades de coleção (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, e <xref:System.Activities.Statements.RemoveFromCollection%601>) com uma classe que implementa a interface de <xref:System.Collections.ICollection> e como criar uma atividade personalizado que executa iterações sobre uma coleção para imprimir para fora o conteúdo de cada elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-103">This sample demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span> <span data-ttu-id="29fb8-104">A atividade personalizado, que é chamada `PrintCollection`, imprime no console os membros do item de uma coleção chamada `Numbers`.</span><span class="sxs-lookup"><span data-stu-id="29fb8-104">The custom activity, which is named `PrintCollection`, prints to the console the item members of a collection named `Numbers`.</span></span>  
  
 <span data-ttu-id="29fb8-105">A tabela a seguir descreve as quatro atividades que fornecem a manipulação de coleção para fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="29fb8-105">The following table describes the four activities that provide collection manipulation for workflows.</span></span>  
  
|<span data-ttu-id="29fb8-106">Nome da atividade</span><span class="sxs-lookup"><span data-stu-id="29fb8-106">Activity name</span></span>|<span data-ttu-id="29fb8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="29fb8-107">Description</span></span>|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="29fb8-108">Adiciona um item a uma coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-108">Adds an item to a collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="29fb8-109">Limpa todos os itens em uma coleção</span><span class="sxs-lookup"><span data-stu-id="29fb8-109">Clears all items in a collection</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="29fb8-110">Retorna `true` se o item especificado existe na coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-110">Returns `true` if specified item exists in collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="29fb8-111">Remove um item de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-111">Removes an item from a collection.</span></span>|  
  
 <span data-ttu-id="29fb8-112">O exemplo consiste duas soluções, uma no diretório de CodedWorkflow e a outra no diretório de DesignerWorkflow.</span><span class="sxs-lookup"><span data-stu-id="29fb8-112">The sample consists of two solutions, one under the CodedWorkflow directory and the other under the DesignerWorkflow directory.</span></span> <span data-ttu-id="29fb8-113">Demonstram duas maneiras diferentes de usar as atividades para as mesmas fins.</span><span class="sxs-lookup"><span data-stu-id="29fb8-113">They demonstrate two different ways of using the activities for the same purposes.</span></span>  
  
|<span data-ttu-id="29fb8-114">Solução</span><span class="sxs-lookup"><span data-stu-id="29fb8-114">Solution</span></span>|<span data-ttu-id="29fb8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="29fb8-115">Description</span></span>|<span data-ttu-id="29fb8-116">Arquivos de chave</span><span class="sxs-lookup"><span data-stu-id="29fb8-116">Main Files</span></span>|  
|-|-|-|  
|<span data-ttu-id="29fb8-117">CodedWorkflow</span><span class="sxs-lookup"><span data-stu-id="29fb8-117">CodedWorkflow</span></span>|<span data-ttu-id="29fb8-118">Exemplo do aplicativo cliente que demonstra como chamar programaticamente as atividades de coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-118">Sample client application that demonstrates how to invoke the collection activities programmatically.</span></span>|<span data-ttu-id="29fb8-119">**PrintCollection.cs**: atividade de auxiliar para imprimir para o console de cada item em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-119">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="29fb8-120">**Program.CS**: cria programaticamente uma atividade de sequência que contém uma série de atividades de coleção e o executa.</span><span class="sxs-lookup"><span data-stu-id="29fb8-120">**Program.cs**: programmatically builds a sequence activity that contains a series of collection activities, and executes it.</span></span>|  
|<span data-ttu-id="29fb8-121">DesignerWorkflow</span><span class="sxs-lookup"><span data-stu-id="29fb8-121">DesignerWorkflow</span></span>|<span data-ttu-id="29fb8-122">Exemplo do aplicativo cliente que demonstra como usar declarativamente as atividades de coleção no designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="29fb8-122">Sample client application that demonstrates how to use the collection activities declaratively in the workflow designer.</span></span>|<span data-ttu-id="29fb8-123">**CollectionWorkflow.xaml**: um fluxo de trabalho criado declarativamente com o designer que usa as atividades de coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-123">**CollectionWorkflow.xaml**: a workflow created declaratively with the designer that uses the collection activities.</span></span><br /><br /> <span data-ttu-id="29fb8-124">**PrintCollection.cs**: atividade de auxiliar para imprimir para o console de cada item em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="29fb8-124">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="29fb8-125">**Program.CS**: invoca o fluxo de trabalho descrito em CollectionWorkflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="29fb8-125">**Program.cs**: invokes the workflow described in CollectionWorkflow.xaml.</span></span>|  
  
 <span data-ttu-id="29fb8-126">Em demonstração, os membros do item da coleção `Numbers` será impresso no console usando uma atividade de chamada definida `PrintCollection`.</span><span class="sxs-lookup"><span data-stu-id="29fb8-126">In the demonstration, the item members of collection `Numbers` are printed on the console using a custom-defined activity called `PrintCollection`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="29fb8-127">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="29fb8-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="29fb8-128">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Collection.sln.</span><span class="sxs-lookup"><span data-stu-id="29fb8-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Collection.sln solution file.</span></span>  
  
2.  <span data-ttu-id="29fb8-129">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="29fb8-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="29fb8-130">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="29fb8-130">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29fb8-131">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="29fb8-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29fb8-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="29fb8-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29fb8-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="29fb8-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29fb8-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="29fb8-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`