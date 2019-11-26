---
title: Configuração do cliente
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 6a5cbf5d536af8649b0b8bb93600e94a48c507c1
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141775"
---
# <a name="client-configuration"></a>Configuração do cliente
Você pode usar a configuração de cliente do Windows Communication Foundation (WCF) para especificar o endereço, a associação, o comportamento e o contrato, as propriedades "ABC" do ponto de extremidade do cliente, que os clientes usam para se conectar a pontos de extremidade de serviço. O elemento de [> do cliente\<](../../configure-apps/file-schema/wcf/client.md) tem um elemento [> ponto de extremidade\<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) cujos atributos são usados para configurar o ponto de extremidade ABCs. Esses atributos são discutidos na seção [Configurando pontos de extremidade](#configuring-endpoints) .  
  
 O elemento [> do ponto de extremidade\<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) também contém um elemento [\<metadados >](../../configure-apps/file-schema/wcf/metadata.md) que é usado para especificar as configurações para importar e exportar metadados, um [\<cabeçalhos >](../../configure-apps/file-schema/wcf/headers.md) elemento que contém uma coleção de cabeçalhos de endereço personalizados e um elemento\<de [identidade](../../configure-apps/file-schema/wcf/identity.md) > que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele. Os [cabeçalhos de\<](../../configure-apps/file-schema/wcf/headers.md) e\<elementos de [> de identidade](../../configure-apps/file-schema/wcf/identity.md) são parte do <xref:System.ServiceModel.EndpointAddress> e são discutidos no artigo de [endereços](../../wcf/feature-details/endpoint-addresses.md) . Links para tópicos que explicam o uso de extensões de metadados são fornecidos na seção [Configurando metadados](#configuring-metadata) .  
  
## <a name="configuring-endpoints"></a>Configurando pontos de extremidade  
 A configuração do cliente foi criada para permitir que o cliente especifique um ou mais pontos de extremidade, cada um com seu próprio nome, endereço e contrato, com cada um referenciando as [associações de\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) e [\<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementos na configuração do cliente a serem usados para configurar esse ponto de extremidade. O arquivo de configuração do cliente deve ser nomeado "app. config" porque esse é o nome esperado pelo tempo de execução do WCF. O exemplo a seguir mostra um arquivo de configuração de cliente.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 O atributo opcional `name` identifica exclusivamente um ponto de extremidade para um determinado contrato. Ele é usado pelo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou pelo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> para especificar qual ponto de extremidade na configuração do cliente está sendo direcionado e deve ser carregado quando um canal é criado para o serviço. Um nome de configuração de ponto de extremidade curinga "\*" está disponível e indica ao método <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> que ele deve carregar qualquer configuração de ponto de extremidade no arquivo, desde que haja exatamente um disponível e, de outra forma, gere uma exceção. Se esse atributo for omitido, o ponto de extremidade correspondente será usado como o ponto de extremidade padrão associado ao tipo de contrato especificado. O valor padrão para o atributo `name` é uma cadeia de caracteres vazia que é igual a qualquer outro nome.  
  
 Cada ponto de extremidade deve ter um endereço associado a ele para localizar e identificar o ponto de extremidade. O atributo `address` pode ser usado para especificar a URL que fornece o local do ponto de extremidade. Mas o endereço de um ponto de extremidade de serviço também pode ser especificado no código criando um Uniform Resource Identifier (URI) e é adicionado ao <xref:System.ServiceModel.ServiceHost> usando um dos métodos <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>. Para obter mais informações, consulte [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Como a introdução indica, os [cabeçalhos de\<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [\<elementos > de identidade](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) são parte do <xref:System.ServiceModel.EndpointAddress> e também são discutidos no tópico [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) .  
  
 O atributo `binding` indica o tipo de associação que o ponto de extremidade espera usar ao se conectar a um serviço. O tipo deve ter uma seção de configuração registrada se for para ser referenciado. No exemplo anterior, esta é a seção [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , que indica que o ponto de extremidade usa uma <xref:System.ServiceModel.WSHttpBinding>. Mas pode haver mais de uma associação de um determinado tipo que o ponto de extremidade pode usar. Cada um deles tem sua própria [associação\<elemento >](../../configure-apps/file-schema/wcf/bindings.md) dentro do elemento do tipo (Associação). O atributo `bindingconfiguration` é usado para distinguir entre associações do mesmo tipo. Seu valor é correspondido com o atributo `name` do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) . Para obter mais informações sobre como configurar uma associação de cliente usando a configuração [do, consulte como especificar uma associação de cliente na configuração](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 O atributo `behaviorConfiguration` é usado para especificar qual [\<de comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do [\<EndpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) o ponto de extremidade deve usar. Seu valor é correspondido com o atributo `name` do elemento [> do comportamento de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) . Para obter um exemplo de como usar a configuração para especificar os comportamentos do cliente, consulte [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 O atributo `contract` especifica qual contrato o ponto de extremidade está expondo. Esse valor é mapeado para a <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> do <xref:System.ServiceModel.ServiceContractAttribute>. O valor padrão é o nome completo do tipo da classe que implementa o serviço.  
  
### <a name="configuring-metadata"></a>Configurando metadados  
 O elemento [\<metadata >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) é usado para especificar as configurações usadas para registrar as extensões de importação de metadados. Para obter mais informações sobre como estender o sistema de metadados, consulte [estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Consulte também

- [Pontos de extremidade: endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md)
