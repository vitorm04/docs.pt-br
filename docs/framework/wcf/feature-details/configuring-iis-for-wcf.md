---
title: Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 13fd068f7a058a0fbf4e15fc99a8de91671fb2d5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664612"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation

Serviços de informações da Internet (IIS) 7.0 tem um design modular que permite que você instale seletivamente os componentes que são necessários. Esse design se baseia na tecnologia componentização controlado por manifesto novo introduzida no [!INCLUDE[wv](../../../../includes/wv-md.md)]. Há mais de 40 componentes de recurso autônomo do IIS 7.0 que pode ser instalado de forma independente. Isso permite que os profissionais de TI personalizar facilmente a instalação conforme necessário. Este tópico discute como configurar o IIS 7.0 para uso com o Windows Communication Foundation (WCF) e determinar quais componentes são necessários.

## <a name="minimal-installation-installing-was"></a>Instalação mínima: A instalação do WAS
 A instalação mínima do pacote completo do IIS 7.0 é instalar o serviço de ativação de processos do Windows (WAS). FOI é um recurso autônomo e é o único recurso do IIS 7.0 que está disponível para todos os [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas operacionais (Home Basic, Home Premium, Business e Ultimate e Enterprise).

 No painel de controle, clique em **programas** e, em seguida, clique em **ativar ou desativar recursos do Windows ativar** que está listado no **programas e recursos**, o componente WAS é mostrado no lista, como mostra a ilustração a seguir.

 ![Recursos de ativar ou desativar o diálogo](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Esse recurso tem os seguintes subcomponentes:

-   Ambiente .NET

-   APIs de configuração

-   Modelo de processo

 Se você selecionar o nó raiz do WAS, somente o **modelo de processo** subnó é marcada por padrão. Observe que a instalação você está instalando WAS, apenas porque não há suporte para um servidor Web.

 Para tornar o WCF ou qualquer trabalho de aplicativo do ASP.NET, verifique as **ambiente .NET** caixa de seleção. Isso significa que todos os componentes do WAS são necessários para tornar o WCF e ASP.NET para funcionar bem. Eles são verificados automaticamente depois de instalar qualquer um desses componentes.

## <a name="iis-70-default-installation"></a>IIS 7.0: Instalação padrão
 Verificando a **serviços de informações da Internet** recurso, alguns de nós subpropriedades são verificados automaticamente, conforme mostrado na ilustração a seguir.

 ![Configurações padrão para recursos do IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Isso é a instalação padrão do IIS 7.0. Com essa instalação, você pode usar o IIS 7.0 para conteúdo estático do serviço (como páginas HTML e outros tipos de conteúdo). No entanto, é possível executar aplicativos ASP.NET ou CGI ou hospedar serviços WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0: Instalação com suporte do ASP.NET
 Você deve instalar o ASP.NET para fazer com que o ASP.NET funcionar no IIS 7.0. Depois de verificar **ASP.NET**, sua tela deve ser semelhante a ilustração a seguir.

 ![As configurações necessárias do Asp.NET](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Isso é o ambiente mínima para aplicativos WCF e ASP.NET funcionar no IIS 7.0.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0: Instalação com componentes de compatibilidade 6.0 do IIS
 Ao instalar o IIS 7.0 em um sistema com o Visual Studio 2005 ou alguns outros scripts de automação ou ferramentas (como Adsutil. vbs) que configuram aplicativos virtuais que usam a API de Metabase do IIS 6.0, certifique-se de que você verifique o IIS 6.0 **as ferramentas de script**. Isso verifica automaticamente os outros nós do IIS 6.0 subpropriedades **compatibilidade com gerenciamento**. A ilustração a seguir mostra a tela depois que isso é feito:

 ![Configurações de compatibilidade do IIS 6.0 gerenciamento](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Com esta instalação, você tem tudo que é necessário usar recursos do IIS 7.0, ASP.NET e WCF e exemplos disponíveis na Web.

## <a name="request-limits"></a>Limites de solicitações
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] com o valor padrão do IIS 7 da `maxUri` e `maxQueryStringSize` configurações foram alteradas. Por padrão, a filtragem de solicitações no IIS 7.0 permite que um comprimento de URL de 4096 caracteres e um comprimento de cadeia de caracteres de consulta de 2048 caracteres. Para alterar esses padrões adicione o seguinte XML ao seu arquivo App. config.

 `<system.webServer>`

 `<security>`

 `<requestFiltering>`

 `<requestLimits maxUrl="8192" maxQueryString="8192" />`

 `</requestFiltering>`

 `</security>`

 `</system.webServer>`

## <a name="see-also"></a>Consulte também

- [Arquitetura de ativação WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Como instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
