---
title: Usando Interoperabilidade com troca de dados externo
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 9571a571137ff0a493be67ee9c607cd46dd47889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-interop-with-external-data-exchange"></a>Usando Interoperabilidade com troca de dados externo
O <xref:System.Activities.Statements.Interop> atividade pode ser usada para executar atividades do Windows Workflow Foundation (WF) no [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] e [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) e fluxos de trabalho no Windows Workflow Foundation no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). Este exemplo mostra como configurar e executar um fluxo de trabalho WF3 que usa <xref:System.Workflow.Activities.ExternalDataExchangeService> (e atividades personalizados correspondentes para chamar métodos e manipular eventos) usando a atividade de <xref:System.Activities.Statements.Interop> em um serviço de fluxo de trabalho WF4.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra o arquivo de ExternalDataExchange.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar o exemplo, pressione CTRL+SHIFT+B.  
  
3.  Para executar o exemplo, pressione F5.
