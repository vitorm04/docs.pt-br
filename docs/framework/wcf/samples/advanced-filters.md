---
title: "Filtros avançados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 988c41bb691d27e819710bbc2cd48bc1c844e7c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-filters"></a>Filtros avançados
Este exemplo demonstra um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] o serviço de roteamento. O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplo de cálculo para se comunicar usando o serviço de roteamento. Este exemplo mostra como definir a lógica de roteamento baseado em conteúdo com o uso de filtros de mensagem e tabelas de filtro de mensagem.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A tabela a seguir mostra os filtros de mensagem que são adicionados à tabela de filtro de mensagem do serviço de roteamento.  
  
|Filtro|Regra|Prioridade|  
|------------|----------|--------------|  
|Se (tem cabeçalho)|Arredondamento|2|  
|Se (apareceram na Ep2)|Normal|1|  
|Se (aparecia com endereço2)|Arredondamento|1|  
|Se (RoundRobin1)|Normal|0|  
|Se (RoundRobin2)|Arredondamento|0|  
  
 As tabelas de filtro de mensagem e filtros de mensagem podem ser criadas e configuradas por meio de código ou no arquivo de configuração do aplicativo. Para este exemplo, você pode encontrar as tabelas de filtro de mensagem definidas por meio de código no arquivo RoutingService\routing.cs ou definidas no arquivo de configuração do aplicativo no arquivo RoutingService\App.config e filtros de mensagem. Os parágrafos a seguir descrevem como as tabelas de filtro de mensagem e filtros de mensagem são criadas para este exemplo de código.  
  
 Primeiro, um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> procura o cabeçalho personalizado. Observe que <xref:System.ServiceModel.WSHttpBinding> resulta em uma versão de envelope usando SOAP 1.2, portanto, a instrução XPath é definida para usar o namespace de SOAP 1.2. O Gerenciador de namespace padrão para <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s já define um prefixo para o namespace de SOAP 1.2, /s12, que pode ser usado. No entanto, o Gerenciador de namespace padrão não tem o namespace personalizado que o cliente usa para definir o valor real do cabeçalho, portanto esse prefixo deve ser definido. Qualquer mensagem que aparece com esse cabeçalho corresponde a este filtro.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 O segundo filtro for um <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, que corresponde a qualquer mensagem que foi recebida o `calculatorEndpoint`. O nome do ponto de extremidade é definido quando um objeto de ponto de extremidade de serviço é criado.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 O terceiro filtro é um <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. Isso corresponde a qualquer mensagem que aparecem em um ponto de extremidade com um endereço que corresponde ao prefixo do endereço (ou a parte frontal) fornecido. Neste exemplo, o prefixo de endereço é definido como "http://localhost/routingservice/router/rounding/". Isso significa que as mensagens de entrada que são endereçadas para "http://localhost/routingservice/router/rounding/ *" correspondem a este filtro. Nesse caso, é mensagens que aparecem no ponto de extremidade de arredondamento cálculo, que tem o endereço de "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Os dois últimos filtros de mensagem são personalizados <xref:System.ServiceModel.Dispatcher.MessageFilter>s. Neste exemplo, um filtro de mensagem "RoundRobin" é usado. Esse filtro de mensagem é criado no arquivo RoutingService\RoundRobinMessageFilter.cs fornecido. Esses filtros, quando definidos para o mesmo grupo, alternam entre relatórios se eles correspondem a mensagem e que eles não, de modo que apenas um deles responde `true` por vez.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Em seguida, todas as mensagens são adicionadas a um <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Dessa forma, as prioridades são especificadas para influenciar a ordem na qual a tabela de filtro de mensagem executa os filtros. Quanto maior a prioridade, mais cedo que o filtro é executado; Quanto menor a prioridade, depois de um filtro é executado. Assim, um filtro com prioridade 2 é executado antes de um filtro com prioridade 1. O nível de prioridade padrão se nenhum for especificado é 0. Uma tabela de filtro de mensagem executa todos os filtros em um nível de prioridade determinada antes de passar para o próximo nível de prioridade mais baixo. Se uma correspondência for encontrada em uma prioridade específica, em seguida, a tabela de filtro de mensagem não continue tentando localizar correspondências com a próxima prioridade inferior.  
  
