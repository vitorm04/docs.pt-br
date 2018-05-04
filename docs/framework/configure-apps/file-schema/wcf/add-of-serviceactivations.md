---
title: '&lt;adicionar&gt; &lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 1a25ad517e26e037c588bb14844e38147e251d96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;adicionar&gt; &lt;serviceActivations&gt;
Um elemento de configuração que permite que você defina configurações de ativação de serviços virtuais que são mapeados para seus tipos de serviço do Windows Communication Foundation (WCF). Isso torna possível para ativar serviços hospedados no WAS / IIS sem um arquivo. svc.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|fábrica|Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação do serviço.|  
|serviço|O ServiceType que implementa o serviço (o Typename qualificado completo ou o Typename curto (quando ele é colocado na pasta App_Code).|  
|relativeAddress|O endereço relativo dentro do aplicativo IIS atual - por exemplo "SVC". No WCF 4.0 Este endereço relativo deve conter uma das extensões de arquivo conhecidos (. svc .xamlx,...). Nenhum arquivo físico deve existir para o relativeUrl|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Uma seção de configuração que descreve as configurações de ativação.|  
  
## <a name="remarks"></a>Comentários  
 O exemplo a seguir mostra como definir as configurações de ativação em seu arquivo Web. config.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 Usando esta configuração, você pode ativar o GreetingService sem usar um arquivo. svc.  
  
 Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo. Você precisa colocar a `web.config` que contém a configuração abaixo da raiz do aplicativo virtual. Além disso, `serviceHostingEnvironment` uma seção herdáveis machinetoApplication. Se você registrar um único serviço na raiz da máquina, cada serviço no aplicativo herdará esse serviço.  
  
 Ativação baseada em configuração oferece suporte à ativação pelo protocolo http e não http. Ele requer extensões no relatativeAddress, ou seja,. svc,. xoml ou .xamlx. Você pode mapear suas próprias extensões para o buildProviders sabe, que, em seguida, permite que você ative o serviço em qualquer extensão. Em conflito, a `<serviceActivations>` seção substitui registros. svc.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
