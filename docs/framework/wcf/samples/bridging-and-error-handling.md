---
title: Tratamento de erro e ponte
ms.date: 03/30/2017
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
ms.openlocfilehash: 6afaddc75855b7e95ad708b2179cabb9aee35001
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514536"
---
# <a name="bridging-and-error-handling"></a>Tratamento de erro e ponte
Este exemplo demonstra como o serviço de roteamento do Windows Communication Foundation (WCF) é usado para a ponte de comunicação entre um cliente e um serviço que usam ligações diferentes. Este exemplo também mostra como usar um serviço de backup para cenários de failover. O serviço de roteamento é um componente do WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta a amostragem de calculadora padrão do WCF para se comunicar usando o serviço de roteamento.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Neste exemplo, o cliente de calculadora é configurado para enviar mensagens para um ponto de extremidade exposto pelo roteador. O serviço de roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-las a um ponto de extremidade que corresponde ao serviço de calculadora. Os pontos a seguir descrevem a configuração do serviço da Calculadora primário, o serviço da Calculadora de backup e o cliente de Calculadora e como a comunicação entre o cliente e o serviço ocorre usando o serviço de roteamento:  
  
-   O cliente de calculadora é configurado para usar BasicHttpBinding, enquanto o serviço da calculadora é configurado para usar a NetTcpBinding. O serviço de roteamento converte automaticamente as mensagens conforme necessário antes de enviá-los para o serviço da Calculadora e também converte as respostas para que o cliente de calculadora possa acessá-los.  
  
-   O serviço de roteamento sabe sobre os dois serviços de Calculadora: o serviço da Calculadora primário e o serviço de Calculadora de backup. O serviço de roteamento primeiro tenta se comunicar com o principal ponto de extremidade de serviço de calculadora. Se essa tentativa falhar porque o ponto de extremidade que está sendo pressionada, o serviço de roteamento, em seguida, tenta se comunicar com o ponto de extremidade de serviço de Calculadora de backup.  
  
 Assim, as mensagens enviadas do cliente são recebidas pelo roteador e são redirecionadas para o serviço da Calculadora real. Se o ponto de extremidade de serviço de Calculadora estiver inativo, o serviço de roteamento encaminha a mensagem para o ponto de extremidade de serviço de Calculadora de backup. Mensagens do serviço de Calculadora de backup são enviadas de volta para o roteador de serviço, que por sua vez passa de volta para o cliente de calculadora.  
  
> [!NOTE]
>  Uma lista de backup pode ter mais de um ponto de extremidade definido. Nesse caso, se o ponto de extremidade de serviço de backup estiver inativo, o serviço de roteamento tenta conectar-se para o próximo ponto de extremidade de backup na lista até que ocorra uma conexão bem-sucedida.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra RouterBridgingAndErrorHandling.sln.  
  
2.  Pressione F5 ou CTRL + SHIFT + B no Visual Studio  
  
    1.  Se você quiser iniciar automaticamente os projetos necessários quando você pressiona F5, clique com botão direito a solução, selecione **propriedades**e, nas **projeto de inicialização** nó sob **depropriedadescomuns**, selecione **vários projetos de inicialização**e defina todos os projetos para **iniciar**.  
  
    2.  Se você compilar o projeto com CTRL + SHIFT + B, inicie os seguintes aplicativos:  
  
        1.  Cliente de Calculadora (. / CalculatorClient/bin/client.exe)  
  
        2.  Serviço da Calculadora (. / CalculatorService/bin/service.exe)  
  
        3.  Serviço de roteamento (. / RoutingService/bin/RoutingService.exe)  
  
3.  No cliente de Calculadora, pressione ENTER para iniciar o cliente.  
  
     Você deverá ver a seguinte saída:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurável por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo App. config para algo diferente para que ele não é reconhecido e remova a chamada de método para `ConfigureRouterViaCode()`. Qualquer um dos métodos resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador de serviço que atua como um manipulador de erro e ponte de protocolo. Nesse cenário, nenhuma roteamento baseado em conteúdo ocorre; o serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto predefinido de pontos de extremidade de destino. O serviço de roteamento também executa as etapas adicionais de forma transparente de tratamento de erros que ocorrem quando ele tenta enviar para os pontos de extremidade que ele está configurado para se comunicar com. Atuando como uma ponte de protocolo, o serviço de roteamento permite que o usuário defina um protocolo de comunicação externa e outro para a comunicação interna.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja fornecer um ponto de extremidade de serviço interoperável com o mundo, otimizando o desempenho internamente. Assim, ele expõe seus serviços para o mundo por meio de um ponto de extremidade usando o BasicHttpBinding, enquanto usa internamente o serviço de roteamento para acabar com essa conexão ao ponto de extremidade usando NetTcpBinding, que usam seus serviços. Além disso, a Contoso deseja que sua oferta de serviço para ser tolerante a falhas de interrupções temporárias em qualquer uma de sua produção de serviços e, portanto, virtualiza vários pontos de extremidade por trás do serviço de roteador usando o de recursos para o failover automaticamente para o tratamento de erros fazer backup os pontos de extremidade quando necessário.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
