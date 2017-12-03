---
title: Tratamento de erro e ponte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc809b75a965107594f7b2aa8a78d412bf284d8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="bridging-and-error-handling"></a>Tratamento de erro e ponte
Este exemplo demonstra como o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] o serviço de roteamento é usado para a ponte de comunicação entre um cliente e um serviço que usam ligações diferentes. Este exemplo também mostra como usar um serviço de backup para cenários de failover. O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculadora de exemplo para se comunicar usando o serviço de roteamento.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Neste exemplo, o cliente de cálculo é configurado para enviar mensagens a um ponto de extremidade exposto pelo roteador. O serviço de roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-los para um ponto de extremidade que corresponde ao serviço de cálculo. Os pontos a seguir descrevem a configuração do serviço Calculadora primário, o serviço de cálculo de backup e o cliente de cálculo e como ocorre a comunicação entre o cliente e o serviço usando o serviço de roteamento:  
  
-   O cliente de cálculo é configurado para usar BasicHttpBinding enquanto o serviço de cálculo é configurado para usar NetTcpBinding. O serviço de roteamento converte automaticamente as mensagens conforme necessário antes de enviá-los para o serviço de cálculo e também converte as respostas para que o cliente de cálculo pode acessá-los.  
  
-   O serviço de roteamento conhece os dois serviços de cálculo: o serviço de calculadora primário e o serviço de cálculo do backup. O serviço de roteamento primeiro tenta se comunicar com o ponto de extremidade de serviço principal Calculadora. Se essa tentativa falhar porque o ponto de extremidade está inativo, o serviço de roteamento, em seguida, tenta se comunicar com o ponto de extremidade do serviço de cálculo do backup.  
  
 Portanto, as mensagens enviadas do cliente são recebidas pelo roteador e são redirecionadas para o serviço de cálculo real. Se o ponto de extremidade de serviço de Calculadora estiver inativo, o serviço de roteamento encaminha a mensagem para o ponto de extremidade do serviço de cálculo do backup. Mensagens do serviço de cálculo do backup são enviadas para o roteador do serviço, que por sua vez passa de volta para o cliente de cálculo.  
  
> [!NOTE]
>  Uma lista de backup pode ter mais de um ponto de extremidade definido. Nesse caso se o ponto de extremidade de serviço de backup estiver inativo, o serviço de roteamento tenta se conectar ao próximo ponto de extremidade de backup na lista até que ocorra uma conexão bem-sucedida.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra RouterBridgingAndErrorHandling.sln.  
  
2.  Pressione F5 ou CTRL + SHIFT + B no Visual Studio  
  
    1.  Se você quiser iniciar os projetos necessários quando você pressionar F5, clique duas vezes a solução, selecione **propriedades**e no **projeto de inicialização** nó **aspropriedadescomuns**, selecione **vários projetos de inicialização**e defina todos os projetos para **iniciar**.  
  
    2.  Se você compilar o projeto com CTRL + SHIFT + B, inicie os seguintes aplicativos:  
  
        1.  Cliente de cálculo (. / CalculatorClient/bin/client.exe)  
  
        2.  Serviço de cálculo (. / CalculatorService/bin/service.exe)  
  
        3.  O serviço de roteamento (. / RoutingService/bin/RoutingService.exe)  
  
3.  No cliente de cálculo, pressione ENTER para iniciar o cliente.  
  
     Você verá a seguinte saída:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configuráveis por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo App. config para algo diferente para que ele não é reconhecido e remova a chamada de método para `ConfigureRouterViaCode()`. Um método resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador de serviço, agindo como um manipulador de protocolo de ponte e o erro. Nesse cenário, nenhum roteamento baseado em conteúdo ocorre; o serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto predefinido de pontos de extremidade de destino. O serviço de roteamento também executa as etapas adicionais de forma transparente a manipulação de erros que ocorrem quando ele tenta enviar para os pontos de extremidade que ele está configurado para se comunicar com. Agindo como uma ponte de protocolo, o serviço de roteamento permite que o usuário defina um protocolo para comunicação externa e outro para comunicação interna.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja fornecer um ponto de extremidade de serviço interoperável com o mundo, ao otimizar o desempenho internamente. Assim, ele expõe seus serviços para o mundo por meio de um ponto de extremidade usando o BasicHttpBinding internamente usando o serviço de roteamento para acabar com essa conexão ao ponto de extremidade usando NetTcpBinding, que usam seus serviços. Além disso, a Contoso deseja sua oferta de serviço para ser tolerante a falhas de interrupções temporárias em qualquer uma das sua produção serviços e virtualiza, portanto, vários pontos de extremidade por trás do serviço de roteador usando o de recursos automaticamente o failover para o tratamento de erros extremidade de backup quando necessário.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
