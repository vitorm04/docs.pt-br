---
title: Visão geral de filas
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 85c8cb1fbbda9be14754174c7cb7c76513bd94c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="queues-overview"></a>Visão geral de filas
Esta seção apresenta o geral e principais conceitos por trás de comunicação em fila. As seções subsequentes entram em detalhes sobre como os conceitos de enfileiramento de mensagens descritos aqui são manifestados no Windows Communication Foundation (WCF).  
  
## <a name="basic-queuing-concepts"></a>Conceitos básicos de enfileiramento de mensagens  
 Ao criar um aplicativo distribuído, escolhendo que o transporte à direita para a comunicação entre clientes e serviços é importante. Diversos fatores afetam o tipo de transporte a ser usado. Um fator importante — isolamento entre o serviço, o cliente e o transporte — determina o uso de um transporte em fila ou um transporte direto, como TCP ou HTTP. Devido à natureza de transportes diretas, como TCP e HTTP, comunicação interrompe completamente se o serviço ou cliente pare de funcionar ou se a rede falhar. O serviço, o cliente e a rede devem estar em execução ao mesmo tempo para o aplicativo para trabalhar. Transportes em fila fornecem isolamento, o que significa que se o serviço ou cliente falhar ou se os links de comunicação entre eles falharem, o cliente e o serviço podem continuar a funcionar.  
  
 As filas fornecem comunicação confiável mesmo com falhas em partes envolvidas na comunicação ou a rede. Filas de captura e entregam mensagens trocadas entre as partes da comunicação. Filas normalmente contam com algum tipo de um repositório, que pode ser duráveis ou voláteis. Filas de armazenam mensagens de um cliente em nome de um serviço e encaminhá-los posteriormente essas mensagens para o serviço. Indireção as filas fornecem garante o isolamento de falha por qualquer uma das partes, tornando o mecanismo de comunicação preferencial para sistemas de alta disponibilidade e desconectado de serviços. Indireção vem com o custo de alta latência. *Latência* o atraso entre a hora em que o cliente envia uma mensagem e a hora em que o serviço recebe. Isso significa que quando uma mensagem é enviada, você não souber quando essa mensagem pode ser processada. Maioria dos aplicativos em fila lidar com alta latência. A ilustração a seguir mostra um modelo conceitual de comunicação em fila.  
  
 ![Modelo de comunicação em fila](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Modelo conceitual de comunicação em fila  
  
 Na realidade, a fila é um conceito distribuído. Assim, eles podem ser local para qualquer uma das partes ou remoto para ambas as partes. Normalmente, a fila é local para o serviço. Nessa configuração, o cliente não pode depender de conectividade para a fila remota esteja sempre disponível. Da mesma forma, a fila deve ser disponível independente da disponibilidade do serviço de leitura da fila. Um Gerenciador de fila gerencia uma coleção de filas. Ele é responsável por aceitar mensagens enviadas para suas filas de outros gerenciadores de fila. Também é responsável por gerenciar a conectividade com filas remotas e transferir mensagens para essas filas remotas. Para garantir a disponibilidade de filas independentemente de falhas de aplicativo cliente ou serviço, o Gerenciador de filas normalmente é executado como um serviço externo.  
  
 Quando um cliente envia uma mensagem para uma fila, ele trata a mensagem à fila de destino, que é gerenciada pelo Gerenciador de fila do serviço fila. O Gerenciador de filas no cliente envia a mensagem para uma transmissão (ou saída) fila. A fila de transmissão é no Gerenciador de fila de cliente que armazena mensagens de transmissão à fila de destino. O Gerenciador de filas, em seguida, localiza um caminho para o Gerenciador de filas que possui a fila de destino e transfere a mensagem a ele. Para garantir uma comunicação confiável, os gerentes de fila implementam um protocolo de transferência confiável para evitar a perda de dados. O Gerenciador de filas de destino aceita as mensagens destinadas a filas de destino, ele possui e armazena as mensagens. O serviço faz solicitações de leitura da fila de destino, no momento em que o Gerenciador de filas, em seguida, envia a mensagem para o aplicativo de destino. A ilustração a seguir mostra a comunicação entre as quatro partes.  
  
 ![Na fila de diagrama do aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Comunicação em fila em um cenário típico de implantação  
  
 Portanto, o Gerenciador de fila fornece o isolamento necessário para que o remetente e o destinatário podem falhar de forma independente sem afetar a comunicação. O benefício de indireção extra que fornecem as filas também permite que várias instâncias do aplicativo leiam a mesma fila, para que o trabalho entre os nós de farming alcança maior taxa de transferência. Portanto, não é incomum ver filas que está sendo usadas para alcançar maior escala e requisitos de taxa de transferência.  
  
## <a name="queues-and-transactions"></a>Filas e transações  
 Transações permitem agrupar um conjunto de operações para que se uma operação falhar, todas as operações de falham. Um exemplo de como usar transações é quando uma pessoa que usa um caixa eletrônico para transferir US $1,000 de sua conta de economias para sua conta corrente. Isso envolve as seguintes operações:  
  
-   Retirando US $1,000 da conta de economia.  
  
-   Depósito de US $1,000 na conta corrente.  
  
 Se a primeira operação for bem-sucedida e US $1,000 é retirado da conta de economia, mas a segunda operação falhará, US $1,000 for perdida, porque já tiver sido retirado da conta de economia. Para manter as contas em um estado válido, se uma operação falhar, as duas operações devem falhar.  
  
 No sistema de mensagens transacionais, mensagens podem enviadas à fila e recebidas da fila em uma transação. Assim, se uma mensagem é enviada em uma transação e a transação é revertida, em seguida, o resultado é como se a mensagem nunca tinha foi enviado para a fila. Da mesma forma se uma mensagem é recebida em uma transação e a transação é revertida, em seguida, o resultado é como se a mensagem tinha nunca foi recebido. A mensagem permanece na fila a ser lido.  
  
 Devido à alta latência, quando você enviar uma mensagem que não há como saber quanto tempo levará para alcançar a fila de destino, nem fazer você saber quanto tempo leva para o serviço de processar a mensagem. Por isso, você não deseja usar uma única transação para enviar a mensagem, a mensagem e, em seguida, processar a mensagem. Isso cria uma transação que não é confirmada por um período indeterminado. Quando um cliente e o serviço se comunicam por meio de uma fila usando uma transação, duas transações envolvidas: um no cliente e um no serviço. A ilustração a seguir mostra os limites de transação em uma comunicação típica na fila.  
  
 ![Fila com transações](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions-Figura 3")  
  
 Mostrando transações separadas para captura e entrega de comunicação em fila  
  
 A transação de cliente processa e envia a mensagem. Quando a transação é confirmada, a mensagem está na fila de transmissão. Sobre o serviço, a transação lê a mensagem da fila de destino, processa a mensagem e, em seguida, confirma a transação. Se ocorrer um erro durante o processamento, a mensagem é revertida e colocada na fila de destino.  
  
## <a name="asynchronous-communication-using-queues"></a>Comunicação assíncrona usando filas  
 As filas fornecem um meio assíncrono de comunicação. Aplicativos que enviam usando filas de mensagens não podem esperar para a mensagem ser recebida e processada pelo destinatário, devido à alta latência apresentada pelo Gerenciador de fila. As mensagens podem permanecer na fila por muito mais tempo que o aplicativo que se destina. Para evitar isso, o aplicativo pode especificar um valor de tempo de vida da mensagem. Esse valor Especifica quanto tempo a mensagem deve permanecer na fila de transmissão. Se esse valor de tempo for excedido, e a mensagem ainda não foram enviada para a fila de destino, a mensagem pode ser transferida para uma fila de mensagens mortas.  
  
 Quando o remetente envia uma mensagem, o retorno da operação de envio implica que a mensagem somente chegou à fila de transmissão no remetente. Assim, se houver uma falha em obter a mensagem à fila de destino, o aplicativo de envio não é possível saber imediatamente. Para anote essas falhas, a mensagem de falha é transferida para uma fila de mensagens mortas.  
  
 Qualquer erro, como uma mensagem de falha alcançar a fila de destino ou o expirando Time-To-Live, deve ser processado separadamente. Não é incomum, portanto, para aplicativos em fila gravar os dois conjuntos de lógica:  
  
-   O cliente normal e lógica do serviço de envio e recebimento de mensagens.  
  
-   Lógica de compensação para lidar com mensagens de transmissão com falha ou entrega.  
  
 As seções a seguir discutem esses conceitos.  
  
## <a name="dead-letter-queue-programming"></a>Programação de fila de mensagens mortas  
 Filas de mensagens mortas contêm mensagens que falharam para chegar à fila de destino por vários motivos. Os motivos podem variar de mensagens expiradas para problemas de conectividade, impedindo que a transferência da mensagem à fila de destino.  
  
 Normalmente, um aplicativo pode ler mensagens de uma fila de mensagens mortas de todo o sistema, determinar o que deu errado e execute a ação apropriada, como corrigir os erros e reenviar a mensagem ou colocando nota.  
  
## <a name="poison-message-queue-programming"></a>Programação de fila de mensagens suspeitas  
 Depois que uma mensagem torna a fila de destino, o serviço pode falhar repetidamente processar a mensagem. Por exemplo, um aplicativo ler uma mensagem da fila em uma transação e atualizar um banco de dados podem localizar o banco de dados desconectado temporariamente. Nesse caso, a transação é revertida, uma nova transação é criada e a mensagem é reler da fila. Uma segunda tentativa pode ser bem-sucedida ou falhar. Em alguns casos, dependendo da causa do erro, a mensagem pode falhar repetidamente entrega para o aplicativo. Nesse caso, a mensagem é considerada como "suspeitas". Essas mensagens são movidas para uma fila suspeita que possa ser lido por um aplicativo de tratamento de inviabilização.  
  
## <a name="see-also"></a>Consulte também  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Filas de mensagens mortas](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 [Comunicação em fila volátil](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 [Windows Communication Foundation para Enfileiramento de Mensagens](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalando o Enfileiramento de Mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Exemplos de associação de integração de serviço de enfileiramento de mensagem](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
