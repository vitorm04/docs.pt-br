---
title: Ativação com base em configuração no ISS e WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: d15202a7d34f3246cd7679687b6a510252fe3541
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541338"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Ativação com base em configuração no ISS e WAS
Normalmente, ao hospedar um serviço do Windows Communication Foundation (WCF) em serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS), você deve fornecer um arquivo. svc. O arquivo. svc contém o nome do serviço e uma fábrica do host de serviço personalizado opcional. Este arquivo adicional aumenta a sobrecarga de capacidade de gerenciamento. O recurso de ativação baseada em configuração remove o requisito de ter um arquivo. svc e, portanto, os respectivos sobrecarga.  
  
## <a name="configuration-based-activation"></a>Ativação com base em configuração  
 Ativação baseada em configuração leva os metadados que costumava ser colocado no arquivo. svc e o coloca no arquivo Web. config. Dentro de <`serviceHostingEnvironment`> elemento, há um <`serviceActivations`> elemento. Dentro de <`serviceActivations`> elemento são um ou mais <`add`> elementos, um para cada serviço hospedado. O <`add`> elemento contém atributos que permitem que você defina o endereço relativo para o serviço e o tipo de serviço ou uma fábrica do host de serviço. O código de exemplo de configuração a seguir mostra como esta seção é usada.  
  
> [!NOTE]
>  Cada <`add`> elemento deve especificar um serviço ou um atributo de fábrica. É permitido especificar atributos de serviço e a fábrica.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Com isso no arquivo Web. config, você pode colocar o código-fonte de serviço no diretório App_Code do aplicativo ou um assembly compilado no diretório Bin do aplicativo.  
  
> [!NOTE]
>  -   Ao usar a ativação baseada em configuração, não há suporte para código embutido em arquivos. svc.  
> -   O `relativeAddress` atributo deve ser definido como um endereço relativo, como "\<subdiretório > / SVC" ou "~ /\<sub directory/SVC".  
> -   Uma exceção de configuração é gerada se você registrar um endereço relativo que não tem uma extensão conhecida associada com o WCF.  
> -   O endereço relativo especificado é relativo à raiz do aplicativo virtual.  
> -   Devido ao modelo hierárquico de configuração, os endereços relativos registrados no nível de máquina e o site são herdados por aplicativos virtuais.  
> -   Registros em um arquivo de configuração têm precedência sobre as configurações em um. svc,. xamlx,. xoml ou outro arquivo.  
> -   Qualquer ' \' (barras invertidas) em um URI enviado para o IIS / WAS são convertidos automaticamente em um '/' (barra). Se um endereço relativo é adicionado, que contém um ' \' e enviar um URI que usa o endereço relativo do IIS, a barra invertida é convertida em uma barra invertida e o IIS não pode corresponder ao endereço relativo. O IIS enviará informações de rastreamento que indica que não há nenhuma correspondência encontrada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Hospedando serviços](../../../../docs/framework/wcf/hosting-services.md)  
 [Visão geral dos serviços de fluxo de trabalho de hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
