---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773940"
---
# <a name="client"></a>\<client >
O elemento `client` define uma lista de pontos de extremidade aos quais um cliente pode se conectar.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp; &nbsp; &nbsp; &nbsp; **\<client** >

## <a name="syntax"></a>Sintaxe

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 Nenhum

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[\<endpoint >](endpoint-of-client.md)|Contém uma coleção de elementos EndPoint que especificam os pontos de extremidade aos quais este cliente pode se conectar.|
|[\<metadata >](metadata.md)|Contém configurações para processar metadados.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).|

## <a name="remarks"></a>Comentários
 A seção `client` define uma lista de pontos de extremidade aos quais um cliente pode se conectar. Cada ponto de extremidade listado na seção cliente define sua própria associação, comportamento e contrato. Ele é identificado exclusivamente pela combinação dos atributos `name` e `contract`. O código do cliente especifica o `name` para se conectar a um ponto de extremidade para o serviço que o cliente implementa. Se o atributo `name` for omitido, o ponto de extremidade atuará como o ponto de extremidade padrão para o contrato que ele implementa.

 Além disso, esta seção também especifica configurações para processar metadados.

## <a name="example"></a>Exemplo

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [Configuração de cliente do WCF](../../../wcf/feature-details/client-configuration.md)
- [Clientes](../../../wcf/feature-details/clients.md)
