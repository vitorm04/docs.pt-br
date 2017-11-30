---
title: "Como implantar uma aplicação de integração + COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d6d9103c2d36de81392858fedc249be9f7ae94f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a>Como implantar uma aplicação de integração + COM
Uma vez você gravou um aplicativo COM+ integration, você talvez queira implantá-lo em outro computador. Este tópico descreve como mover um aplicativo de integração COM+ de um computador para outro.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Mover um COM+ hospedado integração do aplicativo  
  
1.  Certifique-se de que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está instalado nos dois computadores.  
  
2.  Exportar o aplicativo de máquina A.  
  
3.  Importe o aplicativo na máquina B.  
  
4.  Defina o diretório raiz do aplicativo. Por convenção, isso é %PROGRAMFILES%/ComPlus aplicativos / {AppGUID}.  
  
5.  Copie os arquivos config e Application.manifest do diretório raiz do aplicativo em um computador para o diretório raiz do aplicativo na máquina B.  
  
6.  Edite os endereços de ponto de extremidade de serviço no arquivo config no computador B para identificar o computador apropriado. Por exemplo, altere http://machineA/MyService para http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Mover um aplicativo Web hospedado integração  
  
1.  Certifique-se de que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está instalado nos dois computadores.  
  
2.  Exportar o aplicativo de máquina A.  
  
3.  Importe o aplicativo na máquina B.  
  
4.  Crie uma vroot do IIS no computador B.  
  
5.  Copiar o arquivo. svc (componentName.svc) e o arquivo Web. config de vroot em um computador para o vroot recém-criado na máquina B.  
  
## <a name="see-also"></a>Consulte também  
 [Integração com visão geral de aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Como: definir configurações de serviço COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Como: usar a ferramenta de configuração de modelo de serviço COM+](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
