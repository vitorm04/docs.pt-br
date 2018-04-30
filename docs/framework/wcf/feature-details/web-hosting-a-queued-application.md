---
title: Hospedando na Web um aplicativo em fila
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b7168d5283a0dbe1001631f855e493335576a80
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="web-hosting-a-queued-application"></a>Hospedando na Web um aplicativo em fila
O serviço de ativação de processos do Windows (WAS) gerencia a ativação e a vida útil dos processos de trabalho que contêm aplicativos que hospedam [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços. O modelo de processo WAS generaliza o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] modelo de processo para o servidor HTTP, removendo a dependência no HTTP. Isso permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services para usar HTTP e protocolos não HTTP, como NET. MSMQ e FormatName, em um ambiente de hospedagem que oferece suporte à ativação baseada em mensagem e oferece a capacidade de hospedar um grande número de aplicativos em um determinado computador.  
  
 FOI inclui um serviço de ativação de enfileiramento de mensagens (MSMQ) que ativa um aplicativo em fila quando uma ou mais mensagens são colocadas em uma das filas usadas pelo aplicativo. O serviço de ativação MSMQ é um serviço do NT é iniciado automaticamente por padrão.  
  
 Para obter mais informações sobre o WAS e seus benefícios, consulte [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). Para obter mais informações sobre o MSMQ, consulte [visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
  
## <a name="queue-addressing-in-was"></a>Fila de endereçamento no WAS  
 FOI aplicativos têm endereços de identificador de recurso uniforme (URI). Endereços de aplicativo têm duas partes: um prefixo URI base e um endereço específico do aplicativo, relativo (caminho). Essas duas partes fornecem o endereço externo para um aplicativo quando unidas. O prefixo URI base é construído com a associação do site e é usado para todos os aplicativos sob o site, por exemplo, "net.msmq://localhost", "msmq.formatname://localhost" ou "net.tcp://localhost". Endereços de aplicativo, em seguida, são construídos colocando os fragmentos de caminho específico do aplicativo (como "/ applicationOne") e anexando-los para o URI de base do prefixo para chegar a todo o aplicativo URI, por exemplo, "net.msmq://localhost/applicationOne".  
  
 O serviço de ativação MSMQ usa o URI do aplicativo para corresponder a fila que o serviço de ativação MSMQ deve monitorar para mensagens. Quando o serviço de ativação MSMQ é iniciado, ele enumerará todas as filas públicas e particulares no computador em que ele está configurado para receber e monitorá-los para mensagens. A cada 10 minutos, o serviço de ativação MSMQ atualiza a lista de filas para monitorar. Quando uma mensagem é encontrada em uma fila, o serviço de ativação corresponde ao nome de fila para o URI do aplicativo mais longo correspondente para a associação de NET. MSMQ e ativa o aplicativo.  
  
> [!NOTE]
>  O aplicativo que está sendo ativado deve corresponder (correspondência mais longa), o prefixo do nome da fila.  
  
 Por exemplo, um nome de fila é: msmqWebHost/orderProcessing/service.svc. Se o aplicativo 1 tem um /msmqWebHost/orderProcessing do diretório virtual com um SVC sob ele, e 2 do aplicativo tiver /msmqWebHost um diretório virtual com um orderProcessing.svc sob ele, 1 de aplicativo está ativado. Se o aplicativo 1 é excluído, 2 de aplicativo está ativado.  
  
> [!NOTE]
>  Quando uma fila é criada, todas as mensagens enviadas a ele não ativar um aplicativo até que o serviço de ativação MSMQ atualiza a lista de fila, que é, no máximo, 10 minutos da hora em que a fila foi criada. Reiniciar o serviço de ativação atualiza a lista de filas.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>O efeito de filas públicas e privadas em tratar  
 O serviço de ativação MSMQ não faz distinção entre o monitoramento de fila pública e privada. Como tal, você não pode ter filas públicas e privadas com o mesmo nome. Se você fizer isso, um aplicativo Web hospedado pode obter ativado lendo de qualquer uma das filas.  
  
### <a name="queue-configuration-for-activation"></a>Configuração de fila para ativação  
 O serviço de ativação MSMQ é executado como serviço de rede. É o serviço que monitora filas para ativar aplicativos. Para ele ativar aplicativos da fila, a fila deve fornecer acesso de serviço de rede ao inspecionar mensagens na sua lista de controle de acesso (ACL).  
  
### <a name="poison-messaging"></a>Suspeitas de mensagens  
 Mensagem suspeita tratamento em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é tratado pelo canal, que não só detecta que uma mensagem é adulterada mas seleciona uma disposição com base na configuração de usuário. Como resultado, há uma única mensagem na fila. O aplicativo Web hospedado anula sucessivas vezes e a mensagem será movida para uma fila de repetição. Em um momento determinado, o atraso de ciclo de repetição, a mensagem é movida da fila de repetição para a fila principal para tentar novamente. Mas isso exige que o canal em fila esteja ativo. Se o aplicativo é reciclado WAS, em seguida, a mensagem permanece na fila de repetição até que outra mensagem chega na fila principal para ativar o aplicativo na fila. Nesse caso, a solução alternativa é retornar a mensagem manualmente da fila de repetição para a fila principal para reativar o aplicativo.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Subfila de mensagens e a limitação de fila do sistema  
 Um aplicativo hospedado WAS não pode ser ativado com base em mensagens em uma fila do sistema, como a fila de mensagens mortas de todo o sistema ou filas sub, como filas sub suspeitas. Essa é uma limitação para esta versão do produto.  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
