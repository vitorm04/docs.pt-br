---
title: Selecionando um transporte
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b051cdeebf83b34b6e503d8d9cb54a38a46a2a6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="choosing-a-transport"></a>Selecionando um transporte
Este tópico discute os critérios para escolher entre os três transportes principais que estão incluídos no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]: HTTP, TCP e pipes nomeados. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também inclui um (também conhecido como MSMQ) de enfileiramento de mensagens de transporte, mas este documento não aborda o enfileiramento de mensagens.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação separa as operações de ponto de extremidade (conforme expresso em um contrato de serviço) do mecanismo de transporte que conecta dois pontos de extremidade. Isso oferece a flexibilidade para decidir como expor seus serviços na rede.  
  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], especifique como transferir dados através de uma rede entre pontos de extremidade usando um *associação*, que é composto de uma sequência de *elementos de associação*. Um transporte é representado por um elemento de associação de transporte, que faz parte da associação. Uma associação inclui elementos de associação de protocolo opcional, como segurança, um elemento de associação de codificador de mensagem necessário e um elemento de associação de transporte necessário. Um transporte envia ou recebe o formato serializado de uma mensagem para ou de outro aplicativo.  
  
 Se você deve se conectar a um servidor ou cliente existente, você não terá a opção de usar um transporte particular. No entanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem se tornar acessíveis através de vários pontos de extremidade, cada um com um transporte diferente. Quando um único transporte não abrange o público-alvo para seu serviço, considere a possibilidade de expor o serviço em vários pontos de extremidade. Aplicativos cliente podem usar o ponto de extremidade que é melhor para eles.  
  
 Depois de escolher um transporte, você deve selecionar uma associação que usa. Você pode escolher uma associação fornecida pelo sistema (consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md)), ou você pode criar sua própria associação personalizada (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). Você também pode criar sua própria associação. Para obter mais informações, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Vantagens de cada transporte  
 Esta seção descreve as principais razões para a escolha de qualquer um dos três principais transportes, incluindo um gráfico de decisão detalhadas para escolher entre eles.  
  
