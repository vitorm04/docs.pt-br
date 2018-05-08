---
title: Olá Mundo com o serviço de roteamento
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 88b7cdb9beabd8e4ff5ffc9a1c31a702a3cb4f02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="hello-world-with-the-routing-service"></a>Olá Mundo com o serviço de roteamento
Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF). O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculadora de exemplo para se comunicar usando o serviço de roteamento. Neste exemplo, o cliente de cálculo é configurado para enviar mensagens a um ponto de extremidade exposto pelo roteador. O serviço de roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-los para um ponto de extremidade que corresponde ao serviço de cálculo. Assim mensagens enviadas do cliente são recebidas pelo roteador e roteadas para o serviço da Calculadora real. Mensagens do serviço de cálculo são enviadas para o roteador, que por sua vez passa de volta para o cliente de cálculo.  
  
### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra HelloRoutingService.sln.  
  
2.  Pressione F5 ou CTRL + SHIFT + B.  
  
    > [!NOTE]
    >  Se você pressionar F5, o cliente de cálculo é iniciado automaticamente. Se você pressionar CTRL + SHIFT + B (compilação), você deve iniciar a seguir aplicativos por conta própria.  
    >   
    >  1.  Cliente de cálculo (./CalculatorClient/bin/client.exe  
    > 2.  Serviço de cálculo (. / CalculatorService/bin/service.exe)  
    > 3.  O serviço de roteamento (. / RoutingService/bin/RoutingService.exe)  
  
3.  Pressione ENTER para iniciar o cliente.  
  
     Você deverá ver a seguinte saída:  
  
     Add(100,15.99) = 115.99  
  
     Subtract(145,76.54) = 68.46  
  
     MULTIPLY(9,81.25) = 731.25  
  
     Divide(22,7) = 3.14285714285714  
  
## <a name="configurable-via-code-or-appconfig"></a>Configuráveis por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo App. config para algo diferente para que ele não é reconhecido e remova a chamada de método para ConfigureRouterViaCode(). Um método resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador que atua como uma bomba de mensagem básica. O serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto predefinido de pontos de extremidade de destino.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja aumentar a flexibilidade que ele tem na nomenclatura, endereçamento, configuração e segurança de seus serviços. Para fazer isso, eles fizerem uma bomba de mensagem básica na frente de seus serviços para atuar como um ponto de extremidade oposto público. Isso permite colocar segurança adicional na frente de seus serviços reais e torná-lo mais fácil de implementar expandida soluções ou controle de versão do serviço em uma data posterior.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
