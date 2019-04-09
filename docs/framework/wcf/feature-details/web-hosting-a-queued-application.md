---
title: Hospedando na Web um aplicativo em fila
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: c44a6b5059f5294646d95b4281dcf7845b369929
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126016"
---
# <a name="web-hosting-a-queued-application"></a>Hospedando na Web um aplicativo em fila
O serviço de ativação de processos do Windows (WAS) gerencia a ativação e o tempo de vida dos processos de trabalho que contêm aplicativos que hospedar serviços do Windows Communication Foundation (WCF). O modelo de processo WAS generaliza o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] modelo de processo para o servidor HTTP, removendo a dependência no HTTP. Isso permite que os serviços do WCF para usar HTTP e protocolos não HTTP, como NET. MSMQ e FormatName, em um ambiente de hospedagem que oferece suporte à ativação baseada em mensagem e oferece a capacidade de hospedar um grande número de aplicativos em um determinado computador.  
  
 FOI inclui um serviço de ativação de enfileiramento de mensagens (MSMQ) que ativa um aplicativo na fila quando uma ou mais mensagens são colocadas em uma das filas usadas pelo aplicativo. O serviço de ativação MSMQ é um serviço NT que é iniciado automaticamente por padrão.  
  
 Para obter mais informações sobre o WAS e seus benefícios, consulte [hospedagem no serviço de ativação de processos do Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). Para obter mais informações sobre o MSMQ, consulte [visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Fila de endereçamento no WAS  
 ERA aplicativos têm endereços de identificador de recurso uniforme (URI). Endereços de aplicativo têm duas partes: um prefixo URI base e um endereço específico do aplicativo, relativo (caminho). Essas duas partes fornecem o endereço externo para um aplicativo quando unidas. O prefixo URI base é construído com a associação do site e é usado para todos os aplicativos no site, por exemplo, "net.msmq://localhost", "msmq.formatname://localhost" ou "baseaddress="NET.TCP://localhost:6080/vmmhelperservice/". Endereços de aplicativo, em seguida, são construídos por meio de fragmentos de caminho específico do aplicativo (como "/ applicationOne") e acrescentando-os ao URI de base do prefixo para chegar o aplicativo completo URI, por exemplo, "net.msmq://localhost/applicationOne".  
  
 O serviço de ativação MSMQ usa o URI do aplicativo para corresponder a fila que o serviço de ativação MSMQ deve monitorar para mensagens. Quando o serviço de ativação MSMQ é iniciado, ele enumerará todas as filas públicas e privadas no computador em que ele está configurado para receber e monitorá-los para mensagens. A cada 10 minutos, o serviço de ativação MSMQ atualiza a lista de filas para monitorar. Quando uma mensagem é encontrada em uma fila, o serviço de ativação coincide com o nome da fila para o URI do aplicativo correspondente mais longo para a associação de NET. MSMQ e ativa o aplicativo.  
  
> [!NOTE]
>  O aplicativo que está sendo ativado deve corresponder (correspondência mais longa), o prefixo do nome da fila.  
  
 Por exemplo, um nome de fila é: msmqWebHost/orderProcessing/service.svc. Se o aplicativo 1 tem /msmqWebHost/orderProcessing um diretório virtual com um SVC nele e aplicativo 2 tem /msmqWebHost um diretório virtual com um orderProcessing.svc sob ele, aplicativo 1 está ativado. Se o aplicativo 1 é excluído, 2 de aplicativo está ativado.  
  
> [!NOTE]
>  Quando uma fila é criada, todas as mensagens enviadas a ele não ativar um aplicativo até que o serviço de ativação MSMQ atualiza a lista de fila, que é, no máximo, 10 minutos da hora em que a fila foi criada. Reiniciar o serviço de ativação atualiza a lista de filas.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>O efeito de filas públicas e privadas no endereçamento  
 O serviço de ativação MSMQ não faz distinção entre o monitoramento de fila pública e privada. Como tal, você não pode ter filas públicas e privadas com o mesmo nome. Se você fizer isso, um aplicativo hospedado na Web pode obter ativado lendo a qualquer uma das filas.  
  
### <a name="queue-configuration-for-activation"></a>Configuração de fila para ativação  
 O serviço de ativação MSMQ é executado como serviço de rede. É o serviço que monitora as filas para ativar aplicativos. Para que ele ativar aplicativos da fila, a fila deve fornecer para acesso ao serviço de rede inspecionar mensagens em sua lista de controle de acesso (ACL).  
  
### <a name="poison-messaging"></a>Suspeitas de mensagens  
 No WCF de tratamento de mensagens suspeitas é tratada pelo canal, que não apenas detecta que uma mensagem será suspeita, mas seleciona uma disposição com base na configuração do usuário. Como resultado, há uma única mensagem na fila. O aplicativo Web hospedado anula vezes sucessivas e a mensagem é movida para uma fila de repetição. Em um momento determinado pelo intervalo de ciclo de repetição, a mensagem é movida da fila de repetição para a fila principal para tentar novamente. Mas isso requer que o canal em fila esteja ativa. Se o aplicativo é reciclado pelo WAS, em seguida, a mensagem permanecerá na fila de repetição até que outra mensagem chega na fila principal para ativar o aplicativo na fila. Nesse caso, a solução alternativa é mover a mensagem manualmente da fila de repetição volta para a fila principal para reativar o aplicativo.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Esta opção e a limitação de fila do sistema  
 Um aplicativo hospedado do WAS não pode ser ativado com base em mensagens em uma fila do sistema, como a fila de inatividade do sistema ou subfilas como suspeitas subfilas. Essa é uma limitação para esta versão do produto.  
  
## <a name="see-also"></a>Consulte também

- [Manuseio de mensagem suspeita](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