### <a name="when-to-use-http-transport"></a>Quando usar o transporte HTTP  
 HTTP é um protocolo de solicitação/resposta entre clientes e servidores. A aplicação mais comum consiste em clientes de navegador da Web que se comunicam com um servidor Web. O cliente envia uma solicitação para um servidor, que verifica se há mensagens de solicitação de cliente. Quando o servidor recebe uma solicitação, ele retorna uma resposta, que contém o status da solicitação. Se for bem-sucedido, serão retornados dados opcionais, como uma página da Web, uma mensagem de erro ou outras informações. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] o protocolo HTTP, consulte [HTTP - Hypertext Transfer Protocol](http://go.microsoft.com/fwlink/?LinkId=94858).  
  
 O protocolo HTTP não é baseado em conexão — depois que a resposta será enviada, nenhum estado é mantido. Para lidar com transações de várias páginas, o aplicativo deve manter qualquer estado necessárias.  
  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o transporte HTTP associação é otimizada para interoperabilidade com herdado não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistemas. Se estiver usando todas as partes da comunicação [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], as associações com base em pipes nomeadas ou com base em TCP são mais rápidas. Para obter mais informações, consulte <xref:System.ServiceModel.NetTcpBinding> e <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Quando usar o transporte TCP  
 O TCP é um serviço de entrega orientado em fluxo, com base em conexão com a detecção de erros de ponta a ponta e correção. *Com base em Conexão* significa que uma sessão de comunicação entre hosts é estabelecida antes da troca de dados. Um host é qualquer dispositivo em uma rede TCP/IP identificado por um endereço IP lógico.  
  
 TCP fornece entrega de dados confiável e facilidade de uso. Especificamente, TCP notifica o remetente de entrega de pacotes, garante que os pacotes sejam entregues na mesma ordem em que são enviados, retransmite pacotes perdidos e garante que os pacotes de dados não serão duplicados. Observe que essa entrega confiável aplica-se entre dois nós de TCP/IP e não é a mesma coisa que *WS-ReliableMessaging*, que se aplica entre pontos de extremidade, independentemente de quantos nós intermediários podem incluir.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transporte TCP é otimizado para o cenário em que ambas as extremidades da comunicação estão usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Essa associação é o mais rápido [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação para cenários que envolvem a comunicação entre computadores diferentes. A mensagem de uso de troca de <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> para transferência de mensagem otimizado. TCP fornece comunicação duplex e isso podem ser usados para implementar contratos duplex, mesmo se o cliente estiver atrás de conversão de endereços de rede (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Quando usar o transporte de Pipe nomeado  
 Um pipe nomeado é um objeto no núcleo do sistema operacional Windows, como uma seção de memória compartilhada que os processos podem usar para comunicação. Um pipe nomeado tem um nome e pode ser usado para comunicação unidirecional ou duplex entre processos em um único computador.  
  
 Quando a comunicação é necessária entre diferentes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos em um único computador e você deseja impedir que qualquer comunicação de outro computador, em seguida, usar o transporte de pipes nomeados. Uma restrição adicional é que os processos em execução na área de trabalho remota do Windows podem ser restritos a mesma sessão de área de trabalho remota do Windows, a menos que eles têm privilégios elevados.  
  
> [!WARNING]
>  Ao usar o transporte de pipe nomeado com uma reserva de URL curinga fraco em vários sites hospedados no IIS, o seguinte erro pode ocorrer: Ocorreu um erro no serviço de ativação NetPipeActivator do protocolo 'NET. pipe' ao tentar ouvir o site '2' Portanto, o protocolo está desabilitado para o site temporariamente. Consulte a mensagem de exceção para obter mais detalhes. URL: WeakWildcard:net.pipe:/\<nome do computador > / Status: exceção ConflictingRegistration: o nome do processo: ID do processo do SMSvcHost: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Pontos de decisão para a escolha de um transporte  
 A tabela a seguir descreve os pontos de decisão comum usados para escolher um transporte. Você deve considerar as transportes que se aplicam ao seu aplicativo e os atributos adicionais. Identificar os atributos que são importantes para seu aplicativo, identifique os transportes que associam favorável com cada um dos seus atributos e, em seguida, selecione os transportes que funcionam melhor com o conjunto de atributos.  
  
|Atributo|Descrição|Transportes favorecidos|  
|---------------|-----------------|------------------------|  
|Diagnóstico|Diagnóstico permitem que você detecte automaticamente os problemas de conectividade de transporte. Suportam a todos os transportes a capacidade de enviar informações de falha de backup que descreve a conectividade. No entanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não inclui ferramentas de diagnóstico para investigar problemas de rede.|Nenhum|  
|Hospedagem|Todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pontos de extremidade devem ser hospedados dentro de um aplicativo. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] e suporte anterior hospeda somente aplicativos que usam o transporte HTTP. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], é adicionado suporte para hospedagem todos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transportes, incluindo TCP e pipes nomeados. Para obter mais informações, consulte [hospedagem no Internet Information Services](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) e [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Inspeção|Inspeção é a capacidade para extrair e processar informações de mensagens durante a transmissão. O protocolo HTTP separa as informações de roteamento e controle de dados, tornando mais fácil criar ferramentas que Inspecione e analisar as mensagens. Transportes que são fáceis de inspecionar também podem exigir menos capacidade de processamento em dispositivos de rede. O nível de segurança usado impactos se mensagens podem ser inspecionadas.|HTTP|  
|Latência|Latência é a quantidade mínima de tempo necessário para concluir uma troca de mensagens. Todas as operações de rede tem mais ou menos latência dependendo da opção de transporte. Usando a comunicação duplex ou unidirecional com um transporte cujo padrão de troca de mensagem nativo é de solicitação-resposta, como HTTP, pode fazer com que a latência adicional devido a correlação forçada de mensagens. Nessa situação, considere o uso de um transporte cujo padrão de troca de mensagem nativo é duplex, como TCP.|TCP, denominado<br /><br /> pipe|  
|Alcance|O alcance de um transporte reflete como compatível com o transporte é ao conectar-se com outros sistemas. O transporte de pipe nomeado tem muito pouco alcance; ele só pode se conectar aos serviços em execução no mesmo computador. Os transportes HTTP e TCP têm excelente alcance e podem entrar na algumas configurações de firewall e NAT. Para obter mais informações, consulte [trabalhando com NATs e Firewalls](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Segurança|A segurança é a capacidade de proteger as mensagens durante a transferência, fornecendo a confidencialidade, integridade ou autenticação. Confidencialidade impede que uma mensagem que está sendo examinado, integridade impede que uma mensagem que está sendo modificado e autenticação oferece garantias sobre o remetente ou destinatário da mensagem.<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte à segurança de transferência tanto no nível de mensagem e nível de transporte. Segurança de mensagem compõe com um transporte, se o transporte dá suporte a um modo de transferência em buffer. Suporte para segurança de transporte varia dependendo do transporte escolhido. O HTTP, TCP e transportes de pipe nomeado tem paridade razoável em relação ao suporte para segurança de transporte.|Todos|  
|Taxa de transferência|Taxa de transferência mede a quantidade de dados que podem ser transmitidos e processados em um período de tempo especificado. Como a latência, o transporte escolhido pode afetar a taxa de transferência para operações de serviço. Maximizar taxa de transferência para um transporte requer minimizando os dois a sobrecarga de transmitir conteúdo, bem como para minimizar o tempo gasto aguardando trocas de mensagens concluir. O TCP e o pipe nomeado transportes adicionar pouca sobrecarga para o corpo da mensagem e dar suporte a uma forma de duplex nativo que reduz a espera por respostas de mensagens.|TCP, pipe nomeado|  
|Ferramentas|Ferramentas representa o suporte a aplicativos de terceiros para um protocolo para o desenvolvimento, o diagnóstico, hospedagem e outras atividades. Desenvolvimento de software para funcionar com o protocolo HTTP e ferramentas significa um investimento muito grande.|HTTP|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
  <<!--zz <xref:System.ServiceModel.WsDualHttpBinding> --> `System.ServiceModel.WsDualHttpBinding`
 <<!--zz <xref:System.ServiceModel.WsFederationHttpBinding>  --> `System.ServiceModel.WsFederationHttpBinding` <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 [Associações](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Criando associações definidas pelo usuário](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
