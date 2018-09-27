---
title: Exemplo de ponto de extremidade de gerenciamento de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 398ace1c198f0db0268c44083ccc98c5ba2d2c7f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399119"
---
# <a name="workflow-management-endpoint-sample"></a>Exemplo de ponto de extremidade de gerenciamento de fluxo de trabalho
Este exemplo mostra como um ponto de extremidade de controle de fluxo de trabalho pode ser usado para criar localmente e remotamente e executar fluxos de trabalho. O exemplo demonstra como hospedar um ponto final do controle e escrever os clientes que chamam o ponto final do controle para criar e executar a instância de um fluxo de trabalho. O fluxo de trabalho não é um serviço.  
  
 No lado de serviço exemplo de um fluxo de trabalho é hospedado com WorkflowServiceHost e um WorkflowControlEndpoint é adicionado de modo que os clientes podem executar operações de controle (suspenda, inicie, etc.). Um CreationEndpoint definido pelo usuário também é adicionado para permitir que o fluxo de trabalho é criado. O serviço usar esses pontos de extremidade para iniciar o fluxo de trabalho em um estado suspensa e para continuar no fluxo de trabalho. O cliente executa as mesmas operações mas de código do cliente. Para obter mais informações sobre essas interfaces, consulte [ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com privilégios de administrador.  
  
2.  Abra a solução de ManagementEndpoint.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** da **Build** menu.  
  
4.  Inicie o aplicativo de ManagementEndpoint.exe.  
  
5.  Inicie o aplicativo de Client.exe.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`