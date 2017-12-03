---
title: "Reconfiguração dinâmica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3146da86dcbe22f72ebedec57c87ac0a29ed1946
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-reconfiguration"></a>Reconfiguração dinâmica
Este exemplo demonstra o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] o serviço de roteamento. O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculadora de exemplo para se comunicar usando o serviço de roteamento. Este exemplo mostra como o serviço de roteamento pode ser reconfigurado dinamicamente em tempo de execução.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Para reconfigurar o serviço de roteamento dinamicamente em tempo de execução, este exemplo aciona um timer cada cinco segundos que cria um novo <xref:System.ServiceModel.Routing.RoutingConfiguration> do objeto e o aplica. Essa configuração faz referência o ponto de extremidade de calculadora regular ou o ponto de extremidade de arredondamento Calculadora. O aplicativo cliente de calculadora tem suas mensagens retornadas de um serviço ou a outra, dependendo do que o serviço de roteamento está configurado para direcionar para nesse momento.  
  
 Capabilitiy do serviço de roteamento de reconfiguração dinâmica por meio de um comportamento personalizado é usado. Este comportamento personalizado anexa uma extensão de serviço, que contém um timer de segmento simples que é acionado a cada cinco segundos, o que resulta em um retorno de chamada para o `UpdateRules` método. Esse retorno de chamada cria e aplica-se a nova configuração de roteamento. Em uma implantação real, esse retorno de chamada provavelmente seria obtido como resultado de algum outro tipo de evento, como uma notificação de evento do SQL ou um anúncio de WS-Discovery.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra DynamicReconfiguration.sln.  
  
2.  Para abrir **Solution Explorer**, selecione **Solution Explorer** do **exibição** menu.  
  
3.  Pressione **F5** ou **CTRL + SHIFT + B** em [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Se você gostaria de iniciar os projetos necessários quando você pressiona **F5**, a solução e selecione **propriedades**. Selecione o **projeto de inicialização** nó **propriedades comuns** no painel esquerdo. Selecione o **vários projetos de inicialização** botão de opção e defina todos os projetos para que o **iniciar** ação.  
  
    2.  Se você compilar o projeto com **CTRL + SHIFT + B**, você deve iniciar os seguintes aplicativos:  
  
        1.  Calculadora de cliente (. / CalculatorClient/bin/client.exe)  
  
        2.  Serviço de cálculo (. / CalculatorService/bin/service.exe)  
  
        3.  O serviço de roteamento Calculadora (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Na janela do console do cliente Calculadora, pressione ENTER para iniciar o cliente e chamar as operações de serviço da Calculadora.  
  
     O serviço de roteamento encaminha mensagens para o cálculo de arredondamento e a Calculadora regular alternadamente como as alterações de configuração de roteamento dinamicamente a cada cinco segundos. Dependendo de qual ponto de extremidade do serviço de roteamento está configurado para enviar mensagens para existem saídas diferentes na janela do console do cliente.  
  
5.  Continue a pressionar ENTER repetidamente durante mais de cinco segundos e observe a alteração nos resultados do serviço.  
  
    1.  A seguir está que a saída retornada se o serviço de roteador está configurado para rotear mensagens para o serviço de cálculo de arredondamento.  
  
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
  
6.  O serviço de cálculo e o serviço de cálculo de arredondamento também imprimam um log das operações invocado para as janelas do console do respectivos.  
  
7.  Na janela do console de cliente, digite "Sair" e pressione ENTER para sair.  
  
8.  Pressione ENTER nas janelas do console de serviços para encerrar os serviços.  
  
## <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador que atua como um roteador baseado em conteúdo, permitindo que vários tipos ou implementação de serviços a serem expostas por meio de um ponto de extremidade.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja virtualizar todos os seus serviços para expor apenas um ponto de extremidade publicamente por meio do qual eles oferecem acesso a vários tipos diferentes de serviços. Nesse caso, eles utilizam baseado em conteúdo capacidades de roteamento do serviço de roteamento para determinar onde as solicitações de entrada devem ser enviadas.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
