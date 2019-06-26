---
title: Selecionando um transporte
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: 611e8df29b37efd880ee1d19515697d899e4fa7e
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402152"
---
# <a name="choosing-a-transport"></a>Selecionando um transporte
Este tópico discute os critérios para escolher entre os três transportes principais que estão incluídos no Windows Communication Foundation (WCF): HTTP, TCP e pipes nomeados. O WCF também inclui um enfileiramento de mensagens (também conhecido como MSMQ) de transporte, mas este documento não abrange o enfileiramento de mensagens.  
  
 O modelo de programação WCF separa as operações de ponto de extremidade (conforme expressa em um contrato de serviço) do mecanismo de transporte que conecta dois pontos de extremidade. Isso lhe dá a flexibilidade para decidir como expor os serviços de rede.  
  
 No WCF, você especificar como transferir dados através de uma rede entre pontos de extremidade usando um *vinculação*, que é composto de uma sequência de *elementos de associação*. Um transporte é representado por um elemento de associação de transporte, que faz parte da associação. Uma associação inclui elementos de associação de protocolo opcional, como segurança, um elemento de associação do codificador de mensagem necessário e um elemento de associação de transporte obrigatório. Um transporte envia ou recebe o formato serializado de uma mensagem para ou de outro aplicativo.  
  
 Se você precisar se conectar a um servidor ou cliente existente, você não pode ter uma opção sobre como usar um transporte particular. No entanto, os serviços WCF podem se tornar acessíveis por meio de vários pontos de extremidade, cada um com um transporte diferente. Quando um único transporte não abrange o público-alvo para seu serviço, considere a exposição de serviço em vários pontos de extremidade. Aplicativos cliente, em seguida, podem usar o ponto de extremidade que é melhor para eles.  
  
 Depois de escolher um transporte, você deve selecionar uma associação que usa a ele. Você pode escolher uma associação fornecida pelo sistema (consulte [associações System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md)), ou você pode criar sua própria associação personalizada (consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). Você também pode criar sua própria associação. Para obter mais informações, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Vantagens de cada transporte  
 Esta seção descreve os principais motivos para escolher qualquer um dos três principais transportes, incluindo um gráfico de decisão detalhadas para escolher entre eles.  
  
