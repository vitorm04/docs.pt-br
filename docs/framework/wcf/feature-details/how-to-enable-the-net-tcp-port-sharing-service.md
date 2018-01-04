---
title: "Como habilitar o serviço de compartilhamento de porta Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f1c57f067fa7c8bece3acaf0d51303b31d13bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Como habilitar o serviço de compartilhamento de porta Net.TCP
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usa um serviço do Windows chamado o serviço de compartilhamento de porta NET. TCP para facilitar o compartilhamento de portas TCP entre vários processos. Este serviço é instalado como parte do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], mas o serviço não está habilitado por padrão como uma precaução de segurança e portanto devem ser habilitadas manualmente antes de usar pela primeira vez. Este tópico descreve como configurar o serviço de compartilhamento de porta de TCP Net usando o snap-In do Console de gerenciamento Microsoft (MMC).  
  
 Depois de habilitar o serviço de compartilhamento de porta NET. TCP e iniciá-lo manualmente, consulte [como: configurar um serviço WCF para usar o compartilhamento de porta](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) para obter informações sobre como configurar seu serviço para usar este serviço.  
  
 Para obter um exemplo que usa o compartilhamento de porta net.tcp://, consulte o [exemplo de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Para habilitar o usando o MMC Serviço de compartilhamento de porta de NET. TCP  
  
1.  No menu Iniciar, abra o Console de gerenciamento de serviços, abrindo uma janela de Prompt de comando e digitando `services.msc` ou abrindo executar e digitando `services.msc` na caixa Abrir.  
  
2.  No **nome** coluna da lista de serviços, clique com botão direito do **serviço de compartilhamento de porta NET. TCP**e selecione **propriedades** no menu.  
  
3.  Para habilitar a inicialização manual do serviço, no **propriedades** janela Selecionar o **geral** guia e no **tipo de inicialização** caixa de seleção Manual e, em seguida, clique em **Aplicar**.  
  
4.  Para iniciar o serviço, na área de status do serviço, clique o **iniciar** botão. O status do serviço agora deve exibir "Iniciado".  
  
5.  Para retornar à lista de serviços, clique o **Okey**e saia do Console do MMC.  
  
## <a name="example"></a>Exemplo  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhamento de porta do NET.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Configurando o serviço de compartilhamento de porta NET.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
