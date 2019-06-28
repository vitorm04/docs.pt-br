---
title: Noções básicas de alterações de estado
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: 858da2a88c17920910c05966bb3b211d754fb278
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424771"
---
# <a name="understanding-state-changes"></a>Noções básicas de alterações de estado
Este tópico discute os estados e transições que tem canais, os tipos usados para os estados de canal de estrutura e como implementá-los.  
  
## <a name="state-machines-and-channels"></a>Canais e máquinas de estado  
 Soquetes de objetos que lidam com a comunicação, por exemplo, geralmente apresentam uma máquina de estado cujas transições de estado relacionam a alocação de recursos de rede, tornando ou aceitando conexões, fechando conexões e encerramento de comunicação. A máquina de estado do canal fornece um modelo uniforme dos Estados de um objeto de comunicação que abstrai a implementação subjacente desse objeto. O <xref:System.ServiceModel.ICommunicationObject> interface fornece um conjunto de estados, os métodos de transição de estado e eventos de transição de estado. Todos os canais, fábricas de canais e ouvintes de canais implementam a máquina de estado do canal.  
  
 Os eventos fechado, fechar, Faulted, aberto e abertura sinalizam um observador externo após a ocorrência de uma transição de estado.  
  
 Os métodos de anulação, fechar e abrir (e seus equivalentes assíncronos) causam transições de estado.  
  
 A propriedade state retorna o estado atual, conforme definido pelo <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>ICommunicationObject, CommunicationObject e estados e transição de estado  
 Um <xref:System.ServiceModel.ICommunicationObject> começa no estado Created onde suas várias propriedades podem ser configuradas. Uma vez no estado aberto, o objeto é pode ser usado para enviar e receber mensagens, mas suas propriedades são consideradas imutáveis. Depois que no estado de fechamento, o objeto não pode processar o envio de novo ou receber solicitações, mas as solicitações existentes tenham a oportunidade de concluir até que o tempo limite de fechamento é atingido.  Se ocorrer um erro irrecuperável, o objeto faz a transição para o estado de falha em que pode ser inspecionado para obter informações sobre o erro e, por fim, fechada. Quando no estado fechado o objeto essencialmente alcançou o final da máquina de estado. Uma vez um objeto faz a transição de um estado para o próximo, ele não volte a um estado anterior.  
  
 O diagrama a seguir mostra o <xref:System.ServiceModel.ICommunicationObject> estados e transições de estado. Transições de estado podem ser causadas por um dos três métodos de chamada: Anular, abrir, ou fechar. Eles também pode ser causados por chamar outros métodos específicos de implementação. A transição para o estado de falha pode ocorrer como resultado de erros durante a abertura ou depois de ter aberto o objeto de comunicação.  
  
 Cada <xref:System.ServiceModel.ICommunicationObject> começa no estado criado. Nesse estado, um aplicativo pode configurar o objeto definindo suas propriedades. Depois que um objeto está em um estado diferente de criado, ele é considerado imutável.  
  
 ![Transição de estado do canal](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Figura 1. A máquina de estado de ICommunicationObject.  
  
 Windows Communication Foundation (WCF) fornece uma classe base abstrata denominada <xref:System.ServiceModel.Channels.CommunicationObject> que implementa <xref:System.ServiceModel.ICommunicationObject> e a máquina de estado do canal. O gráfico a seguir é um diagrama de estado modificado que é específico para <xref:System.ServiceModel.Channels.CommunicationObject>. Além de <xref:System.ServiceModel.ICommunicationObject> máquina de estado, ele mostra o tempo quando adicionais <xref:System.ServiceModel.Channels.CommunicationObject> métodos são invocados.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Figura 2. A implementação de CommunicationObject da máquina de estado ICommunicationObject, incluindo as chamadas aos eventos e métodos protegidos.  
  
### <a name="icommunicationobject-events"></a>Eventos de ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject> expõe os cinco eventos definidos por <xref:System.ServiceModel.ICommunicationObject>. Esses eventos são projetados para o código usando o objeto de comunicação para ser notificado de transições de estado. Conforme mostrado na Figura 2 acima, cada evento é acionado uma vez depois que o estado do objeto faz a transição para o estado chamado pelo evento. Todos os cinco eventos são do `EventHandler` tipo que é definido como:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 No <xref:System.ServiceModel.Channels.CommunicationObject> implementação, o remetente seja a <xref:System.ServiceModel.Channels.CommunicationObject> propriamente dito ou tudo o que foi passado como o remetente para o <xref:System.ServiceModel.Channels.CommunicationObject> construtor (se essa sobrecarga de construtor foi usada). O parâmetro EventArgs `e`, é sempre `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Objeto derivado de retornos de chamada  
 Além dos cinco eventos, <xref:System.ServiceModel.Channels.CommunicationObject> declara oito protegido métodos virtuais projetados para permitir que um objeto derivado a ser chamado antes e depois ocorrem transições de estado.  
  
 O <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> métodos têm três desses retornos de chamada associados com cada um deles. Por exemplo, correspondente ao <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> há <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Associados <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> são os <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> métodos.  
  
 Da mesma forma, o <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> método tem um correspondente <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Embora <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, e <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> não têm nenhuma implementação padrão, os outros retornos de chamada terá uma implementação padrão que é necessária para a correção de máquina de estado. Se você substituir esses métodos Certifique-se de chamar a implementação base ou substitua-o corretamente.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> acionar correspondente <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> eventos. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> definem o estado do objeto aberto e fechado, respectivamente, em seguida, acionar correspondente <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> eventos.  
  
### <a name="state-transition-methods"></a>Métodos de transição de estado  
 <xref:System.ServiceModel.Channels.CommunicationObject> fornece implementações de anulação, feche e abra. Ele também fornece um método de falha que faz com que uma transição de estado para o estado de falha. A Figura 2 mostra o <xref:System.ServiceModel.ICommunicationObject> máquina de estado com cada transição rotulada pelo método que faz com que ele (sem rótulo transições acontecer dentro da implementação do método que fez a transição de rotulado última).  
  
> [!NOTE]
>  Todos os <xref:System.ServiceModel.Channels.CommunicationObject> Obtém/define são sincronizados pelo thread de estado de implementações de comunicação.  
  
 Construtor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> fornece três construtores, que deixar o objeto no estado criado. Os construtores são definidos como:  
  
 O primeiro construtor é um construtor padrão que delega para a sobrecarga de construtor que utiliza um objeto:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 O construtor que usa um objeto usa esse parâmetro como o objeto a ser bloqueado durante a sincronização de acesso ao estado do objeto de comunicação:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Por fim, um terceiro construtor leva um parâmetro adicional que é usado como o argumento do remetente quando <xref:System.ServiceModel.ICommunicationObject> os eventos são disparados.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Os dois construtores anteriores definido o remetente para isso.  
  
 Método Open  
  
 Pré-condição: Estado é criado.  
  
 Pós-condição: Estado é aberto ou com falha. Pode lançar uma exceção.  
  
 O método Open () tentará abrir o objeto de comunicação e definir o estado como aberto. Se ele encontrar um erro, ele definirá o estado de falha.  
  
 O método primeiro verifica se o estado atual foi criado. Se o estado atual é a abertura ou abriu lança um <xref:System.InvalidOperationException>. Se o estado atual é de fechamento ou Closed, ele gerará uma <xref:System.ServiceModel.CommunicationObjectAbortedException> se o objeto foi encerrado e <xref:System.ObjectDisposedException> caso contrário. Se o estado atual está com defeito, ele gerará um <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Em seguida, ele define o estado de abertura e chama OnOpening() (que gera o evento de abertura), OnOpen() e OnOpened() nessa ordem. OnOpened() define o estado como aberto e gera o evento aberto. Se qualquer um desses lança uma exceção, (aberta) chama Fault() e permite que a bolha de exceção, o backup. O diagrama a seguir mostra o processo de abertura mais detalhadamente.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Substitua o método OnOpen para implementar uma lógica personalizada de aberto, como abrir um objeto de comunicação interna.  
  
 Método Close  
  
 Pré-condição: nenhuma.  
  
 Pós-condição: Estado está fechado. Pode lançar uma exceção.  
  
 O método Close () pode ser chamado em qualquer estado. Ele tenta fechar o objeto normalmente. Se um erro for encontrado, ele encerra o objeto. O método faz nada se o estado atual está fechando ou fechada. Caso contrário, ele define o estado para fechar. Se o estado original tiver sido criado, a abertura ou com falha, ele chama Abort () (consulte o diagrama a seguir). Se o estado original foi aberto, ele chama OnClosing() (que gera o evento de fechamento), OnClose() e OnClosed() nessa ordem. Se qualquer um desses lança uma exceção, (Fechar) chama Abort () e permite que a bolha de exceção, o backup. OnClosed() define o estado para fechado e aciona o evento Closed. A diagrama a seguir mostra o processo de fechamento em mais detalhes.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Substitua o método OnClose para implementar a lógica personalizada de fechamento, como fechar um objeto de comunicação interna. Todos os normal fechando a lógica que podem ser bloqueadas por muito tempo (por exemplo, aguardando o outro lado responder) deve ser implementado em OnClose() porque ele usa um parâmetro de tempo limite e porque ele não é chamado como parte de Abort ().  
  
 Anular  
  
 Pré-condição: nenhuma.  
Pós-condição: Estado está fechado. Pode lançar uma exceção.  
  
 O método Abort () não faz nada se o estado atual for fechado ou se o objeto foi encerrado antes (por exemplo, possivelmente fazendo com que Abort () em execução em outro thread). Caso contrário, ele define o estado de fechamento e chama OnClosing() (que gera o evento de fechamento), OnAbort() e OnClosed() nessa ordem (chame OnClose porque o objeto está sendo encerrado, não fechada). OnClosed() define o estado para fechado e aciona o evento Closed. Se qualquer um desses lançar uma exceção, é lançada novamente para o chamador de anulação. Implementações de OnClosing(), OnClosed() e OnAbort() não devem bloquear (por exemplo, na entrada/saída). O diagrama a seguir mostra o processo de anulação em mais detalhes.  
  
 ![Alterações de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Substituir o método OnAbort implementar personalizado encerrar lógica como encerrar um objeto de comunicação interna.  
  
 Fault  
  
 O método de falha é específico para <xref:System.ServiceModel.Channels.CommunicationObject> e é não fazem parte do <xref:System.ServiceModel.ICommunicationObject> interface. Ele é incluído aqui para fins de integridade.  
  
 Pré-condição: nenhuma.  
  
 Pós-condição: Estado está com defeito. Pode lançar uma exceção.  
  
 O método Fault() não fará nada se o estado atual for Faulted ou fechado. Caso contrário, ele define o estado Faulted e chamada OnFaulted(), que gera o evento de falha. Se OnFaulted lança uma exceção é lançada novamente.  
  
### <a name="throwifxxx-methods"></a>Métodos de ThrowIfXxx  
 CommunicationObject tem três métodos protegidos que podem ser usados para gerar exceções se o objeto está em um estado específico.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> gera uma exceção se o estado for fechamento, fechado ou com falha.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> gera uma exceção se o estado não é criado.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> gera uma exceção se o estado não estiver aberto.  
  
 As exceções geradas dependem do estado. A tabela a seguir mostra os diferentes estados e o tipo da exceção gerada ao chamar um ThrowIfXxx que gera em que o estado correspondente.  
  
|Estado|Anulação foi chamada?|Exceção|  
|-----------|----------------------------|---------------|  
|Criado|N/D|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Abertura|N/D|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Aberto|N/D|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Fechando|Sim|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Fechando|Não|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Closed|Sim|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> no caso de que um objeto foi fechado por uma chamada anterior e explícita de anulação. Se você chamar Close no objeto, uma <xref:System.ObjectDisposedException?displayProperty=nameWithType> é gerada.|  
|Closed|Não|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Com falha|N/D|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Tempos limite  
 Vários métodos que discutimos usam parâmetros de tempo limite. Esses são OnOpen, OnClose, aberto (determinadas sobrecargas e versões assíncronas) e próximos à. Esses métodos são projetados para permitir operações demoradas (por exemplo, entrada/saída, enquanto normalmente fechar uma conexão de bloqueio) para que o parâmetro timeout indica quanto tempo dessas operações podem levar antes que está sendo interrompida. Implementações de qualquer um desses métodos devem usar o valor de tempo limite fornecido para garantir que ele retorna ao chamador dentro do que o tempo limite. Implementações de outros métodos que não têm um tempo limite não são projetadas para operações longas e não devem bloquear na entrada/saída.  
  
 A exceção são as sobrecargas de Open () e Close () que não têm um tempo limite. Eles usam um valor de tempo limite padrão fornecido pela classe derivada. <xref:System.ServiceModel.Channels.CommunicationObject> expõe duas propriedades abstratas denominadas protegido por <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> e <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> definida como:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Uma classe derivada implementa essas propriedades para fornecer o tempo limite padrão para as sobrecargas de Open () e Close () que não têm um valor de tempo limite. Em seguida, as implementações de Open () e Close () delegar para a sobrecarga que utiliza um tempo limite passando o valor de tempo limite padrão, por exemplo:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Essa interface tem quatro propriedades somente leitura para fornecer padrão de valores de tempo limite para abrir, enviar, receber e fechar. Cada implementação é responsável por obter os valores padrão de qualquer maneira apropriada. Como uma conveniência <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase> padrão desses valores para 1 minuto.
