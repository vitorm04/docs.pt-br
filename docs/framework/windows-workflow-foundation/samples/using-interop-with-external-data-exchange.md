---
title: Usando Interoperabilidade com troca de dados externo
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 534321e5b5568e0dd0988333dc98ccc18ff33df8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508290"
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="c125b-102">Usando Interoperabilidade com troca de dados externo</span><span class="sxs-lookup"><span data-stu-id="c125b-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="c125b-103">O <xref:System.Activities.Statements.Interop> atividade pode ser usada para executar atividades do Windows Workflow Foundation (WF) no [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] e [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) e fluxos de trabalho no Windows Workflow Foundation no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span><span class="sxs-lookup"><span data-stu-id="c125b-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from Windows Workflow Foundation (WF) in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="c125b-104">Este exemplo mostra como configurar e executar um fluxo de trabalho WF3 que usa <xref:System.Workflow.Activities.ExternalDataExchangeService> (e atividades personalizados correspondentes para chamar métodos e manipular eventos) usando a atividade de <xref:System.Activities.Statements.Interop> em um serviço de fluxo de trabalho WF4.</span><span class="sxs-lookup"><span data-stu-id="c125b-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c125b-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c125b-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c125b-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c125b-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c125b-107">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c125b-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c125b-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c125b-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c125b-109">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="c125b-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="c125b-110">Abra o arquivo de ExternalDataExchange.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c125b-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c125b-111">Para criar o exemplo, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="c125b-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c125b-112">Para executar o exemplo, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="c125b-112">To run the sample, press F5.</span></span>
