---
title: "Ativação com base em configuração no ISS e WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 116d7ec11f141e813aa960b28289031e0cfa8999
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Ativação com base em configuração no ISS e WAS
Normalmente, ao hospedar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço em serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS), você deve fornecer um arquivo. svc. O arquivo. svc contém o nome do serviço e uma fábrica de host de serviço personalizada opcional. Esse arquivo adicional aumenta a sobrecarga de gerenciamento. O recurso de ativação com base em configuração remove a necessidade de ter um arquivo. svc e, portanto, os respectivos sobrecarga.  
  
## <a name="configuration-based-activation"></a>Ativação com base em configuração  
 Ativação baseada em configuração usa os metadados que costumava ser colocado no arquivo. svc e o coloca no arquivo Web. config. Dentro de <`serviceHostingEnvironment`> elemento há um <`serviceActivations`> elemento. Dentro de <`serviceActivations`> elemento são um ou mais <`add`> elementos, um para cada serviço hospedado. O <`add`> elemento contém atributos que permitem que você defina o endereço relativo para o serviço e o tipo de serviço ou uma fábrica de host de serviço. O código de exemplo de configuração a seguir mostra como esta seção é usada.  
  
> [!NOTE]
>  Cada <`add`> elemento deve especificar um serviço ou um atributo de fábrica. Especificando atributos de fábrica e o serviço é permitido.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Com isso no arquivo Web. config, você pode colocar o código de serviço de origem no diretório App_Code do aplicativo ou um assembly compilado no diretório Bin do aplicativo.  
  
> [!NOTE]
>  -   Ao usar a ativação baseada em configuração, não há suporte para código embutido em arquivos. svc.  
> -   O `relativeAddress` atributo deve ser definido como um endereço relativo, como "\<subdiretório > / SVC" ou "~ /\<sub-directory/SVC".  
> -   Uma exceção de configuração é gerada se você registrar um endereço relativo que não tem uma extensão conhecida associada com o WCF.  
> -   O endereço relativo especificado é relativo à raiz do aplicativo virtual.  
> -   Devido ao modelo hierárquico da configuração, os endereços relativos registrados no nível de máquina e de site são herdados por aplicativos virtuais.  
> -   Os registros de um arquivo de configuração têm precedência sobre as configurações em um SVC, .xamlx,. xoml ou outro arquivo.  
> -   Qualquer ' \' (barras invertidas) em um URI enviado ao IIS / WAS são automaticamente convertidos para um '/' (barra). Se um endereço relativo é adicionado, que contém um ' \' e enviar um URI que usa o endereço relativo do IIS, a barra invertida é convertida em uma barra invertida e o IIS não pode corresponder ao endereço relativo. IIS envia informações de rastreamento que indica que não há nenhuma correspondência encontrada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Hosting Services](../../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)  
 [Visão geral dos serviços de fluxo de trabalho hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
