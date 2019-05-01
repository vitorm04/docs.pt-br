---
title: Lista de atividades
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: f96aab037e86b05096df7ffc82a0be3f6cce1ad2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998030"
---
# <a name="activity-list"></a>Lista de atividades
Este tópico lista todas as atividades definidas pelo Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Você também pode definir as atividades por meio de programação para rastreamentos de usuário do grupo. Para obter mais informações, consulte [emitindo rastreamentos de código do usuário](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Atividades de ServiceModel  
 A tabela a seguir lista todas as atividades para os principais cenários de uso.  
  
|Rotular|Nome da Atividade|Tipo de Atividade|Descrição|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Atividade de ambiente|N/d (isso não é controlado pelo ServiceModel)|A atividade cuja ID é definida no TLS antes de todas as chamadas para código de ServiceModel (do lado do cliente ou do lado do servidor).<br /><br /> Exemplo: É chamada de uma atividade onde open é chamada no cliente WCF ou ServiceHost.|  
|B|Constructo<br /><br /> ChannelFactory. ContractType: '[tipo]'.|Constructo||  
|C|Abrir<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: '[tipo]'.|Abrir||  
|I|Fechar [ClientBase&#124;ChannelFactory]. ContractType: '[tipo]'.|Fechar||  
|M|Construa o ServiceHost. ServiceType: '[tipo]'.|Constructo||  
|N|Abrir o ServiceHost. ServiceType: '[tipo]'.|Abrir||  
|Z|Feche o ServiceHost. ServiceType: '[tipo]'.|Fechar||  
|O|Escute em '[endereço]'.|ListenAt|Isso e a próxima atividade são específicas do transporte. A atividade ListenAt representa o conteúdo que é mapeado para o endereço no qual o ouvinte de canais escuta em. No caso do MSMQ, é a própria fila desde que a fila é mapeado para um endereço. Essa atividade escuta as conexões de entrada no caso de transportes e orientada a conexão, para mensagens MSMQ no caso do MSMQ. Essa atividade é criada durante a ServiceHost.Open() e contém os rastreamentos relacionados à criação e descartar o ouvinte, bem como transferindo-out para todas as atividades de ReceiveBytes.|  
|P|Receba bytes na conexão '[endereço]'. Receba mensagem MSMQ.|ReceiveBytes|Essa atividade, dados que, eventualmente, obterão uma mensagem WCF são processados. Bytes de entrada são aguardados no caso de transporte voltado para conexão ou http. Para TCP/pipes nomeados, o tempo de vida dessa atividade é o tempo de vida da conexão, como ela é criada quando a conexão é criada. Para http, ele é do tempo de vida de uma solicitação de mensagem e é criado quando a mensagem é enviada. Essa atividade contém os rastreamentos relacionados à criação e descarte a conexão, se aplicável, assim como é transferida para todas as atividades de processamento de mensagem (objeto).<br /><br /> No caso do MSMQ, ele é a atividade em que a mensagem do MSMQ é recuperada.|  
|Q|Mensagem de processo [número]. (Observe que [número] é um valor que aumenta que começa em 1.)|ProcessMessage|Processe uma mensagem de entrada. Essa atividade é iniciado quando todos os dados (bytes, a mensagem do MSMQ) são recebidos para formar um objeto de mensagem do WCF. Rastreamentos dentro desta atividade lidam com processamento de cabeçalho.<br /><br /> Depois que uma mensagem que pode ser expedida é formada, a atividade de ServiceHost ProcessAction é alternada para depois de pesquisar a ID da atividade correspondente.|  
|D, S|Processar ação '[ação]'.|ProcessAction|Processo de receber a mensagem por meio da pilha de transporte/Security/RM para expedir a mensagem ao código do usuário no, e na ordem inversa no envio.<br /><br /> No servidor, essa atividade usa a ID de atividade propagada se ele for enviado no cabeçalho da mensagem por meio de propagação de atividade""; Caso contrário, um novo GUID é criado.<br /><br /> Também é processada a mensagem de resposta para contratos de solicitação/resposta que a atividade.|  
|T|Execute '[IContract.Operation]'.|ExecuteUserCode|Execute o código do usuário após a expedição no lado do serviço. Esta atividade fornece um limite para delinear código ServiceHost do código fornecido pelo usuário.|  
  
## <a name="security-activities"></a>Atividades de segurança  
 A tabela a seguir lista todas as atividades relacionadas à segurança.  
  
|Nome da Atividade|Tipo de Atividade|Descrição|  
|-------------------|-------------------|-----------------|  
|Configuração de sessão segura|SetupSecurity|Existe somente do lado do cliente. Contém todos os RST * / SCT troca para autenticação e definir o contexto de segurança. Se `propagateActivity` = `true`, essa atividade é mesclada com o RST de ação de processo correspondente do serviço\*atividades /SCT.|  
|Fechar sessão segura|SetupSecurity|Existe no lado do cliente. Contém a troca de mensagens ' Cancelar ' para fechar a sessão segura. Se `propagateActivity` = `true`, essa atividade é mesclada com a ação "Cancelar" do processo do serviço.|  
  
 A tabela a seguir lista todas as atividades relacionadas ao COM+.  
  
|Nome da Atividade|Tipo de Atividade|Descrição|  
|-------------------|-------------------|-----------------|  
|Criar instância de COM+|TransferToCOMPlus|1 instância de atividade para cada COM+ chamar do código do WCF|  
|Executar COM+ \<operação >|TransferToCOMPlus|1 instância de atividade para cada COM+ chamar do código do WCF|  
  
## <a name="wmi-activities"></a>Atividades WMI  
 A tabela a seguir lista todas as atividades relacionadas ao WMI.  
  
|Nome da Atividade|Tipo de Atividade|Descrição|  
|-------------------|-------------------|-----------------|  
|Get WMI|WMIGetObject|Usuário está recuperando dados do WMI.|  
|Put WMI|WmiPutInstance|Usuário está atualizando dados com o WMI.|
