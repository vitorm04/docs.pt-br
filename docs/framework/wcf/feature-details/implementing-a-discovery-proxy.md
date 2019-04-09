---
title: Implementando um proxy de descoberta
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140992"
---
# <a name="implementing-a-discovery-proxy"></a>Implementando um proxy de descoberta
Esta seção descreve as etapas necessárias para implementar um proxy de descoberta. Um proxy de descoberta é um serviço autônomo que contém um repositório de serviços. Os clientes podem consultar um proxy de descoberta para localizar serviços podem ser descobertos que o proxy está ciente. Como um proxy é preenchido com os serviços cabe ao implementador. Por exemplo, um proxy de descoberta pode se conectar a um repositório de serviço existente e tornar essas informações detectáveis, um administrador pode usar uma API de gerenciamento para adicionar serviços podem ser descobertos para um proxy ou um proxy de descoberta pode usar a funcionalidade de anúncio Atualize seu cache interno.  
  
 A implementação do WCF fornece as classes base que permitem que você crie facilmente um proxy. Você pode usar essas APIs para criar um Proxy de descoberta na parte superior de seu repositório existente.  
  
 O proxy de descoberta implementado aqui é como qualquer outro serviço do WCF, em que você também pode fazer o proxy de descoberta podem ser descobertos e fazer com que os clientes localizar seus pontos de extremidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: implementar um proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Descreve como implementar um proxy de descoberta.  
  
 [Como: implementar um serviço de descoberta que registra usando o proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Descreve como implementar um serviço WCF de descoberta que registra com o proxy de descoberta.  
  
 [Como: implementar um aplicativo cliente que utiliza o proxy de descoberta para encontrar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Descreve como implementar um aplicativo de cliente do WCF que usa o proxy de descoberta para pesquisar para um serviço.  
  
 [Como: testar o proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Descreve como testar o código escrito em três tópicos anteriores.  
  
## <a name="see-also"></a>Consulte também

- [Descoberta de WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [Como: adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
