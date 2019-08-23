---
title: Ativação com base em configuração no ISS e WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: f4de4aff2fbe6b8e82dc3d6523f492d06494c79e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909776"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Ativação com base em configuração no ISS e WAS

Normalmente, ao hospedar um serviço de Windows Communication Foundation (WCF) em Serviços de Informações da Internet (IIS) ou no WAS (serviço de ativação de processos do Windows), você deve fornecer um arquivo. svc. O arquivo. svc contém o nome do serviço e uma fábrica de host de serviço personalizada opcional. Esse arquivo adicional adiciona sobrecarga de gerenciabilidade. O recurso de ativação baseada em configuração remove a necessidade de ter um arquivo. svc e, portanto, a sobrecarga associada.

## <a name="configuration-based-activation"></a>Ativação com base em configuração

A ativação baseada em configuração usa os metadados que costumava ser colocados no arquivo. svc e os coloca no arquivo Web. config. Dentro do elemento`serviceHostingEnvironment`< > há um elemento <`serviceActivations`>. Dentro do elemento`serviceActivations`< > há um ou mais elementos`add`de > <, um para cada serviço hospedado. O elemento`add`< > contém atributos que permitem definir o endereço relativo para o serviço e o tipo de serviço ou uma fábrica de host de serviço. O código de exemplo de configuração a seguir mostra como essa seção é usada.

> [!NOTE]
> Cada elemento`add`de > de < deve especificar um atributo de serviço ou de fábrica. É permitido especificar os atributos de serviço e de fábrica.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Com isso no arquivo Web. config, você pode posicionar o código-fonte do serviço no diretório App_Code do aplicativo ou um assembly em conformidade no diretório bin do aplicativo.

> [!NOTE]
> - Ao usar a ativação baseada em configuração, não há suporte para código embutido em arquivos. svc.
> - O `relativeAddress` atributo deve ser definido como um endereço relativo, como "\<subdiretório >/Service.svc" ou "~/\<sub-Directory/Service. svc".
> - Uma exceção de configuração será gerada se você registrar um endereço relativo que não tenha uma extensão conhecida associada ao WCF.
> - O endereço relativo especificado é relativo à raiz do aplicativo virtual.
> - Devido ao modelo hierárquico da configuração, os endereços relativos registrados no nível do computador e do site são herdados por aplicativos virtuais.
> - Os registros em um arquivo de configuração têm precedência sobre as configurações em um. svc,. xamlx,. xoml ou outro arquivo.
> - Qualquer ' \ ' (barras invertidas) em um URI enviado para o IIS/WAS é convertido automaticamente em um '/' (barra "/"). Se um endereço relativo for adicionado que contenha um ' \ ' e você enviar um URI que usa o endereço relativo, a barra invertida será convertida em uma barra e o IIS não poderá corresponder ao endereço relativo. O IIS envia informações de rastreamento que indicam que não foram encontradas correspondências.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Hospedando serviços](../../../../docs/framework/wcf/hosting-services.md)
- [Visão geral dos serviços de fluxo de trabalho de hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Recursos de hospedagem do Windows Server app Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
