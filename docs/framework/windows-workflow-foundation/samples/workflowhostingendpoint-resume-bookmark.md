---
title: Indexador de resumo de WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3af31af17e0c362beb8ba4b9b0479de59cab8ef3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515669"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Indexador de resumo de WorkflowHostingEndpoint
Este exemplo demonstra como <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pode ser usado com <xref:System.ServiceModel.Activities.WorkflowServiceHost> para criar instâncias de fluxo de trabalho.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Discussão  
 Este exemplo usa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para criar uma instância de fluxo de trabalho hospedada usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> é um ponto de extensibilidade para <xref:System.ServiceModel.Activities.WorkflowServiceHost> que pode ser usada nos seguintes situações:  
  
-   Criando novas instâncias de fluxo de trabalho.  
  
-   Continuando indicadores em uma instância de fluxo de trabalho hospedada em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 O ponto final de exemplo que é expõe incluídas o contrato que fornece operações para criar um fluxo de trabalho e retornar um ID de instância, ou para criar uma instância com uma identificação específica O aplicativo de console do exemplo cria uma instância de <xref:System.ServiceModel.Activities.WorkflowServiceHost> com uma definição básica de fluxo de trabalho, e adicione `CreationEndpoint` para o host. Então chama a operação de `Create` no ponto de extremidade para criar uma nova instância de fluxo de trabalho.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Compile a solução.  
  
2.  Execute o aplicativo. O console de `CreationEndpoint` mostra uma mensagem que inclui a ID da instância quando a instância do fluxo de trabalho é criada. A mensagem "Hello World!" é impressa pelo fluxo de trabalho na retomada bem-sucedida do indicador.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
