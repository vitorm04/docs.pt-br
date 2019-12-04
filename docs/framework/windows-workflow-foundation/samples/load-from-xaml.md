---
title: Carregamento XAML
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715960"
---
# <a name="load-from-xaml"></a><span data-ttu-id="fed06-102">Carregamento XAML</span><span class="sxs-lookup"><span data-stu-id="fed06-102">Load From XAML</span></span>
<span data-ttu-id="fed06-103">Este exemplo demonstra como carregar dinamicamente um fluxo de trabalho XAML sem ter que execute a ferramenta de XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="fed06-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="fed06-104">Em vez disso, o exemplo chama o método de <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="fed06-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="fed06-105">O exemplo é um aplicativo cliente Windows Presentation Foundation (WPF) que carrega fluxos de trabalho XAML usando a classe <xref:System.Activities.XamlIntegration.ActivityXamlServices> e os executa.</span><span class="sxs-lookup"><span data-stu-id="fed06-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="fed06-106">Depois que foram carregados usando a classe de <xref:System.Activities.XamlIntegration.ActivityXamlServices> , <xref:System.Activities.DynamicActivity%601> é retornado que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="fed06-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="fed06-107">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="fed06-107">To use this sample</span></span>

1. <span data-ttu-id="fed06-108">Usando o Visual Studio 2010, abra o arquivo de solução LoadFromXAML. sln.</span><span class="sxs-lookup"><span data-stu-id="fed06-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="fed06-109">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="fed06-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="fed06-110">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="fed06-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fed06-111">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="fed06-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fed06-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fed06-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fed06-113">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="fed06-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fed06-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="fed06-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
