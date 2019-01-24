---
title: Implementando um proxy de descoberta
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: f2f687912b966b03c17206f369b46ffd28d019d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634513"
---
# <a name="implementing-a-discovery-proxy"></a>Implementando um proxy de descoberta
Esta seção descreve as etapas necessárias para implementar um proxy de descoberta. Um proxy de descoberta é um serviço autônomo que contém um repositório de serviços. Os clientes podem consultar um proxy de descoberta para localizar serviços podem ser descobertos que o proxy está ciente. Como um proxy é preenchido com os serviços cabe ao implementador. Por exemplo, um proxy de descoberta pode se conectar a um repositório de serviço existente e tornar essas informações detectáveis, um administrador pode usar uma API de gerenciamento para adicionar serviços podem ser descobertos para um proxy ou um proxy de descoberta pode usar a funcionalidade de anúncio Atualize seu cache interno.  
  
 A implementação do WCF fornece as classes base que permitem que você crie facilmente um proxy. Você pode usar essas APIs para criar um Proxy de descoberta na parte superior de seu repositório existente.  
  
 O proxy de descoberta implementado aqui é como qualquer outro serviço do WCF, em que você também pode fazer o proxy de descoberta podem ser descobertos e fazer com que os clientes localizar seus pontos de extremidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Implementar um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Descreve como implementar um proxy de descoberta.  
  
 [Como: Implementar um serviço de descoberta que registra com o Proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Descreve como implementar um serviço WCF de descoberta que registra com o proxy de descoberta.  
  
 [Como: Implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Descreve como implementar um aplicativo de cliente do WCF que usa o proxy de descoberta para pesquisar para um serviço.  
  
 [Como: O Proxy de descoberta de teste](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Descreve como testar o código escrito em três tópicos anteriores.  
  
## <a name="see-also"></a>Consulte também
- [Descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [Como: Adicionar programaticamente a capacidade de descoberta para um cliente e serviço do WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
