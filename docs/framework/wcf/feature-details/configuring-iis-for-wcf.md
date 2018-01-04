---
title: "Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 511f5177e1b9d2660daf887cc13728aed2c9de0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation
Serviços de informações da Internet (IIS) 7.0 tem um design modular que permite que você instale seletivamente os componentes necessários. Esse design é baseado na tecnologia controlada por manifesto componentização novo introduzida no [!INCLUDE[wv](../../../../includes/wv-md.md)]. Há mais de 40 componentes do recurso autônomo do [!INCLUDE[iisver](../../../../includes/iisver-md.md)] que podem ser instalados de forma independente. Isso permite que os profissionais de TI personalizar facilmente a instalação conforme necessário. Este tópico discute como configurar [!INCLUDE[iisver](../../../../includes/iisver-md.md)] para uso com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e determinar quais componentes são necessários.  
  
## <a name="minimal-installation-installing-was"></a>Instalação mínima: A instalação do WAS  
 A instalação mínima do todo [!INCLUDE[iisver](../../../../includes/iisver-md.md)] pacote é instalar o serviço de ativação de processos do Windows (WAS). FOI é um recurso autônomo e é o único recurso do [!INCLUDE[iisver](../../../../includes/iisver-md.md)] que está disponível para todos os [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas operacionais (Home Basic, Home Premium, Business e Ultimate e Enterprise).  
  
 No painel de controle, clique em **programas** e, em seguida, clique em **ativar recursos do Windows ou desativar** que é listado em **programas e recursos**, o componente WAS é mostrado no lista como a ilustração a seguir.  
  
 ![Recursos de ativar ou desativar o diálogo](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 Esse recurso tem os seguintes subcomponentes:  
  
-   Ambiente .NET  
  
-   APIs de configuração  
  
-   Modelo de processo  
  
 Se você selecionar o nó raiz do WAS, somente o **modelo de processo** subnó é marcada por padrão. Observe que a instalação está somente instalando WAS, porque não há suporte para um servidor Web.  
  
 Para fazer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou qualquer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo funcione, verifique o **ambiente .NET** caixa de seleção. Isso significa que todos os componentes do WAS são necessárias para fazer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funcione bem. Esses são verificados automaticamente depois de instalar qualquer um desses componentes.  
  
## <a name="iis-70-default-installation"></a>IIS 7.0: Instalação padrão  
 Verificando o **Internet Information Services** recurso, alguns de nós sub são verificados automaticamente, conforme mostrado na ilustração a seguir.  
  
 ![Configurações padrão para recursos do IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 Essa é a instalação padrão do [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. A instalação, você pode usar [!INCLUDE[iisver](../../../../includes/iisver-md.md)] para conteúdo estático de serviço (como páginas HTML e outros tipos de conteúdo). No entanto, não é possível executar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou aplicativos CGI ou host [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.  
  
## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0: Instalação com suporte do ASP.NET  
 Você deve instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fazer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funcionam no IIS 7.0. Depois de verificar **ASP.NET**, sua tela deve ser semelhante a ilustração a seguir.  
  
 ![As configurações necessárias do Asp.NET](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 Esse é o ambiente mínimo para ambos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativos funcionem [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0: Instalação com componentes de compatibilidade 6.0 do IIS  
 Ao instalar [!INCLUDE[iisver](../../../../includes/iisver-md.md)] em um sistema com o Visual Studio 2005 ou alguns outros scripts de automação ou ferramentas (como Adsutil.vbs) que configurar aplicativos virtuais que usam [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Metabase API, certifique-se de que você verifique o [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **Ferramentas de script**. Isso verifica automaticamente os outros nós do subdiretório [!INCLUDE[iis601](../../../../includes/iis601-md.md)] **compatibilidade com gerenciamento**. A ilustração a seguir mostra a tela após ter feito isso.  
  
 ![Configurações de compatibilidade do IIS 6.0 gerenciamento](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 Com essa instalação, você tem tudo que é necessário usar [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos e exemplos disponíveis na Web.  
  
## <a name="request-limits"></a>Limites de solicitação  
 Em [!INCLUDE[wv](../../../../includes/wv-md.md)] com o valor padrão do IIS 7 da `maxUri` e `maxQueryStringSize` configurações foram alteradas. Por padrão, a filtragem de solicitações no IIS 7.0 permitem um comprimento de URL de 4096 caracteres e um comprimento de cadeia de caracteres de consulta de 2048 caracteres. Para alterar esses padrões adicione o seguinte XML ao seu arquivo App. config.  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de ativação WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Como instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
