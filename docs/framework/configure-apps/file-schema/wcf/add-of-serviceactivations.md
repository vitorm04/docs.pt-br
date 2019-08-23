---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920021"
---
# <a name="add-of-serviceactivations"></a>\<Adicionar > de \<perativações >

Um elemento de configuração que permite definir configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF). Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.

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
|padrões|Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação de serviço.|
|serviço|O ServiceType que implementa o serviço (o TypeName totalmente qualificado ou o TypeName curto (quando ele é colocado na pasta App_Code).|
|relativeAddress|O endereço relativo no aplicativo IIS atual-por exemplo, "Service. svc". No WCF 4,0, esse endereço relativo deve conter uma das extensões de arquivo conhecidas (. svc,. xamlx,...). Nenhum arquivo físico deve existir para o relativeUrl|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Uma seção de configuração que descreve as configurações de ativação.|

## <a name="remarks"></a>Comentários

O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.

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

Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.

Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo. Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual. Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication. Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.

A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http. Ele requer extensões no relativeAddress, ou seja,. svc,. xoml ou. xamlx. Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão. Após o conflito, `<serviceActivations>` a seção substitui os registros. svc.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
