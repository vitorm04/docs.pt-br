---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 0b06d61a33cd6a704a5ab0f75d29bde3f72d77fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115850"
---
# <a name="servicemetadata"></a>\<serviceMetadata>
Especifica a publicação de metadados de serviço e informações associadas.  
  
\<system.serviceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<serviceMetadata>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|externalMetadataLocation|Um Uri que contém o local de um arquivo WSDL, que é retornado para o usuário em resposta a solicitações WSDL e MEX em vez do WSDL gerado automaticamente. Quando esse atributo não for definido, o padrão WSDL é retornado. O padrão é uma cadeia de caracteres vazia.|  
|httpGetBinding|Uma cadeia de caracteres que especifica o tipo de associação que será usado para recuperação de metadados via HTTP GET. Essa configuração é opcional. Se não for especificado, as associações padrão serão usadas.<br /><br /> Somente associações com elementos de associação interna que dão suporte a <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte. Além disso, o <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Uma cadeia de caracteres que define o nome da associação que é especificado no `httpGetBinding` atributo, o que faz referência às informações de configuração adicionais desta associação. O mesmo nome deve ser definido no `<bindings>` seção.|  
|httpGetEnabled|Um valor booliano que especifica se a publicação de metadados de serviço para recuperação usando uma solicitação HTTP/Get. O padrão é `false`.<br /><br /> Se o atributo httpGetUrl não for especificado, o endereço no qual os metadados são publicados é o endereço de serviço além de um "? wsdl". Por exemplo, se o endereço do serviço for "http://localhost:8080/CalculatorService", o endereço de metadados HTTP/Get é"http://localhost:8080/CalculatorService?wsdl".<br /><br /> Se essa propriedade for `false`, ou o endereço do serviço não é baseado em HTTP ou HTTPS, "? wsdl" será ignorado.|  
|httpGetUrl|Um Uri que especifica o endereço no qual os metadados são publicados para recuperação usando uma solicitação HTTP/Get. Se um Uri relativo for especificado será tratado como relativo ao endereço base do serviço.|  
|httpsGetBinding|Uma cadeia de caracteres que especifica o tipo de associação que será usado para recuperação de metadados via HTTPS GET. Essa configuração é opcional. Se não for especificado, as associações padrão serão usadas.<br /><br /> Somente associações com elementos de associação interna que dão suporte a <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte. Além disso, o <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Uma cadeia de caracteres que define o nome da associação que é especificado no `httpsGetBinding` atributo, o que faz referência às informações de configuração adicionais desta associação. O mesmo nome deve ser definido no `<bindings>` seção.|  
|httpsGetEnabled|Um valor booliano que especifica se a publicação de metadados de serviço para recuperação usando uma solicitação HTTPS/Get. O padrão é `false`.<br /><br /> Se o atributo httpsGetUrl não for especificado, o endereço no qual os metadados são publicados é o endereço de serviço além de um "? wsdl". Por exemplo, se o endereço do serviço for "https://localhost:8080/CalculatorService", o endereço de metadados HTTP/Get é"https://localhost:8080/CalculatorService?wsdl".<br /><br /> Se essa propriedade for `false`, ou o endereço do serviço não é baseado em HTTP ou HTTPS, "? wsdl" será ignorado.|  
|httpsGetUrl|Um Uri que especifica o endereço no qual os metadados são publicados para recuperação usando uma solicitação HTTPS/Get.|  
|policyVersion|Uma cadeia de caracteres que especifica a versão da especificação WS-Policy sendo usada. Esse atributo é do tipo <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração permite que você controle os recursos de publicação de metadados de um serviço. Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para serviços Windows Communication Foundation (WCF) desabilita a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importar ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração. Usando este elemento de configuração, você pode habilitar esse comportamento de publicação para seu serviço.  
  
 Para obter um exemplo detalhado de configurar esse comportamento, consulte [comportamento de publicação de metadados](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 Opcional `httpGetBinding` e `httpsGetBinding` atributos permitem que você configure as associações usadas para recuperação de metadados via HTTP GET (ou HTTPS GET). Se não forem especificadas, as associações padrão (`HttpTransportBindingElement`, no caso de HTTP e `HttpsTransportBindingElement`, no caso HTTPS) são usados para recuperação de metadados, conforme apropriado. Observe que você não pode usar esses atributos com associações do WCF internas. Somente associações com elementos de associação interna que dão suporte a <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte. Além disso, o <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Para reduzir a exposição de um serviço a usuários mal-intencionados, é possível a transferência segura usando o SSL ao longo do mecanismo de HTTP (HTTPS). Para fazer isso, primeiro você deve associar um certificado x. 509 adequado a uma porta específica no computador que hospeda o serviço. (Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Em segundo lugar, adicione esse elemento para a configuração do serviço e defina as `httpsGetEnabled` atributo `true`. Por fim, defina o `httpsGetUrl` de atributo para a URL do ponto de extremidade de metadados de serviço, conforme mostrado no exemplo a seguir.  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configurar um serviço para expor metadados usando o \<serviceMetadata > elemento. Ele também configura um ponto de extremidade para expor o `IMetadataExchange` contrato como uma implementação de um protocolo WS-MetadataExchange (MEX). O exemplo usa o `mexHttpBinding`, que é uma conveniência padrão de associação que é equivalente de `wsHttpBinding` com o modo de segurança definido como `None`. Um endereço relativo "mex" é usado no ponto de extremidade, que, quando resolvido nos serviços de base endereço resulta em um endereço de ponto de extremidade de `http://localhost/servicemodelsamples/service.svc/mex`.  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Comportamento de publicação de metadados](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
