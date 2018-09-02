---
title: Uso básico de atividades de SendParameters e de ReceiveParameters
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467689"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>Uso básico de atividades de SendParameters e de ReceiveParameters
Este exemplo mostra o uso de <xref:System.ServiceModel.Activities.SendParametersContent> e de atividades de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . O serviço expõe uma operação que recebe um argumento de cadeia de caracteres e ecoa a entrada de volta para o cliente. O exemplo a seguir mostra como configurar parâmetros para essas atividades de mensagem.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Usando este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.  
  
2.  Executa EchoWorkflowService aplicativo gerado em [] do diretório da solução EchoWorkflowService \ \ bin \ debug.  
  
3.  Segundo, executam EchoWorkflowClient aplicativo gerado em [] do diretório da solução EchoWorkflowClient \ \ bin \ debug.  
  
4.  O cliente chama a operação de eco no serviço e imprime os resultados. Quando completo, pressione ENTER para sair do cliente e o serviço.