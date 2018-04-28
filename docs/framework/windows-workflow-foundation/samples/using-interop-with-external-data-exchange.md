---
title: Usando Interoperabilidade com troca de dados externo
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4acec4209ddadd181774ae754cb1d6b94a21685e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="458e8-102">Usando Interoperabilidade com troca de dados externo</span><span class="sxs-lookup"><span data-stu-id="458e8-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="458e8-103">O <xref:System.Activities.Statements.Interop> atividade pode ser usada para executar atividades do Windows Workflow Foundation (WF) no [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] e [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) e fluxos de trabalho no Windows Workflow Foundation no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span><span class="sxs-lookup"><span data-stu-id="458e8-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from Windows Workflow Foundation (WF) in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="458e8-104">Este exemplo mostra como configurar e executar um fluxo de trabalho WF3 que usa <xref:System.Workflow.Activities.ExternalDataExchangeService> (e atividades personalizados correspondentes para chamar métodos e manipular eventos) usando a atividade de <xref:System.Activities.Statements.Interop> em um serviço de fluxo de trabalho WF4.</span><span class="sxs-lookup"><span data-stu-id="458e8-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="458e8-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="458e8-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="458e8-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="458e8-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="458e8-107">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="458e8-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="458e8-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="458e8-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="458e8-109">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="458e8-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="458e8-110">Abra o arquivo de ExternalDataExchange.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="458e8-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="458e8-111">Para criar o exemplo, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="458e8-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="458e8-112">Para executar o exemplo, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="458e8-112">To run the sample, press F5.</span></span>
