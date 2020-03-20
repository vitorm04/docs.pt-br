---
title: Visão geral de filas
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 78d80a88153ee15f7ab152da44801c77900f874d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184596"
---
# <a name="queues-overview"></a>Visão geral das filas

Esta seção introduz os conceitos gerais e fundamentais por trás da comunicação enfileirada. As seções subseqüentes entram em detalhes sobre como os conceitos de fila descritos aqui são manifestados na Windows Communication Foundation (WCF).  
  
## <a name="basic-queuing-concepts"></a>Conceitos básicos de enfileiramento  
 Ao projetar um aplicativo distribuído, é importante escolher o transporte certo para a comunicação entre serviços e clientes. Vários fatores afetam o tipo de transporte para usar. Um fator importante — o isolamento entre o serviço, o cliente e o transporte — determina o uso de um transporte enfileirado ou de um transporte direto, como TCP ou HTTP. Devido à natureza dos transportes diretos, como TCP e HTTP, a comunicação pára completamente se o serviço ou o cliente parar de funcionar ou se a rede falhar. O serviço, o cliente e a rede devem estar funcionando ao mesmo tempo para que o aplicativo funcione. Os transportes enfileirados proporcionam isolamento, o que significa que se o serviço ou cliente falharem ou se os links de comunicação entre eles falharem, o cliente e o serviço podem continuar funcionando.  
  
 As filas fornecem comunicação confiável mesmo com falhas nas partes comunicadoras ou na rede. Filas capturam e entregam mensagens trocadas entre as partes comunicadoras. As filas são normalmente apoiadas por algum tipo de loja, que pode ser volátil ou durável. Filas armazenam mensagens de um cliente em nome de um serviço e depois encaminham essas mensagens para o serviço. As filas de indireção proporcionam o isolamento assegurado da falha por qualquer das partes, tornando-o o mecanismo de comunicação preferido para sistemas de alta disponibilidade e serviços desconectados. A indireção vem com o custo da alta latência. *Latência* é o atraso de tempo entre o tempo em que o cliente envia uma mensagem e o tempo que o serviço recebe. Isso significa que uma vez que uma mensagem é enviada, você não sabe quando essa mensagem pode ser processada. A maioria dos aplicativos enfileirados lida com alta latência. A ilustração a seguir mostra um modelo conceitual de comunicação enfileirada.  
  
 ![Modelo de comunicação enfileirada](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual-Figure1c")  
  
 Modelo conceitual de comunicação enfileirado  
  
 Na realidade, a fila é um conceito distribuído. Como tal, eles podem ser locais para qualquer parte ou remoto para ambas as partes. Normalmente, a fila é local para o serviço. Nesta configuração, o cliente não pode depender da conectividade com a fila remota para estar constantemente disponível. Da mesma forma, a fila deve estar disponível independente da disponibilidade da leitura do serviço da fila. Um gerente de fila gerencia uma coleção de filas. É responsável por aceitar mensagens enviadas para suas filas de outros gerentes de fila. Também é responsável por gerenciar a conectividade com filas remotas e transferir mensagens para essas filas remotas. Para garantir a disponibilidade de filas apesar das falhas do cliente ou do aplicativo de serviço, o gerenciador de filas normalmente é executado como um serviço externo.  
  
 Quando um cliente envia uma mensagem para uma fila, ele direciona a mensagem para a fila de destino, que é a fila gerenciada pelo gerente de fila do serviço. O gerenciador de filas no cliente envia a mensagem para uma fila de transmissão (ou saída). A fila de transmissão é uma fila no gerenciador de filas do cliente que armazena mensagens para transmissão na fila de destino. Em seguida, o gerenciador de filas encontra um caminho para o gerenciador de filas que possui a fila de destino e transfere a mensagem para ela. Para garantir uma comunicação confiável, os gerentes de fila implementam um protocolo de transferência confiável para evitar a perda de dados. O gerente da fila de destino aceita mensagens endereçadas às filas de destino que possui e armazena as mensagens. O serviço faz solicitações de leitura da fila de destino, momento em que o gerenciador da fila entrega a mensagem para o aplicativo de destino. A ilustração a seguir mostra comunicação entre as quatro partes.  
  
 ![Diagrama de aplicativos enfileirados](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura de fila distribuída")  
  
 Comunicação enfileirada em um cenário típico de implantação  
  
 Assim, o gerenciador de filas fornece o isolamento necessário para que o remetente e o receptor possam falhar independentemente sem afetar a comunicação real. O benefício da indireção extra que as filas fornecem também permite que várias instâncias de aplicativos leiam da mesma fila, de modo que o trabalho agrícola entre os álos atinja maior rendimento. Portanto, não é incomum ver filas sendo usadas para atingir maiores exigências de escala e rendimento.  
  
## <a name="queues-and-transactions"></a>Filas e Transações  
 As transações permitem que você agrupe um conjunto de operações para que, se uma operação falhar, todas as operações falharem. Um exemplo de como usar transações é quando uma pessoa usa um caixa eletrônico para transferir US$ 1.000 de sua conta poupança para sua conta corrente. Isso implica as seguintes operações:  
  
- Sacar $1.000 da poupança.  
  
- Depositando $1.000 na conta corrente.  
  
 Se a primeira operação for bem sucedida e US$ 1.000 for retirado da conta poupança, mas a segunda operação falhar, os US$ 1.000 são perdidos porque já foram sacados da conta poupança. Para manter as contas em um estado válido, se uma operação falhar, ambas as operações devem falhar.  
  
 Nas mensagens transacionais, as mensagens podem ser enviadas para a fila e recebidas da fila uma transação. Assim, se uma mensagem é enviada em uma transação e a transação é revertida, então o resultado é como se a mensagem nunca tivesse sido enviada para a fila. Da mesma forma, se uma mensagem é recebida em uma transação e a transação é revertida, então o resultado é como se a mensagem nunca tivesse sido recebida. A mensagem permanece na fila para ser lida.  
  
 Por causa da alta latência, quando você envia uma mensagem você não tem como saber quanto tempo leva para atingir sua fila de destino, nem sabe quanto tempo leva para o serviço processar a mensagem. Por causa disso, você não quer usar uma única transação para enviar a mensagem, receber a mensagem e, em seguida, processar a mensagem. Isso cria uma transação que não é cometida por um período de tempo indeterminado. Quando um cliente e serviço se comunicam através de uma fila usando uma transação, duas transações estão envolvidas: uma no cliente e outra no serviço. A ilustração a seguir mostra os limites da transação na comunicação típica enfileirada.  
  
 ![Fila com transações](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions-Figure3")  
  
 Comunicação enfileirada mostrando transações separadas para captura e entrega  
  
 A transação do cliente processa e envia a mensagem. Quando a transação é comprometida, a mensagem está na fila de transmissão. No serviço, a transação lê a mensagem da fila de destino, processa a mensagem e, em seguida, comete a transação. Se ocorrer um erro durante o processamento, a mensagem será redirecionada e colocada na fila de destino.  
  
## <a name="asynchronous-communication-using-queues"></a>Comunicação assíncrona usando filas  
 As filas fornecem um meio assíncrono de comunicação. Os aplicativos que enviam mensagens usando filas não podem esperar que a mensagem seja recebida e processada pelo receptor devido à alta latência introduzida pelo gerente da fila. As mensagens podem permanecer na fila por muito mais tempo do que o aplicativo pretendia. Para evitar isso, o aplicativo pode especificar um valor time-to-live na mensagem. Este valor especifica quanto tempo a mensagem deve permanecer na fila de transmissão. Se esse valor de tempo for excedido e a mensagem ainda não tiver sido enviada para a fila de destino, a mensagem poderá ser transferida para uma fila de letras mortas.  
  
 Quando o remetente envia uma mensagem, o retorno da operação enviar implica que a mensagem só chegou à fila de transmissão no remetente. Como tal, se houver uma falha na obtenção da mensagem para a fila de destino, o aplicativo de envio não poderá saber sobre ela imediatamente. Para tomar nota de tais falhas, a mensagem falha é transferida para uma fila de letras mortas.  
  
 Qualquer erro, como uma mensagem que não atinja a fila de destino ou o vencimento do Time-To-Live, deve ser processado separadamente. Não é incomum, portanto, que aplicativos enfileirados escrevam dois conjuntos de lógica:  
  
- A lógica normal de cliente e serviço de envio e recebimento de mensagens.  
  
- Lógica de compensação para lidar com mensagens da transmissão ou entrega falhadas.  
  
 As seções a seguir discutem esses conceitos.  
  
## <a name="dead-letter-queue-programming"></a>Programação da fila de letras mortas  
 Filas de letras mortas contêm mensagens que não atingiram a fila de destino por várias razões. As razões podem variar de mensagens expiradas a problemas de conectividade impedindo a transferência da mensagem para a fila de destino.  
  
 Normalmente, um aplicativo pode ler mensagens de uma fila de letras mortas em todo o sistema, determinar o que deu errado e tomar medidas apropriadas, como corrigir os erros e reenviar a mensagem ou tomar nota dela.  
  
## <a name="poison-message-queue-programming"></a>Programação da fila da mensagem venenosa  
 Depois que uma mensagem chega à fila de destino, o serviço pode repetidamente não processar a mensagem. Por exemplo, um aplicativo lendo uma mensagem da fila uma transação e atualizando um banco de dados pode encontrar o banco de dados temporariamente desconectado. Neste caso, a transação é revertida, uma nova transação é criada e a mensagem é relida na fila. Uma segunda tentativa pode ter sucesso ou falhar. Em alguns casos, dependendo da causa do erro, a mensagem pode falhar repetidamente na entrega do aplicativo. Neste caso, a mensagem é considerada "veneno". Essas mensagens são movidas para uma fila de veneno que pode ser lida por um aplicativo de manipulação de veneno.  
  
## <a name="see-also"></a>Confira também

- [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Filas de mensagens de inatividade](../../../../docs/framework/wcf/samples/dead-letter-queues.md)
- [Comunicação em fila volátil](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)
- [Windows Communication Foundation para Enfileiramento de Mensagens](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalando o Enfileiramento de Mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
