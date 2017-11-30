---
title: Atividade de RangeEnumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35bff923b0e8d6fe7c01cb7970c7b6ee46488a43
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="72b56-102">Atividade de RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="72b56-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="72b56-103">Este exemplo demonstra como criar uma atividade personalizado que executa iterações sobre uma coleção de números. A tabela a seguir detalha os arquivos de chave incluídos no exemplo.</span><span class="sxs-lookup"><span data-stu-id="72b56-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="72b56-104">Nome do arquivo</span><span class="sxs-lookup"><span data-stu-id="72b56-104">File name</span></span>|<span data-ttu-id="72b56-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="72b56-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72b56-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="72b56-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="72b56-107">Define uma atividade personalizada chamada `RangeEnumeration` que substitui a classe e loops de <xref:System.Activities.NativeActivity> com uma série de números.</span><span class="sxs-lookup"><span data-stu-id="72b56-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="72b56-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="72b56-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="72b56-109">Um aplicativo cliente que usa a atividade de `RangeEnumeration` para iterar sobre uma coleção de números.</span><span class="sxs-lookup"><span data-stu-id="72b56-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="72b56-110">A tabela a seguir detalha as propriedades de atividade de `RangeEnumeration` .</span><span class="sxs-lookup"><span data-stu-id="72b56-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="72b56-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="72b56-111">Property</span></span>|<span data-ttu-id="72b56-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="72b56-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="72b56-113">Início</span><span class="sxs-lookup"><span data-stu-id="72b56-113">Start</span></span>|<span data-ttu-id="72b56-114">O inteiro para iniciar o loop do.</span><span class="sxs-lookup"><span data-stu-id="72b56-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="72b56-115">Stop</span><span class="sxs-lookup"><span data-stu-id="72b56-115">Stop</span></span>|<span data-ttu-id="72b56-116">O inteiro para parar no loop.</span><span class="sxs-lookup"><span data-stu-id="72b56-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="72b56-117">Etapa</span><span class="sxs-lookup"><span data-stu-id="72b56-117">Step</span></span>|<span data-ttu-id="72b56-118">Especifica quanto para iterar cada vez.</span><span class="sxs-lookup"><span data-stu-id="72b56-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="72b56-119">Corpo</span><span class="sxs-lookup"><span data-stu-id="72b56-119">Body</span></span>|<span data-ttu-id="72b56-120">Especifica o código para executar durante cada iteração.</span><span class="sxs-lookup"><span data-stu-id="72b56-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="72b56-121">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="72b56-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="72b56-122">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="72b56-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="72b56-123">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="72b56-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="72b56-124">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="72b56-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="72b56-125">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="72b56-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="72b56-126">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="72b56-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="72b56-127">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="72b56-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="72b56-128">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="72b56-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`