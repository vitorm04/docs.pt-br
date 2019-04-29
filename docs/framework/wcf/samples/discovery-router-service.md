---
title: Serviço de roteador de descoberta
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 166f6b9d1055e36f987e6b9a81fe69dc8bd548b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773029"
---
# <a name="discovery-router-service"></a>Serviço de roteador de descoberta
Este exemplo demonstra como encaminhar mensagens para outro ponto de extremidade de descoberta.  
  
## <a name="demonstrates"></a>Demonstra  
 Roteamento de descoberta  
  
## <a name="discussion"></a>Discussão  
 O roteamento de descoberta é útil em um cenário em que um cliente está procurando por um serviço usando um proxy e o proxy não tem conhecimento de um serviço como esse, mas sabe de outro proxy. Esse proxy pode encaminhar o pacote de descoberta deste cliente para o proxy do segundo. O proxy do segundo pode procurar o serviço e retornar as respostas ao cliente original.  
  
 Neste exemplo, um cliente envia uma mensagem a um componente de roteamento de descoberta. Esta mensagem é enviada para um ponto de extremidade específico do roteador de descoberta. O roteador encaminha a mensagem para um UDP multicast do ponto de extremidade. A mensagem de teste vai para o ponto de extremidade de multicast e um serviço escutando em um UDP multicast endereço responde a esse roteador de descoberta. O roteador de descoberta coleta as respostas e as envia ao cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Crie o exemplo.  
  
2. Execute o executável DiscoveryRouter.  
  
3. Execute o executável do serviço de diretório de compilação.  
  
4. Execute o executável do cliente. Observe que o cliente localiza o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
