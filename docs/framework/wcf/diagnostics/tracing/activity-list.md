---
title: Lista de atividades
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c3b478d88eff022d8cb28f4123291f4662644ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="activity-list"></a>Lista de atividades
Este tópico lista todas as atividades definidas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
> [!NOTE]
>  Você também pode definir atividades programaticamente para rastreamentos de usuário do grupo. Para obter mais informações, consulte [emitindo rastreamentos de código de usuário](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Atividades de ServiceModel  
 A tabela a seguir lista todas as atividades para cenários de uso principal.  
  
|Rotular|Nome da Atividade|Tipo de Atividade|Descrição|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Atividade de ambiente|N/d (isso não é controlado pelo ServiceModel)|A atividade cuja ID é definido no TLS antes de qualquer chamada para o código de ServiceModel (do lado do cliente ou servidor).<br /><br /> Exemplo: Uma atividade onde open é chamada no [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] cliente ou ServiceHost é chamado.|  
|B|Constructo<br /><br /> ChannelFactory. ContractType: '[tipo]'.|Constructo||  
|C|Abrir<br /><br /> [ClientBase &#124; ChannelFactory]. ContractType: '[tipo]'.|Abrir||  
|I|Fechar [ClientBase &#124; ChannelFactory]. ContractType: '[tipo]'.|Fechar||  
|M|Construa ServiceHost. ServiceType: '[tipo]'.|Constructo||  
|N|Abrir o ServiceHost. ServiceType: '[tipo]'.|Abrir||  
|Z|Feche o ServiceHost. ServiceType: '[tipo]'.|Fechar||  
|O|Escute '[endereço]'.|ListenAt|Isso e a próxima atividade são específicas do transporte. A atividade ListenAt representa o conteúdo que é mapeado para o endereço onde a escuta de canal escuta no. No caso do MSMQ, é a própria fila desde que a fila é mapeado para um endereço. Esta atividade de escuta para conexões de entrada no caso de transportes orientado a conexão, para mensagens MSMQ no caso do MSMQ. Esta atividade é criada durante a ServiceHost.Open() e contém os rastreamentos relacionados ao criar e descartar o ouvinte, bem como transferência de limite para todas as atividades de ReceiveBytes.|  
|P|Receba bytes na conexão '[endereço]'. Mensagem do MSMQ.|ReceiveBytes|Nesta atividade, dados, eventualmente, obterão um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mensagem é processada. Bytes de entrada são aguardaram no caso de transporte orientado à conexão ou http. Para TCP/pipes nomeados, o tempo de vida dessa atividade é o tempo de vida da conexão, como ele é criado quando a conexão é criada. Para http, ele é do tempo de vida de uma solicitação de mensagem e é criado quando a mensagem é enviada. Essa atividade contém os rastreamentos relacionados à criação e descarte a conexão, se aplicável, bem como transferências de saída para todas as atividades de processamento de mensagem (objeto).<br /><br /> No caso do MSMQ, é a atividade em que a mensagem do MSMQ é recuperada.|  
|Q|Mensagem de processo [número]. (Observe que, [número] é um valor de aumentando de forma monotônica que inicia em 1.)|ProcessMessage|Processe uma mensagem de entrada. Esta atividade é iniciado quando todos os dados (em bytes, mensagem MSMQ) são recebidos para formar um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] objeto de mensagem. Rastreamentos dentro dessa atividade lidam com processamento de cabeçalho.<br /><br /> Depois que uma mensagem que pode ser distribuída é formada, a atividade de ServiceHost ProcessAction é alternada para depois de pesquisar a ID da atividade correspondente.|  
|D, S|Processar a ação '[ação]'.|ProcessAction|Processo de recebimento de mensagens por meio da pilha de transporte/Security/RM para expedir a mensagem ao código do usuário em, e na ordem inversa no envio.<br /><br /> No servidor, essa atividade usa a ID da atividade propagadas se ele for enviado no cabeçalho da mensagem por meio de propagação de atividade""; Caso contrário, é criado um novo GUID.<br /><br /> A mensagem de resposta para contratos de solicitação/resposta também é processada por essa atividade.|  
|T|Execute '[IContract.Operation]'.|ExecuteUserCode|Execute o código do usuário depois de expedição no lado do serviço. Esta atividade fornece um limite para determinar o código de ServiceHost de código fornecido pelo usuário.|  
  
## <a name="security-activities"></a>Atividades de segurança  
 A tabela a seguir lista todas as atividades relacionadas à segurança.  
  
|Nome da Atividade|Tipo de Atividade|Descrição|  
|-------------------|-------------------|-----------------|  
|Configurar sessão segura|SetupSecurity|Existe somente no cliente. Contém todos os primeira * / SCT troca para autenticação e definir o contexto de segurança. Se `propagateActivity` = `true`, essa atividade é mesclada com a primeira de ação de processo correspondente do serviço\*atividades /SCT.|  
|Fechar sessão segura|SetupSecurity|Existe no lado do cliente. Contém a troca de mensagens ' Cancelar ' para fechar a sessão segura. Se `propagateActivity` = `true`, essa atividade é mesclada com a ação "Cancelar" do processo do serviço.|  
  
 A tabela a seguir lista todas as atividades relacionadas ao COM+.  
  
|Nome da Atividade|Tipo de Atividade|Descrição|  
|-------------------|-------------------|-----------------|  
|Criar instância de COM+|TransferToCOMPlus|instância de atividade de 1 para cada chamada de COM+ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] código|  
|Executar COM+ \<operação >|TransferToCOMPlus|instância de atividade de 1 para cada chamada de COM+ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] código|  
  
## <a name="wmi-activities"></a>Atividades WMI  
 A tabela a seguir lista todas as atividades relacionadas à WMI.  
  
|Nome da Atividade|Tipo de Atividade|Descrição|  
|-------------------|-------------------|-----------------|  
|Get do WMI|WMIGetObject|Usuário está recuperando dados do WMI.|  
|Put do WMI|WmiPutInstance|Usuário está atualizando dados com o WMI.|
