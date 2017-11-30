---
title: Carregamento XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ca5f830e666ad65ca2162ffd1abb03ce9beca387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="load-from-xaml"></a><span data-ttu-id="5f623-102">Carregamento XAML</span><span class="sxs-lookup"><span data-stu-id="5f623-102">Load From XAML</span></span>
<span data-ttu-id="5f623-103">Este exemplo demonstra como carregar dinamicamente um fluxo de trabalho XAML sem ter que execute a ferramenta de XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="5f623-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="5f623-104">Em vez disso, o exemplo chama o método de <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="5f623-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="5f623-105">O exemplo é um aplicativo cliente de [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] que carrega fluxos de trabalho XAML usando a classe de <xref:System.Activities.XamlIntegration.ActivityXamlServices> e os executar.</span><span class="sxs-lookup"><span data-stu-id="5f623-105">The sample is a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="5f623-106">Depois que foram carregados usando a classe de <xref:System.Activities.XamlIntegration.ActivityXamlServices> , <xref:System.Activities.DynamicActivity%601> é retornado que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="5f623-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5f623-107">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="5f623-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="5f623-108">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="5f623-108">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LoadFromXAML.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5f623-109">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="5f623-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5f623-110">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="5f623-110">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f623-111">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5f623-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f623-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5f623-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5f623-113">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="5f623-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f623-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5f623-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`  
  
## <a name="see-also"></a><span data-ttu-id="5f623-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f623-115">See Also</span></span>
