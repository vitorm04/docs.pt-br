---
title: "Noções básicas de alterações de estado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 972b7e0ed9ffbc9f9ddecb2ab7afdd08626fde19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-state-changes"></a>Noções básicas de alterações de estado
Este tópico discute os estados e transições que tem canais, os tipos usados para estados de canal de estrutura e como implementá-los.  
  
## <a name="state-machines-and-channels"></a>Máquinas de estado e canais  
 Soquetes de objetos que lidam com a comunicação, por exemplo, geralmente apresentam uma máquina de estado cujas transições de estado relacionam a alocação de recursos de rede, tornando ou aceitando conexões, fechando conexões e encerrando comunicação. A máquina de estado do canal fornece um modelo uniforme de estados de um objeto de comunicação que abstrai a implementação subjacente desse objeto. O <xref:System.ServiceModel.ICommunicationObject> interface fornece um conjunto de estados, métodos de transição de estado e eventos de transição de estado. Todos os canais, fábricas de canais e ouvintes de canais implementam a máquina de estado do canal.  
  
 Os eventos fechado, fechar, com falha, aberto e abrir sinalizam um observador externo após a ocorrência de uma transição de estado.  
  
 Os métodos de anulação, fechar e abrir (e seus equivalentes assíncronas) causam transições de estado.  
  
 A propriedade state retorna o estado atual, conforme definido pelo <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>ICommunicationObject, CommunicationObject e estados e transição de estado  
 Um <xref:System.ServiceModel.ICommunicationObject> iniciado no estado criado em suas várias propriedades podem ser configuradas. Uma vez no estado aberto, o objeto é usado para enviar e receber mensagens, mas suas propriedades são consideradas imutáveis. Quando no estado de fechamento, o objeto não pode processar novo enviar ou receber solicitações, mas as solicitações existentes tenham a oportunidade de concluir até que o tempo limite de fechamento é atingido.  Se ocorrer um erro irrecuperável, o objeto faz a transição para estado com falha, onde pode ser inspecionado para obter informações sobre o erro e, por fim, fechado. Quando no estado fechado o objeto essencialmente atingiu o fim da máquina de estado. Uma vez um objeto faz a transição de um estado para o próximo, ele não volte a um estado anterior.  
  
 O diagrama a seguir mostra o <xref:System.ServiceModel.ICommunicationObject> estados e transições de estado. Transições de estado podem ser causadas por um dos três métodos de chamada: anular, abrir, ou fechar. Eles também podem ser causados por chamar outros métodos específicos de implementação. Em transição para estado com falha pode ocorrer como resultado de erros durante a abertura ou depois de ter aberto o objeto de comunicação.  
  
 Cada <xref:System.ServiceModel.ICommunicationObject> iniciado no estado criado. Nesse estado, um aplicativo pode configurar o objeto definindo suas propriedades. Depois que um objeto está em um estado que não seja criado, ele é considerado imutável.  
  
 ![Canal estado transitition](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Figura 1. A máquina de estado de ICommunicationObject.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece uma classe base abstrata denominada <xref:System.ServiceModel.Channels.CommunicationObject> que implementa <xref:System.ServiceModel.ICommunicationObject> e a máquina de estado do canal. O gráfico a seguir é um diagrama de estado modificado é específico para <xref:System.ServiceModel.Channels.CommunicationObject>. Além de <xref:System.ServiceModel.ICommunicationObject> máquina de estado, ele mostra o tempo quando adicionais <xref:System.ServiceModel.Channels.CommunicationObject> métodos forem invocados.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Figura 2. A implementação de CommunicationObject da máquina de estado ICommunicationObject incluindo chamadas para eventos e métodos protegidos.  
  
### <a name="icommunicationobject-events"></a>Eventos de ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject>expõe os cinco eventos definidos por <xref:System.ServiceModel.ICommunicationObject>. Esses eventos são criados para o código usando o objeto de comunicação a ser notificado das transições de estado. Conforme mostrado na Figura 2 acima, cada evento é disparado uma vez depois que o estado do objeto faz a transição para o estado de chamada pelo evento. Todos os cinco eventos são do `EventHandler` tipo que está definido como:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 No <xref:System.ServiceModel.Channels.CommunicationObject> implementação, o remetente é o <xref:System.ServiceModel.Channels.CommunicationObject> em si, ou que foi passado como o remetente para o <xref:System.ServiceModel.Channels.CommunicationObject> construtor (se essa sobrecarga de construtor foi usada). O parâmetro EventArgs, `e`, é sempre `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Objeto derivado de retornos de chamada  
 Os cinco eventos, além de <xref:System.ServiceModel.Channels.CommunicationObject> declara oito protegido métodos virtuais projetados para permitir que um objeto derivado seja chamado novamente, antes e depois ocorrem transições de estado.  
  
 O <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> métodos têm três tais retornos de chamada associados a cada um deles. Por exemplo, correspondente ao <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> há <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Associado <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> são o <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> métodos.  
  
 Da mesma forma, o <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> método tem um correspondente <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Enquanto <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> não têm nenhuma implementação padrão, os outros retornos de chamada tem uma implementação padrão que é necessária para a correção de máquina de estado. Se você substituir os métodos Certifique-se de chamar a implementação base ou substitua-o corretamente.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> acionar correspondente <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> eventos. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>e <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> definem o estado do objeto aberto e fechado, respectivamente, em seguida, acionar correspondente <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> eventos.  
  
### <a name="state-transition-methods"></a>Métodos de transição de estado  
 <xref:System.ServiceModel.Channels.CommunicationObject>fornece implementações de Abort, feche e abra. Ele também fornece um método de falha que faz com que uma transição de estado para o estado com falha. A Figura 2 mostra o <xref:System.ServiceModel.ICommunicationObject> máquina de estado com cada transição rotulada pelo método que faz com que ele (sem rótulo transições acontecer dentro da implementação do método que fez a última transição rotulada).  
  
> [!NOTE]
>  Todos os <xref:System.ServiceModel.Channels.CommunicationObject> Obtém/define são sincronizados de thread de estado de implementações de comunicação.  
  
 Construtor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>fornece três construtores, que deixe o objeto no estado criado. Os construtores são definidos como:  
  
 O primeiro construtor é um construtor padrão que delega para a sobrecarga de construtor que usa um objeto:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 O construtor que usa um objeto usa esse parâmetro como o objeto a ser bloqueada durante a sincronização de acesso ao estado do objeto de comunicação:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Por fim, um terceiro construtor usa um parâmetro adicional que é usado como o argumento do remetente quando <xref:System.ServiceModel.ICommunicationObject> os eventos são disparados.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Os dois construtores anteriores definido o remetente para isso.  
  
 Método Open  
  
 Pré-condição: O estado é criado.  
  
 Pós-condição: O estado é aberto ou com falha. Pode lançar uma exceção.  
  
 O método Open () tentará abrir o objeto de comunicação e defina o estado como aberto. Se encontrar um erro, ele definirá o estado como com falha.  
  
 O método primeiro verifica se o estado atual é criado. Se o estado atual for a abertura ou abriu lança um <xref:System.InvalidOperationException>. Se o estado atual é de fechamento ou fechado, ele gerará uma <xref:System.ServiceModel.CommunicationObjectAbortedException> se o objeto foi encerrado e <xref:System.ObjectDisposedException> caso contrário. Se o estado atual está com defeito, ele gerará um <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Ele define o estado de abertura e chama OnOpening() (que gera o evento de abertura), OnOpen() e OnOpened() nessa ordem. OnOpened() define o estado como aberto e gera o evento aberto. Se qualquer um desses lança uma exceção, (aberta) chama Fault() e permite que a bolha de exceção, o backup. O diagrama a seguir mostra o processo de abertura mais detalhadamente.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Substitua o método OnOpen para implementar a lógica de abrir personalizada, como abrir um objeto de comunicação interna.  
  
 Método Close  
  
 Pré-condição: None.  
  
 Pós-condição: O estado está fechado. Pode lançar uma exceção.  
  
 O método Close () pode ser chamado em qualquer estado. Tentar fechar o objeto normalmente. Se um erro for encontrado, ele encerra o objeto. O método não nada se o estado atual é de fechamento ou fechado. Caso contrário, ela define o estado fechamento. Se o estado original foi criado, a abertura ou com falha, ele chama Abort () (consulte o diagrama a seguir). Se o estado original foi aberto, ele chama OnClosing() (que gera o evento de fechamento), OnClose() e OnClosed() nessa ordem. Se qualquer um desses lança uma exceção, (Fechar) chama Abort () e permite que a bolha de exceção, o backup. OnClosed() define o estado para fechado e gera o evento fechado. O diagrama a seguir mostra o fechamento processar mais detalhadamente.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Substitua o método OnClose para implementar a lógica de fechar personalizada, como fechar um objeto de comunicação interna. Todos os normal fechando lógica que pode ser bloqueadas por muito tempo (por exemplo, aguardando outro lado responder) deve ser implementado em OnClose() porque ele usa um parâmetro de tempo limite e porque ele não é chamado como parte de Abort ().  
  
 Anular  
  
 Pré-condição: None.  
Pós-condição: O estado está fechado. Pode lançar uma exceção.  
  
 O método Abort () não fará nada se o estado atual for fechado ou se o objeto foi finalizado antes (por exemplo, possivelmente fazendo com que Abort () em execução em outro thread). Caso contrário, ele define o estado de fechamento e chama OnClosing() (que gera o evento de fechamento), OnAbort() e OnClosed() nessa ordem (não chamar OnClose porque o objeto está sendo encerrado, não fechada). OnClosed() define o estado para fechado e gera o evento fechado. Se qualquer uma dessas lançar uma exceção, é lançada novamente para o chamador de anulação. Implementações de OnClosing(), OnClosed() e OnAbort() não devem bloquear (por exemplo, na entrada/saída). O diagrama a seguir mostra o processo de anulação em mais detalhes.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Substituir o método OnAbort implementar personalizada de término lógica como encerrar um objeto de comunicação interna.  
  
 Fault  
  
 O método de falhas é específico para <xref:System.ServiceModel.Channels.CommunicationObject> e não fazem parte do <xref:System.ServiceModel.ICommunicationObject> interface. Aqui está incluído para fins de integridade.  
  
 Pré-condição: None.  
  
 Pós-condição: Estado está com defeito. Pode lançar uma exceção.  
  
 O método Fault() não fará nada se o estado atual é com falha ou fechado. Caso contrário, ele define o estado com falha e chamada OnFaulted(), que gera o evento com falha. Se OnFaulted lança uma exceção é lançada novamente.  
  
### <a name="throwifxxx-methods"></a>Métodos de ThrowIfXxx  
 CommunicationObject tem três métodos protegidos que podem ser usados para gerar exceções se o objeto está em um estado específico.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A>gera uma exceção se o estado for fechamento, fechado ou com falha.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A>gera uma exceção se o estado não é criado.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A>gera uma exceção se o estado não estiver aberto.  
  
 As exceções geradas dependem do estado. A tabela a seguir mostra os diferentes estados e o tipo correspondente do exceção gerada ao chamar um ThrowIfXxx que lança nesse estado.  
  
|Estado|Anular foi chamada?|Exceção|  
|-----------|----------------------------|---------------|  
|Criado|N/D|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Abertura|N/D|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Aberto|N/D|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Fechando|Sim|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Fechando|Não|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Closed|Sim|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>no caso de que um objeto foi fechado por uma chamada anterior e explícita de anulação. Se você chamar Fechar no objeto e um <xref:System.ObjectDisposedException?displayProperty=nameWithType> é gerada.|  
|Closed|Não|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Com defeito|N/D|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Tempos limite  
 Vários métodos que discutimos usam parâmetros de tempo limite. Estes são fechar, Open (determinadas sobrecargas e versões assíncronas), OnClose AoAbrir. Esses métodos são projetados para permitir operações longas (por exemplo, bloqueando a entrada/saída ao fechar uma conexão normalmente) para o parâmetro timeout indica por quanto tempo essas operações podem levar antes que está sendo interrompida. Implementações de qualquer um desses métodos devem usar o valor de tempo limite fornecido para garantir que ele retorna ao chamador dentro desse limite. Implementações de outros métodos que não têm um tempo limite não são projetadas para operações demoradas e não devem bloquear na entrada e saída.  
  
 A exceção são as sobrecargas de Open () e Close () que não têm um tempo limite. Esses usam um valor de tempo limite padrão fornecido pela classe derivada. <xref:System.ServiceModel.Channels.CommunicationObject>expõe dois protegido propriedades abstratas denominadas <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> e <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> definido como:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Uma classe derivada implementa essas propriedades para fornecer o tempo limite padrão para as sobrecargas de Open () e Close () que não têm um valor de tempo limite. Em seguida, as implementações de Open () e Close () deleguem para a sobrecarga que usa um tempo limite de passar o valor de tempo limite padrão, por exemplo:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Essa interface possui quatro propriedades somente leitura para fornecer padrão valores de tempo limite para abrir, enviar, receber e fechar. Cada implementação é responsável por obter os valores padrão de qualquer maneira apropriada. Como uma conveniência, <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase> padrão esses valores como 1 minuto.
