---
title: Atividade de RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207584"
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="abdcd-102">Atividade de RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="abdcd-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="abdcd-103">Este exemplo demonstra como criar uma atividade personalizado que executa iterações sobre uma coleção de números. A tabela a seguir detalha os arquivos de chave incluídos no exemplo.</span><span class="sxs-lookup"><span data-stu-id="abdcd-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="abdcd-104">Nome do arquivo</span><span class="sxs-lookup"><span data-stu-id="abdcd-104">File name</span></span>|<span data-ttu-id="abdcd-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="abdcd-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abdcd-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="abdcd-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="abdcd-107">Define uma atividade personalizada chamada `RangeEnumeration` que substitui a classe e loops de <xref:System.Activities.NativeActivity> com uma série de números.</span><span class="sxs-lookup"><span data-stu-id="abdcd-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="abdcd-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="abdcd-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="abdcd-109">Um aplicativo cliente que usa a atividade de `RangeEnumeration` para iterar sobre uma coleção de números.</span><span class="sxs-lookup"><span data-stu-id="abdcd-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="abdcd-110">A tabela a seguir detalha as propriedades de atividade de `RangeEnumeration` .</span><span class="sxs-lookup"><span data-stu-id="abdcd-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="abdcd-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="abdcd-111">Property</span></span>|<span data-ttu-id="abdcd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="abdcd-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="abdcd-113">Início</span><span class="sxs-lookup"><span data-stu-id="abdcd-113">Start</span></span>|<span data-ttu-id="abdcd-114">O inteiro para iniciar o loop do.</span><span class="sxs-lookup"><span data-stu-id="abdcd-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="abdcd-115">Stop</span><span class="sxs-lookup"><span data-stu-id="abdcd-115">Stop</span></span>|<span data-ttu-id="abdcd-116">O inteiro para parar no loop.</span><span class="sxs-lookup"><span data-stu-id="abdcd-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="abdcd-117">Etapa</span><span class="sxs-lookup"><span data-stu-id="abdcd-117">Step</span></span>|<span data-ttu-id="abdcd-118">Especifica quanto para iterar cada vez.</span><span class="sxs-lookup"><span data-stu-id="abdcd-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="abdcd-119">Corpo</span><span class="sxs-lookup"><span data-stu-id="abdcd-119">Body</span></span>|<span data-ttu-id="abdcd-120">Especifica o código para executar durante cada iteração.</span><span class="sxs-lookup"><span data-stu-id="abdcd-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="abdcd-121">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="abdcd-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="abdcd-122">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="abdcd-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="abdcd-123">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="abdcd-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="abdcd-124">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="abdcd-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="abdcd-125">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="abdcd-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="abdcd-126">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="abdcd-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="abdcd-127">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="abdcd-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="abdcd-128">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="abdcd-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`