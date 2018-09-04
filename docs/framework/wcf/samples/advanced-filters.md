---
title: Filtros avançados
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564194"
---
# <a name="advanced-filters"></a>Filtros avançados
Este exemplo demonstra um serviço de roteamento do Windows Communication Foundation (WCF). O serviço de roteamento é um componente do WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo. Este exemplo se adapta a amostragem padrão de Calculadora do WCF para se comunicar usando o serviço de roteamento. Este exemplo mostra como definir a lógica de roteamento baseado em conteúdo com o uso de filtros de mensagem e tabelas de filtro de mensagem.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A tabela a seguir mostra os filtros de mensagem que são adicionados à tabela de filtro de mensagem do serviço de roteamento.  
  
|Filtro|Regra|Prioridade|  
|------------|----------|--------------|  
|Se (tem o cabeçalho)|Arredondamento|2|  
|Se (aparecia no Ep2)|Normal|1|  
|Se (aparecia com endereço2)|Arredondamento|1|  
|Se (RoundRobin1)|Normal|0|  
|Se (RoundRobin2)|Arredondamento|0|  
  
 As tabelas de filtro de mensagem e filtros de mensagem podem ser criadas e configuradas por meio de código ou no arquivo de configuração do aplicativo. Para este exemplo, você pode encontrar as tabelas de filtro de mensagem definido por meio de código no arquivo RoutingService\routing.cs ou definidas no arquivo de configuração do aplicativo no arquivo RoutingService\App.config e filtros de mensagem. Os parágrafos a seguir descrevem como os filtros de mensagem e tabelas de filtro de mensagem são criadas para este exemplo por meio de código.  
  
 Primeiro, um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> procura por cabeçalho personalizado. Observe que <xref:System.ServiceModel.WSHttpBinding> resulta em uma versão de envelope usando SOAP 1.2, portanto, a instrução XPath é definida para usar o namespace SOAP 1.2. O Gerenciador de namespace padrão para <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s já define um prefixo para o namespace SOAP 1.2, /s12, que pode ser usado. No entanto, o Gerenciador de namespace padrão não tem o namespace personalizado que o cliente usa para definir o valor real do cabeçalho, portanto, esse prefixo deve ser definido. Esse filtro corresponde a qualquer mensagem que aparece com esse cabeçalho.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 O segundo filtro é um <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, que corresponde a qualquer mensagem que foi recebida o `calculatorEndpoint`. O nome do ponto de extremidade é definido quando um objeto de ponto de extremidade de serviço é criado.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 O terceiro filtro é um <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. Isso corresponde a qualquer mensagem que aparecem em um ponto de extremidade com um endereço que corresponde ao prefixo de endereço (ou a parte frontal), fornecida. Neste exemplo, o prefixo de endereço é definido como "http://localhost/routingservice/router/rounding/". Isso significa que qualquer mensagem de entrada endereçados para "http://localhost/routingservice/router/rounding/*" correspondem a este filtro. Nesse caso, ele é mensagens que aparecem no ponto de extremidade de arredondamento Calculadora, que tem o endereço do "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Os dois últimos filtros de mensagem são personalizados <xref:System.ServiceModel.Dispatcher.MessageFilter>s. Neste exemplo, um filtro de mensagem "RoundRobin" é usado. Esse filtro de mensagem é criado no arquivo RoutingService\RoundRobinMessageFilter.cs fornecido. Esses filtros, quando definidos como o mesmo grupo, alternam entre a emissão de relatórios se eles correspondem à mensagem e que não estiverem, de modo que apenas um deles responde `true` por vez.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Em seguida, todas essas mensagens são adicionadas a um <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Dessa forma, as prioridades são especificadas para influenciar a ordem na qual a tabela de filtro de mensagem executa os filtros. Quanto maior a prioridade, mais cedo que o filtro é executado; Quanto menor a prioridade, quanto mais tarde um filtro é executado. Assim, um filtro com prioridade 2 é executado antes de um filtro com prioridade 1. O nível de prioridade padrão se nenhum for especificado é 0. Uma tabela de filtro de mensagem executa todos os filtros em um nível de prioridade determinada antes de passar para o próximo nível de prioridade mais baixo. Se uma correspondência for encontrada em uma prioridade específica, em seguida, a tabela de filtro de mensagem não continuará tentando localizar correspondências com a próxima prioridade mais baixa.  
  