> [!NOTE]
>  Embora este exemplo mostra como usar as prioridades de filtro de mensagem, em geral é mais funcionais e melhor design para design e configurar seus filtros de modo que eles não exigem priorização funcione corretamente.  
  
 O primeiro filtro a ser adicionado é o filtro XPath e sua prioridade é definida como 2. Este é o primeiro filtro de mensagem que é executado. Se ele encontrar o cabeçalho personalizado, independentemente do que os resultados dos outros filtros seriam, a mensagem é roteada para o ponto de extremidade de arredondamento Calculadora.  
  
 Com prioridade 1, os dois filtros são adicionados. Novamente, esses executado somente se o filtro XPath com prioridade 2 não coincide com a mensagem. Esses dois filtros mostram dois modos diferentes para determinar onde a mensagem foi tratada quando ele aparecia. Como os dois filtros efetivamente verificam para ver se a mensagem chegou em um dos dois pontos de extremidade, eles podem ser executados no mesmo nível de prioridade porque eles são não ambos retornam `true` ao mesmo tempo.  
  
 Por fim, com prioridade 0 (prioridade mais baixa), execute o RoundRobin mensagem filtros. Como os filtros são configurados com o mesmo nome de grupo, somente um deles corresponde a cada vez. Como todas as mensagens com o cabeçalho personalizado tem sido roteadas e todos os resolvidos para os pontos de extremidade específicos virtualizados, mensagens tratadas por filtros de mensagem RoundRobin são apenas as mensagens que foram resolvidas para o ponto de extremidade de roteador padrão sem personalizado cabeçalho. Como alternar essas mensagens em uma mensagem para cada chamada, metade das operações de ir para o ponto de extremidade de calculadora Regular e a outra metade, vá para o ponto de extremidade de arredondamento Calculadora.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra AdvancedFilters.sln.  
  
2.  Para abrir **Solution Explorer**, selecione **Solution Explorer** do **exibição** menu.  
  
3.  Pressione F5 ou CTRL + SHIFT + B no [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Se você quiser iniciar os projetos necessários quando você pressionar F5, a solução e selecione **propriedades**. Selecione o **projeto de inicialização** nó **propriedades comuns** no painel esquerdo. Selecione o **vários projetos de inicialização** botão de opção e defina todos os projetos para que o **iniciar** ação.  
  
    2.  Se você compilar o projeto com CTRL + SHIFT + B, inicie os seguintes aplicativos:  
  
        1.  Calculadora de cliente (. / CalculatorClient/bin/client.exe)  
  
        2.  Serviço de cálculo (. / CalculatorService/bin/service.exe)  
  
        3.  O serviço de roteamento Calculadora (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Na janela do console do cliente Calculadora, pressione ENTER para iniciar o cliente. O cliente retorna uma lista de pontos de extremidade de destino à sua escolha.  
  
5.  Escolha um ponto de extremidade de destino, digitando seu letra correspondente e pressione ENTER.  
  
6.  Em seguida, o cliente solicita se você deseja adicionar um cabeçalho personalizado. Pressione s para Sim ou N para não e, em seguida, pressione ENTER.  
  
7.  Dependendo das seleções feitas, você deve ver resultados diferentes.  
  
    1.  A seguir está que a saída retornada se você adicionou um cabeçalho personalizado para as mensagens.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  A seguir está que a saída retornada se você escolher o ponto de extremidade de arredondamento Calculadora sem um cabeçalho personalizado.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  A seguir está que a saída retornada se você escolher o ponto de extremidade de calculadora regulares sem um cabeçalho personalizado.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  A seguir está que a saída retornada se você escolher o ponto de extremidade de roteador padrão sem um cabeçalho personalizado.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  O serviço de cálculo e o serviço de cálculo de arredondamento também imprime um log das operações invocado para as janelas do console do respectivos.  
  
9. Na janela do console de cliente, digite `quit` e pressione ENTER para sair.  
  
10. Pressione ENTER nas janelas do console de serviços para encerrar os serviços.  
  
## <a name="configurable-via-code-or-appconfig"></a>Configuráveis por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo RoutingService\App.config para algo diferente para que ele não é reconhecido e remova a chamada de método para `ConfigureRouterViaCode()` em RoutingService\routing.cs. Um método resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador que atua como um roteador baseado em conteúdo, permitindo que vários tipos ou implementação de serviços a serem expostas por meio de um ponto de extremidade.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja virtualizar todos os seus serviços para expor apenas um ponto de extremidade publicamente por meio do qual eles oferecem acesso a vários tipos diferentes de serviços. Nesse caso, eles utilizam baseado em conteúdo capacidades de roteamento do serviço de roteamento para determinar onde as solicitações de entrada devem ser enviadas.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
