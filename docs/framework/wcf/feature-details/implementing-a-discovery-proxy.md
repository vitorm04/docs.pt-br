---
title: Implementando um proxy de descoberta
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 0c7086e0eecea6cc2d7494d6afda0abf056ba758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492213"
---
# <a name="implementing-a-discovery-proxy"></a>Implementando um proxy de descoberta
Esta seção descreve as etapas necessárias para implementar um proxy de descoberta. Um proxy de descoberta é um serviço autônomo que contém um repositório de serviços. Os clientes podem consultar um proxy de descoberta para localizar serviços detectáveis que o proxy está ciente do. Como um proxy é populado com os serviços é o implementador. Por exemplo, um proxy de descoberta pode se conectar a um repositório de serviço existente e fazer essas informações detectáveis, um administrador pode usar uma API de gerenciamento para adicionar serviços de descoberta para um proxy ou um proxy de descoberta pode usar a funcionalidade de lançamento para Atualize seu cache interno.  
  
 A implementação de WCF fornece classes base que permitem que você crie facilmente um proxy. Você pode usar essas APIs para criar um Proxy de descoberta sobre seu repositório existente.  
  
 O proxy de descoberta implementado aqui é como qualquer outro serviço do WCF, você também pode fazer o proxy de descoberta podem ser descobertos e com que os clientes localizar seus pontos de extremidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como implementar um proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Descreve como implementar um proxy de descoberta.  
  
 [Como implementar um serviço de descoberta que registra usando o proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Descreve como implementar um serviço WCF detectável que registra com o proxy de descoberta.  
  
 [Como implementar um aplicativo cliente que usa o proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Descreve como implementar um aplicativo de cliente do WCF que usa o proxy de descoberta para pesquisar para um serviço.  
  
 [Como testar o proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Descreve como testar o código escrito em três tópicos anteriores.  
  
## <a name="see-also"></a>Consulte também  
 [Descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Como adicionar programaticamente a capacidade de descoberta a um cliente e serviço do WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
