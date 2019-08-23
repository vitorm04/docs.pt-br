---
title: Adicionando status online e offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 74b113d64003756982a6b5701d9601c3116a9046
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960653"
---
# <a name="adding-online-and-offline-status"></a>Adicionando status online e offline
Em muitos casos, é importante que um aplicativo monitore detalhes específicos sobre o status de uma conexão de canal de mesmo nível. Você pode obter essas informações chamando o `GetProperty` método em uma implementação <xref:System.ServiceModel.IOnlineStatus> da interface. Um objeto com uma implementação dessa interface pode monitorar o status da conexão ou registrar-se para manipuladores de `OnOnline` eventos `OnOffline`, como e e reagir imediatamente conforme as alterações no status online ocorrem.  
  
 Na infraestrutura de canal par, um cliente será considerado online se estiver conectado a pelo menos um outro par e offline do contrário. Isso pode ser particularmente útil na depuração de aplicativos de desenvolvimento ou na exibição de informações detalhadas para o usuário final.  
  
> [!NOTE]
> Um manipulador de eventos online deve primeiro garantir que o nó esteja aberto antes de enviar qualquer mensagem.  
  
## <a name="see-also"></a>Consulte também

- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
