---
title: Serviço de roteador de descoberta
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183724"
---
# <a name="discovery-router-service"></a>Serviço de roteador de descoberta
Esta amostra demonstra como encaminhar mensagens de descoberta para outro ponto final.  
  
## <a name="demonstrates"></a>Demonstra  
 Roteamento de descobertas  
  
## <a name="discussion"></a>Discussão  
 O roteamento de descobertas é útil em um cenário no qual um cliente está procurando um serviço usando um proxy e o proxy desconhece tal serviço, mas sabe de outro proxy. Este proxy pode encaminhar o pacote de detecção deste cliente para o segundo proxy. O segundo proxy pode procurar o serviço e retornar as respostas ao cliente original.  
  
 Nesta amostra, um cliente envia uma mensagem para um componente de roteamento de descobertas. Esta mensagem é enviada para um ponto final específico no roteador de descobertas. Em seguida, o roteador encaminha a mensagem para um ponto final multicast UDP. A mensagem do teste vai para o ponto final de multicast e um serviço ouvindo em um endereço multicast UDP responde a esse roteador de detecção. O roteador de descoberta coleta as respostas e as envia de volta para o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Compile o exemplo.  
  
2. Execute o executável DiscoveryRouter.  
  
3. Execute o executável de serviço a partir do diretório de compilação.  
  
4. Execute o cliente executável. Observe que o cliente localiza o serviço.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
