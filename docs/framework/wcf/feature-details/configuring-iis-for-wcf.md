---
title: Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 369fd641adc91c58a676a7c2708e267366d73b41
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838046"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Configurando os Serviços de informação da internet 7.0 para o Windows Communication Foundation

O Serviços de Informações da Internet (IIS) 7,0 tem um design modular que permite que você instale seletivamente os componentes necessários. Esse design se baseia na nova tecnologia de componentização orientada por manifesto introduzida no Windows Vista. Há mais de 40 componentes de recursos autônomos do IIS 7,0 que podem ser instalados de forma independente. Isso permite que os profissionais de ti personalizem facilmente a instalação conforme necessário. Este tópico discute como configurar o IIS 7,0 para uso com o Windows Communication Foundation (WCF) e determinar quais componentes são necessários.

## <a name="minimal-installation-installing-was"></a>Instalação mínima: a instalação do foi
 A instalação mínima de todo o pacote do IIS 7,0 é instalar o WAS (serviço de ativação de processos do Windows). O WAS é um recurso autônomo e é o único recurso do IIS 7,0 que está disponível para todos os sistemas operacionais Windows Vista (Home Basic, Home Premium, Business e Ultimate e Enterprise).

 No painel de controle, clique em **programas** e, em seguida, clique em **Ativar ou desativar recursos do Windows** , que está listado em **programas e recursos**, o componente was é mostrado na lista como na ilustração a seguir.

 ![Caixa de diálogo ativar ou desativar recursos](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Este recurso tem os seguintes subcomponentes:

- Ambiente .NET

- APIs de Configuração

- Modelo de Processo

 Se você selecionar o nó raiz do WAS, somente o subnó do **modelo de processo** será verificado por padrão. Observe que, com essa instalação, você está instalando o WAS, porque não há suporte para um servidor Web.

 Para fazer com que o WCF ou qualquer aplicativo ASP.NET funcione, marque a caixa de seleção **ambiente .net** . Isso significa que todos os componentes do WAS são necessários para fazer com que o WCF e o ASP.NET funcionem bem. Eles são verificados automaticamente após a instalação de qualquer um desses componentes.

## <a name="iis-70-default-installation"></a>IIS 7,0: instalação padrão
 Ao verificar o recurso **serviços de informações da Internet** , alguns dos subnós são automaticamente verificados, conforme mostrado na ilustração a seguir.

 ![Configurações padrão para recursos do IIS 7,0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Esta é a instalação padrão do IIS 7,0. Com essa instalação, você pode usar o IIS 7,0 para serviço de conteúdo estático (como páginas HTML e outro conteúdo). No entanto, você não pode executar aplicativos ASP.NET ou CGI nem hospedar serviços WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7,0: instalação com suporte a ASP.NET
 Você deve instalar o ASP.NET para fazer com que o ASP.NET funcione no IIS 7,0. Depois de verificar **ASP.net**, sua tela deve ser parecida com a ilustração a seguir.

 ![Asp.NET configurações necessárias](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Esse é o ambiente mínimo para que os aplicativos WCF e ASP.NET funcionem no IIS 7,0.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7,0: instalação com componentes de compatibilidade do IIS 6,0
 Ao instalar o IIS 7,0 em um sistema com o Visual Studio 2005 ou outros scripts ou ferramentas de automação (como Adsutil. vbs) que configuram aplicativos virtuais que usam a API de metabase do IIS 6,0, verifique as **ferramentas de script**do IIS 6,0. Isso verifica automaticamente os outros subnós da **compatibilidade de gerenciamento**do IIS 6,0. A ilustração a seguir mostra a tela depois que isso é feito:

 ![Configurações de compatibilidade de gerenciamento do IIS 6,0](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Com essa instalação, você tem tudo o que é necessário para usar os recursos do IIS 7,0, ASP.NET e WCF e exemplos disponíveis na Web.

## <a name="request-limits"></a>Limites de solicitações
 No Windows Vista com IIS 7, o valor padrão do `maxUri` e as configurações de `maxQueryStringSize` foram alteradas. Por padrão, a filtragem de solicitações no IIS 7,0 permite um comprimento de URL de 4096 caracteres e um comprimento de cadeia de caracteres de consulta de 2048 caracteres. Para alterar esses padrões, adicione o seguinte XML ao seu arquivo app. config.

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>Consulte também

- [Arquitetura de ativação WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Como instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Recursos de hospedagem do Windows Server app Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
