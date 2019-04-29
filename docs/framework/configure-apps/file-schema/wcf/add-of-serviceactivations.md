---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 2a3ba6d41059a480fe610254c0407df16d149e3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701457"
---
# <a name="add-of-serviceactivations"></a>\<Adicionar > de \<serviceActivations >

Um elemento de configuração que permite que você defina configurações de ativação de serviços virtuais que são mapeados para seus tipos de serviço do Windows Communication Foundation (WCF). Isso torna possível para ativar serviços hospedados no WAS / IIS sem um arquivo. svc.

\<system.ServiceModel>\
\<serviceHostingEnvironment>

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

|Atributo|Descrição|
|---------------|-----------------|
|fábrica|Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação do serviço.|
|serviço|O ServiceType que implementa o serviço (o Typename qualificado completo ou o Typename curto (quando ele é colocado na pasta App_Code).|
|relativeAddress|O endereço relativo dentro do aplicativo IIS atual – por exemplo "SVC". No WCF 4.0 Este endereço relativo deve conter uma das extensões de arquivo conhecidos (. svc. xamlx,...). Nenhum arquivo físico deve existir para a relativeUrl|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Uma seção de configuração que descreve as configurações de ativação.|

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

Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo. Você precisa colocar o `web.config` que contém a configuração sob a raiz do aplicativo virtual. Além disso, `serviceHostingEnvironment` é uma seção de herdável machineToApplication. Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.

Ativação baseada em configuração oferece suporte à ativação pelo protocolo http e não http. Ele requer que as extensões no relativeAddress, ou seja,. svc,. xoml ou. xamlx. Você pode mapear suas próprias extensões para o buildProviders saber, que, em seguida, permitirá que você ativar o serviço ao longo de qualquer extensão. Após o conflito, o `<serviceActivations>` seção substitui os registros. svc.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