> [!NOTE]
>  Embora este exemplo mostra como usar as prioridades de filtro de mensagem, em geral é mais eficaz e melhor design para design e configurar seus filtros de modo que eles não requerem a priorização funcione corretamente.  
  
 O primeiro filtro a ser adicionado é o filtro XPath e sua prioridade é definida como 2. Isso é o primeiro filtro de mensagem que é executado. Se ele encontrar o cabeçalho personalizado, independentemente do que os resultados dos outros filtros seriam, a mensagem é roteada para o ponto de extremidade de Calculadora de arredondamento.  
  
 Com prioridade 1, os dois filtros são adicionados. Novamente, esses executado apenas se o filtro XPath com prioridade 2 não coincide com a mensagem. Esses dois filtros mostram duas maneiras diferentes para determinar onde a mensagem foi tratada quando ele apareceu. Como os dois filtros efetivamente verificam para ver se a mensagem chegou em um dos dois pontos de extremidade, eles podem ser executados no mesmo nível de prioridade porque eles fazem não ambos retornam `true` ao mesmo tempo.  
  
 Por fim, com prioridade 0 (prioridade mais baixa), execute o RoundRobin de mensagem filtros. Como os filtros são configurados com o mesmo nome de grupo, apenas um deles corresponde a cada vez. Como todas as mensagens com cabeçalho personalizado tiveram sido roteadas e todos aqueles resolvidos para os pontos de extremidade específicos virtualizados, mensagens tratadas pelos filtros de mensagem RoundRobin são apenas as mensagens que tenham sido tratadas ao ponto de extremidade de roteador padrão sem personalizado cabeçalho. Como alternar essas mensagens em uma mensagem para cada chamada, metade das operações de ir para o ponto de extremidade de calculadora Regular e a outra metade, vá para o ponto de extremidade de Calculadora de arredondamento.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra AdvancedFilters.sln.  
  
2.  Para abrir **Gerenciador de soluções**, selecione **Gerenciador de soluções** do **exibição** menu.  
  
3.  Pressione F5 ou CTRL + SHIFT + B no Visual Studio.  
  
    1.  Se você quiser iniciar automaticamente os projetos necessários quando você pressiona F5, a solução com o botão direito e selecione **propriedades**. Selecione o **projeto de inicialização** nó sob **propriedades comuns** no painel esquerdo. Selecione o **vários projetos de inicialização** botão de opção e defina todos os projetos para que o **iniciar** ação.  
  
    2.  Se você compilar o projeto com CTRL + SHIFT + B, você deve iniciar os seguintes aplicativos:  
  
        1.  Calculadora de cliente (. / CalculatorClient/bin/client.exe)  
  
        2.  Serviço da Calculadora (. / CalculatorService/bin/service.exe)  
  
        3.  Serviço de roteamento de Calculadora (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Na janela do console do cliente da Calculadora, pressione ENTER para iniciar o cliente. O cliente retorna uma lista de pontos de extremidade de destino à sua escolha.  
  
5.  Escolha um ponto de extremidade de destino, digitando seu letra correspondente e pressione ENTER.  
  
6.  Em seguida, o cliente solicita se você deseja adicionar um cabeçalho personalizado. Pressione s para Sim ou N para não e, em seguida, pressione ENTER.  
  
7.  Dependendo das seleções feitas, você deve ver saídas diferentes.  
  
    1.  A seguir está que a saída retornada, se você adicionou um cabeçalho personalizado para as mensagens.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  A seguir está que a saída retornada, se você escolheu o ponto de extremidade de arredondamento Calculadora sem um cabeçalho personalizado.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  A seguir está que a saída retornada, se você escolheu o ponto de extremidade de calculadora regulares sem um cabeçalho personalizado.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  A seguir está que a saída retornada, se você escolheu o ponto de extremidade de roteador padrão sem um cabeçalho personalizado.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  O serviço da Calculadora e o serviço da Calculadora arredondamento também imprime um log das operações invocado para as janelas de console respectivo.  
  
9. Na janela do console de cliente, digite `quit` e pressione ENTER para sair.  
  
10. Pressione ENTER nas janelas do console de serviços para encerrar os serviços.  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurável por meio de código ou App. config  
 O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador. Você também pode alterar o nome do arquivo RoutingService\App.config para algo diferente para que ele não é reconhecido e remova a chamada de método para `ConfigureRouterViaCode()` em RoutingService\routing.cs. Qualquer um dos métodos resulta no mesmo comportamento do roteador.  
  
### <a name="scenario"></a>Cenário  
 Este exemplo demonstra o roteador que atua como um roteador baseado em conteúdo, permitindo que vários tipos ou implementação de serviços a serem expostos por meio de um ponto de extremidade.  
  
### <a name="real-world-scenario"></a>Cenário do mundo real  
 A Contoso deseja virtualizar todos os seus serviços para expor somente um ponto de extremidade publicamente por meio dos quais eles oferecem acesso a vários tipos diferentes de serviços. Nesse caso, eles utilizam baseado em conteúdo recursos de roteamento do serviço de roteamento para determinar onde as solicitações de entrada devem ser enviadas.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
