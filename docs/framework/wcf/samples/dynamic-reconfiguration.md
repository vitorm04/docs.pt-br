---
title: Reconfiguração dinâmica
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537456"
---
# <a name="dynamic-reconfiguration"></a>Reconfiguração dinâmica
Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF). O serviço de roteamento é um componente do WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta a amostragem de calculadora padrão do WCF para se comunicar usando o serviço de roteamento. Este exemplo mostra como o serviço de roteamento pode ser reconfigurado dinamicamente durante o tempo de execução.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Para reconfigurar o serviço de roteamento dinamicamente durante o tempo de execução, este exemplo é acionado a cada cinco segundos um temporizador que cria um novo <xref:System.ServiceModel.Routing.RoutingConfiguration> do objeto e o aplica. Essa configuração faz referência o ponto de extremidade de calculadora regular ou o ponto de extremidade de Calculadora de arredondamento. O aplicativo cliente de calculadora tem suas mensagens retornadas de um serviço ou outro, dependendo de qual o serviço de roteamento está configurado para rotear para nesse momento.  
  
 Recurso do serviço de roteamento para reconfiguração dinâmica por meio de um comportamento personalizado é usado. Este comportamento personalizado anexa uma extensão de serviço, que contém um temporizador de thread simples que é acionado a cada cinco segundos, o que resulta em um retorno de chamada para o `UpdateRules` método. Esse retorno de chamada cria e aplica-se a nova configuração de roteamento. Em uma implantação real, esse retorno de chamada provavelmente seria obtido como resultado de algum outro tipo de evento, como uma notificação de evento do SQL ou um anúncio de WS-Discovery.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra DynamicReconfiguration.sln.  
  
2.  Para abrir **Gerenciador de soluções**, selecione **Gerenciador de soluções** do **exibição** menu.  
  
3.  Pressione **F5** ou **CTRL + SHIFT + B** no Visual Studio.  
  
    1.  Se você deseja iniciar automaticamente os projetos necessários quando você pressiona **F5**, a solução com o botão direito e selecione **propriedades**. Selecione o **projeto de inicialização** nó sob **propriedades comuns** no painel esquerdo. Selecione o **vários projetos de inicialização** botão de opção e defina todos os projetos para que o **iniciar** ação.  
  
    2.  Se você compilar o projeto com **CTRL + SHIFT + B**, você deve iniciar os seguintes aplicativos:  
  
        1.  Calculadora de cliente (. / CalculatorClient/bin/client.exe)  
  
        2.  Serviço da Calculadora (. / CalculatorService/bin/service.exe)  
  
        3.  Serviço de roteamento de Calculadora (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Na janela do console do cliente da Calculadora, pressione ENTER para iniciar o cliente e chamar as operações de serviço da Calculadora.  
  
     O serviço de roteamento encaminha mensagens para a Calculadora de arredondamento e a Calculadora regular como alternativa, como as alterações de configuração de roteamento dinamicamente a cada cinco segundos. Dependendo de qual ponto de extremidade que o serviço de roteamento é configurado para enviar mensagens para há saídas diferentes na janela do console de cliente.  
  
5.  Continue a pressionar ENTER repetidamente ao longo de mais de cinco segundos e observe a alteração nos resultados do serviço.  
  
    1.  A seguir está que a saída retornada se o serviço de roteador está configurado para rotear mensagens para o serviço da Calculadora de arredondamento.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  A seguir está que a saída retornada se o serviço de roteamento está configurado para rotear mensagens para o serviço da Calculadora regular.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  O serviço da Calculadora e o serviço da Calculadora arredondamento também imprimam um log das operações invocado para as janelas de console respectivo.  
  
7.  Na janela do console de cliente, digite "quit" e pressione ENTER para sair.  
  
8.  Pressione ENTER nas janelas do console de serviços para encerrar os serviços.  
  
## <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador que atua como um roteador baseado em conteúdo, permitindo que vários tipos ou implementação de serviços a serem expostos por meio de um ponto de extremidade.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja virtualizar todos os seus serviços para expor somente um ponto de extremidade publicamente por meio dos quais eles oferecem acesso a vários tipos diferentes de serviços. Nesse caso, eles utilizam baseado em conteúdo recursos de roteamento do serviço de roteamento para determinar onde as solicitações de entrada devem ser enviadas.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
