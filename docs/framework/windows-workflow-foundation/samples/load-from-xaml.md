---
title: Carregamento XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: 2f45beb398e6d6b91bf7444dd590b862ff8c7515
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038079"
---
# <a name="load-from-xaml"></a><span data-ttu-id="e9550-102">Carregamento XAML</span><span class="sxs-lookup"><span data-stu-id="e9550-102">Load From XAML</span></span>
<span data-ttu-id="e9550-103">Este exemplo demonstra como carregar dinamicamente um fluxo de trabalho XAML sem ter que execute a ferramenta de XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="e9550-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="e9550-104">Em vez disso, o exemplo chama o método de <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="e9550-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="e9550-105">O exemplo é um aplicativo cliente Windows Presentation Foundation (WPF) que carrega fluxos de trabalho XAML usando <xref:System.Activities.XamlIntegration.ActivityXamlServices> a classe e os executa.</span><span class="sxs-lookup"><span data-stu-id="e9550-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="e9550-106">Depois que foram carregados usando a classe de <xref:System.Activities.XamlIntegration.ActivityXamlServices> , <xref:System.Activities.DynamicActivity%601> é retornado que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="e9550-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="e9550-107">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="e9550-107">To use this sample</span></span>

1. <span data-ttu-id="e9550-108">Usando o Visual Studio 2010, abra o arquivo de solução LoadFromXAML. sln.</span><span class="sxs-lookup"><span data-stu-id="e9550-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="e9550-109">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e9550-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="e9550-110">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="e9550-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9550-111">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e9550-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e9550-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e9550-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e9550-113">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="e9550-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e9550-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e9550-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
