---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 5da05c7b6a9685b9e34b3181ce8e0bd31ccd052b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704950"
---
# <a name="ltserviceactivationsgt"></a>&lt;serviceActivations&gt;
Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviço virtual que são mapeados para seus tipos de serviço do Windows Communication Foundation (WCF). Isso torna possível para ativar serviços hospedados no WAS / IIS sem um arquivo. svc.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment>  
\<serviceActivations>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.|  
  
## <a name="remarks"></a>Comentários  
 O exemplo a seguir mostra como definir as configurações de ativação dentro de seu arquivo Web. config.  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 Usando esta configuração, você pode ativar o GreetingService sem usar um arquivo. svc.  
  
 Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo. Você precisa colocar o `web.config` que contém a configuração sob a raiz do aplicativo virtual. Além disso, `serviceHostingEnvironment` é uma seção de herdável machinetoApplication. Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.  
  
 Ativação baseada em configuração oferece suporte à ativação pelo protocolo http e não http. Ele requer que as extensões no relatativeAddress, ou seja,. svc,. xoml ou. xamlx. Você pode mapear suas próprias extensões para o buildProviders saber, que, em seguida, permitirá que você ativar o serviço ao longo de qualquer extensão. Após o conflito, o `<serviceActivations>` seção substitui os registros. svc.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
