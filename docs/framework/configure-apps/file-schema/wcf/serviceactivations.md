---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936443"
---
# <a name="serviceactivations"></a>\<serviceActivations>

Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF). Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.

\<system.ServiceModel>\
\<serviceHostingEnvironment>\
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
|[\<add>](add-of-serviceactivations.md)|Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.|

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

A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http. Ele requer extensões em relativeAddress, ou seja,. svc,. xoml ou. xamlx. Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão. Após o conflito, `<serviceActivations>` a seção substitui os registros. svc.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
