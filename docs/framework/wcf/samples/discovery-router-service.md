---
title: "Serviço de roteador de descoberta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 663ece44a18ae073412376bc11a1d70927740e8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-router-service"></a>Serviço de roteador de descoberta
Este exemplo demonstra como encaminhar mensagens de descoberta para outro ponto de extremidade.  
  
## <a name="demonstrates"></a>Demonstra  
 Roteamento de descoberta  
  
## <a name="discussion"></a>Discussão  
 Roteamento de descoberta é útil em um cenário em que um cliente está procurando por um serviço usando um proxy e o proxy não sabe nada sobre um serviço, mas sabe de outro proxy. Este proxy pode encaminhar o pacote de descoberta desse cliente para o proxy de segundo. O segundo proxy pode procurar o serviço e retornar a resposta para o cliente original.  
  
 Neste exemplo, um cliente envia uma mensagem para um componente de roteamento de descoberta. Esta mensagem é enviada para um ponto de extremidade específico do roteador de descoberta. O roteador encaminha a mensagem para um UDP multicast do ponto de extremidade. A mensagem de teste vai para o ponto de extremidade de multicast e um serviço de escuta em um UDP multicast endereço responde a esse roteador de descoberta. O roteador de descoberta coleta as respostas e as envia ao cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Crie o exemplo.  
  
2.  Execute o executável DiscoveryRouter.  
  
3.  Execute o executável do serviço de diretório de compilação.  
  
4.  Execute o executável do cliente. Observe que o cliente localiza o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
