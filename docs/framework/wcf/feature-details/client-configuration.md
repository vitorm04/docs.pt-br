---
title: Configuração do cliente
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: b9975c6caeedc94bf4a7773e71a95eb0d8c7aed2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144684"
---
# <a name="client-configuration"></a>Configuração do cliente
Você pode usar a configuração de cliente do Windows Communication Foundation (WCF) para especificar o endereço, associação, comportamento e contrato, as propriedades de "ABC" do ponto de extremidade de cliente, quais clientes usam para se conectar aos pontos de extremidade de serviço. O [ \<cliente >](../../configure-apps/file-schema/wcf/client.md) elemento tem um [ \<ponto de extremidade >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) cujos atributos são usados para configurar o ponto de extremidade ABCs do elemento. Esses atributos são discutidos os [Configurando pontos de extremidade](#configuring-endpoints) seção.  
  
 O [ \<ponto de extremidade >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) também contém um elemento de uma [ \<metadados >](../../configure-apps/file-schema/wcf/metadata.md) elemento que é usado para especificar configurações de importação e exportação de metadados, um [ \<cabeçalhos >](../../configure-apps/file-schema/wcf/headers.md) elemento que contém uma coleção de cabeçalhos de endereço personalizado, e um [ \<identidade >](../../configure-apps/file-schema/wcf/identity.md) elemento que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele. O [ \<cabeçalhos >](../../configure-apps/file-schema/wcf/headers.md) e [ \<identidade >](../../configure-apps/file-schema/wcf/identity.md) elementos fazem parte do <xref:System.ServiceModel.EndpointAddress> e são discutidos no [endereços](../../wcf/feature-details/endpoint-addresses.md) artigo. São fornecidos links para tópicos que explicam o uso de extensões de metadados na [metadados configurando](#configuring-metadata) seção.  
  
## <a name="configuring-endpoints"></a>Configurando pontos de extremidade  
 A configuração do cliente foi projetada para permitir que o cliente especificar um ou mais pontos de extremidade, cada um com seu próprio nome, endereço e de contrato, com cada referência a [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) e [ \< comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementos na configuração do cliente a ser usado para configurar o ponto de extremidade. O arquivo de configuração do cliente deve ser nomeado "App. config" porque esse é o nome que espera que o tempo de execução do WCF. O exemplo a seguir mostra o arquivo de configuração de um cliente.  
  
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
  
 Opcional `name` atributo identifica exclusivamente um ponto de extremidade para um determinado contrato. Ele é usado pelo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou o <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> para especificar qual ponto de extremidade na configuração do cliente está sendo direcionado e deve ser carregado quando um canal é criado para o serviço. Um nome de configuração de ponto de extremidade de curinga "\*" está disponível e indica para o <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> método que deve carregar qualquer configuração de ponto de extremidade no arquivo, desde que haja exatamente um disponível e caso contrário, gerará uma exceção. Se esse atributo for omitido, o ponto de extremidade correspondente é usado como o ponto de extremidade padrão associado ao tipo de contrato especificado. O valor padrão para o `name` atributo é uma cadeia de caracteres vazia, o que é correspondida como qualquer outro nome.  
  
 Cada ponto de extremidade deve ter um endereço associado a ele para localizar e identificar o ponto de extremidade. O `address` atributo pode ser usado para especificar a URL que fornece a localização do ponto de extremidade. Mas o endereço de um ponto de extremidade de serviço também pode ser especificado no código, criando um identificador de recurso uniforme (URI) e é adicionado para o <xref:System.ServiceModel.ServiceHost> usando um do <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos. Para obter mais informações, consulte [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Como indica a introdução, o [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementos fazem parte do <xref:System.ServiceModel.EndpointAddress> e também são discutidas no [ Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tópico.  
  
 O `binding` atributo indica o tipo de ponto de extremidade de associação espera usar ao se conectar a um serviço. O tipo deve ter uma seção de configuração registrado se ela deve ser referenciado. No exemplo anterior, isso é o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) seção, que indica que o ponto de extremidade usa um <xref:System.ServiceModel.WSHttpBinding>. Mas pode haver mais de uma associação de um determinado tipo em que o ponto de extremidade pode usar. Cada um deles tem sua própria [ \<associação >](../../../../docs/framework/misc/binding.md) elemento dentro do elemento type (binding). O `bindingconfiguration` atributo é usado para distinguir as associações do mesmo tipo. Seu valor é correspondido com o `name` atributo o [ \<associação >](../../../../docs/framework/misc/binding.md) elemento. Para obter mais informações sobre como configurar um cliente de associação usando a configuração, consulte [como: Especificar uma associação de cliente na configuração](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 O `behaviorConfiguration` atributo é usado para especificar quais [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) dos [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) o ponto de extremidade deve usar. Seu valor é correspondido com o `name` atributo o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento. Para obter um exemplo de como usar a configuração para especificar comportamentos do cliente, consulte [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 O `contract` atributo especifica qual contrato que o ponto de extremidade está expondo. Esse valor é mapeado para o <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> do <xref:System.ServiceModel.ServiceContractAttribute>. O valor padrão é o nome de tipo completo da classe que implementa o serviço.  
  
### <a name="configuring-metadata"></a>Configuração de metadados  
 O [ \<metadados >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) elemento é usado para especificar as configurações usadas para registrar metadados importar extensões. Para obter mais informações sobre como estender o sistema de metadados, consulte [estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Consulte também

- [Pontos de extremidade: endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md)
