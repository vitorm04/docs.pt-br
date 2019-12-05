---
title: Implantando aplicativos do WCF com um clique
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: b520931751bbba00d440b46657962ad3f1e41cd3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802226"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>Implantando aplicativos do WCF com um clique
Aplicativos cliente que usam Windows Communication Foundation (WCF) podem ser implantados usando a tecnologia ClickOnce. Essa tecnologia permite que eles aproveitem as proteções de segurança de tempo de execução fornecidas pela segurança de acesso ao código, desde que sejam assinadas digitalmente com um certificado confiável. O certificado usado para assinar o aplicativo ClickOnce deve residir no repositório de fornecedores confiáveis, e a política de segurança local no computador cliente deve ser configurada para conceder permissões de confiança total a aplicativos assinados com o certificado do Publicador.  
  
 Para obter informações sobre como configurar aplicativos ClickOnce e editores confiáveis, consulte [Configurando editores confiáveis do ClickOnce](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview)
- [Implantação do ClickOnce para aplicativos Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