### <a name="when-to-use-http-transport"></a>Quando usar o transporte HTTP  
 HTTP é um protocolo de solicitação/resposta entre clientes e servidores. A aplicação mais comum consiste em clientes de navegador da Web que se comunicam com um servidor Web. O cliente envia uma solicitação para um servidor que escuta mensagens de solicitação do cliente. Quando o servidor recebe uma solicitação, ele retorna uma resposta, que contém o status da solicitação. Se for bem-sucedido, os dados opcionais, como uma página da Web, uma mensagem de erro ou outra informação são retornados. Para obter mais informações sobre o protocolo HTTP, consulte [HTTP - Hypertext Transfer Protocol](https://go.microsoft.com/fwlink/?LinkId=94858).  
  
 O protocolo HTTP não é baseado em conexão — depois que a resposta é enviada, nenhum estado é mantido. Para lidar com transações de várias páginas, o aplicativo deve persistir qualquer estado necessário.  
  
 No WCF, o transporte HTTP associação é otimizada para interoperabilidade com sistemas herdados não WCF. Se todas as partes da comunicação estiver usando o WCF, as associações com base em pipes nomeadas ou com base em TCP são mais rápidas. Para obter mais informações, consulte <xref:System.ServiceModel.NetTcpBinding> e <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Quando usar o transporte TCP  
 TCP é um serviço de entrega orientada por fluxo com base em conexão com a detecção de erros de ponta a ponta e correção. *Com base em Conexão* significa que uma sessão de comunicação entre os hosts é estabelecida antes da troca de dados. Um host é qualquer dispositivo em uma rede TCP/IP identificado por um endereço IP lógico.  
  
 TCP fornece entrega confiável de dados e a facilidade de uso. Especificamente, TCP notifica o remetente de entrega de pacotes, garante que os pacotes sejam entregues na mesma ordem em que elas são enviadas, retransmite pacotes perdidos e garante que os pacotes de dados não são duplicados. Observe que essa entrega confiável aplica-se entre dois nós de TCP/IP e não é a mesma coisa que *WS-ReliableMessaging*, que aplica-se entre os pontos de extremidade, não importa quantos nós intermediários podem incluir.  
  
 O transporte TCP do WCF é otimizado para o cenário em que ambas as extremidades da comunicação estão usando o WCF. Essa associação é a associação WCF mais rápida para cenários que envolvem a comunicação entre computadores diferentes. Uso de troca de mensagem o <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> para transferência de mensagem otimizado. TCP fornece comunicação duplex e, portanto, podem ser usados para implementar contratos duplex, mesmo se o cliente estiver atrás de conversão de endereços de rede (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Quando usar o transporte de Pipe nomeado  
 Um pipe nomeado é um objeto no kernel do sistema operacional Windows, como uma seção de memória compartilhada que os processos podem usar para comunicação. Um pipe nomeado tem um nome e pode ser usado para comunicação unidirecional ou bidirecionais entre processos em um único computador.  
  
 Quando a comunicação é necessária entre diferentes aplicativos WCF em um único computador, e você deseja impedir qualquer comunicação de outro computador, em seguida, use o transporte de pipes nomeados. Uma restrição adicional é que os processos em execução na área de trabalho remota do Windows podem ser restritos à mesma sessão de área de trabalho remota do Windows, a menos que eles têm privilégios elevados.  
  
> [!WARNING]
>  Ao usar o transporte de pipe nomeado com uma reserva de URL curinga fraco em vários sites hospedados no IIS, o seguinte erro pode ocorrer: Ocorreu um erro no serviço de ativação NetPipeActivator do protocolo 'NET. pipe' ao tentar escutar para o site '2', portanto, o protocolo é desabilitado para o site temporariamente. Consulte a mensagem de exceção para obter mais detalhes. URL: WeakWildcard:net.pipe:/\<nome do computador > / Status: Exceção ConflictingRegistration:  Nome do processo: ID do processo do SMSvcHost: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Pontos de decisão para escolher um transporte  
 A tabela a seguir descreve os pontos de decisão comum usados para escolher um transporte. Você deve considerar todos os atributos adicionais e transportes que se aplicam ao seu aplicativo. Identificar os atributos que são importantes para seu aplicativo, identificar os transportes de maneira favorável associar com cada um dos seus atributos e, em seguida, selecione os transportes que funcionam melhor com seu conjunto de atributos.  
  
|Atributo|Descrição|Transportes favorecidos|  
|---------------|-----------------|------------------------|  
|Diagnóstico|Diagnóstico permitem que você detecte automaticamente os problemas de conectividade de transporte. Todos os transportes dão suporte a capacidade de enviar informações de falha de back-que descreve a conectividade. No entanto, o WCF não inclui ferramentas de diagnóstico para investigar problemas de rede.|Nenhum|  
|Hospedagem|Todos os pontos de extremidade do WCF devem ser hospedados dentro de um aplicativo. IIS 6.0 e versões anteriores dão suporte somente aplicativos de hospedagem que usam o transporte HTTP. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], o suporte é adicionado para hospedar todos os transportes WCF, incluindo TCP e pipes nomeado. Para obter mais informações, consulte [hospedagem nos serviços de informações da Internet](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) e [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Inspeção|A inspeção é a capacidade de extrair e processar informações da mensagens durante a transmissão. O protocolo HTTP separa as informações de roteamento e controle de dados, tornando mais fácil criar ferramentas que inspecionar e analisar as mensagens. Transportes que são fáceis de inspecionar também podem exigir menos poder de processamento em dispositivos de rede. O nível de segurança usada afeta se as mensagens podem ser inspecionadas.|HTTP|  
|latência|Latência é a quantidade mínima de tempo necessário para concluir uma troca de mensagens. Todas as operações de rede mais ou menos têm latência dependendo da opção de transporte. Usando comunicação duplex ou unidirecional com um transporte cujo padrão de troca de mensagem nativo é de solicitação-resposta, como HTTP, pode fazer com que a latência adicional devido a correlação forçada de mensagens. Nessa situação, considere o uso de um transporte cujo padrão de troca de mensagem nativa é duplex, como TCP.|TCP, chamado<br /><br /> Pipe|  
|Alcance|O alcance de um transporte reflete como compatível com o transporte é ao conectar-se com outros sistemas. O transporte de pipe nomeado tem muito pouco alcance; ele só pode se conectar aos serviços em execução no mesmo computador. Os transportes TCP e HTTP têm alcance excelente e podem entrar em algumas configurações de NAT e firewall. Para obter mais informações, consulte [trabalhando com NATs e Firewalls](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Segurança|A segurança é a capacidade de proteger as mensagens durante a transferência, fornecendo a confidencialidade, integridade ou a autenticação. Confidencialidade protege uma mensagem de que está sendo examinado, integridade protege uma mensagem de que está sendo modificado e autenticação fornece garantias sobre o remetente ou receptor da mensagem.<br /><br /> O WCF oferece suporte a segurança de transferência tanto no nível da mensagem e nível de transporte. Segurança de mensagem compõe com um transporte, se o transporte dá suporte a um modo de transferência em buffer. Suporte para segurança de transporte varia dependendo do transporte escolhido. O HTTP, TCP e pipe nomeado transportes têm paridade razoável em relação ao suporte para segurança de transporte.|Todos|  
|Taxa de transferência|Taxa de transferência mede a quantidade de dados que podem ser transmitidos e processados em um período de tempo especificado. Como latência, o transporte escolhido pode afetar a taxa de transferência para operações de serviço. Maximizar taxa de transferência para um transporte requer minimizando os dois a sobrecarga de transmitir conteúdo, bem como minimizar o tempo gasto aguardando as trocas de mensagens ser concluída. Transportes de pipe nomeado e o TCP adicione pouca sobrecarga para o corpo da mensagem e dar suporte a uma forma de duplex nativa que reduz a espera por respostas de mensagem.|TCP, pipe nomeado|  
|Ferramentas|Ferramentas representa o suporte a aplicativos de terceiros para um protocolo para o desenvolvimento, diagnóstico, hospedagem e outras atividades. Desenvolvimento de ferramentas e software para funcionar com o protocolo HTTP significa um grande investimento.|HTTP|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- [Associações](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Criando associações definidas pelo usuário](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
