---
title: 'Como: implantar um aplicativo de integração COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 281fe0fb93fffb84f85f19b42e8d90e86dc300c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146725"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Como: implantar um aplicativo de integração COM+
Quando você tiver gravado um aplicativo COM+ integration, você talvez queira implantá-lo em outro computador. Este tópico descreve como mover um aplicativo de integração COM+ de um computador para outro.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Mover um COM+ hospedou o aplicativo de integração  
  
1.  Certifique-se de que o WCF está instalado em ambos os computadores.  
  
2.  Exportar o aplicativo do computador A.  
  
3.  Importe o aplicativo no computador B.  
  
4.  Defina o diretório raiz do aplicativo. Por convenção, isso é %PROGRAMFILES%/ComPlus aplicativos / {AppGUID}.  
  
5.  Copie os arquivos config e Application.manifest do diretório raiz do aplicativo em um computador para o diretório raiz do aplicativo no computador B.  
  
6.  Edite os endereços de ponto de extremidade de serviço no arquivo config no computador B para identificar a máquina apropriada. Por exemplo, altere `http://machineA/MyService` para `http://machineB/MyService`.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Mover um aplicativo hospedado na Web de integração  
  
1.  Certifique-se de que o WCF está instalado em ambos os computadores.  
  
2.  Exportar o aplicativo do computador A.  
  
3.  Importe o aplicativo no computador B.  
  
4.  Criar uma raiz virtual do IIS no computador B.  
  
5.  Copiar o arquivo. svc (componentName.svc) e o arquivo Web. config do vroot na máquina A para o vroot recém-criado no computador B.  
  
## <a name="see-also"></a>Consulte também

- [Integração com visão geral de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [Como: definir configurações de serviço de COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [Como: usar a ferramenta de configuração do modelo de serviço COM+](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
