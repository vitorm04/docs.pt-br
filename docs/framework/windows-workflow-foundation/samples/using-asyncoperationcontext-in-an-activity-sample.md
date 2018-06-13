---
title: Usando AsyncOperationContext em um exemplo de atividades
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515491"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Usando AsyncOperationContext em um exemplo de atividades
Este exemplo demonstra como desenvolver um personalizado <xref:System.Activities.CodeActivity> que usa <xref:System.Activities.AsyncCodeActivityContext> para executar o trabalho de forma assíncrona fora de fluxo de trabalho.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Atividade de exemplo usa os métodos de <xref:System.IO.FileStream.BeginWrite%2A> e de <xref:System.IO.FileStream.EndWrite%2A> na classe de <xref:System.IO.FileStream> para gravar dados de forma assíncrona a um arquivo. O padrão introduzido aqui pode ser adaptado para uso com outros métodos assíncronos. Quando a operação assíncrona, executar outras atividades no fluxo de trabalho podem executar, mas o fluxo de trabalho não pode ser persistido.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução de exemplo de Async.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`