---
title: Configuração do cliente
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: ff82f56639ec451c04624d22fff0bcb03f46d946
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185370"
---
# <a name="client-configuration"></a>Configuração do cliente
Você pode usar a configuração do cliente da Windows Communication Foundation (WCF) para especificar o endereço, vinculação, comportamento e contrato, as propriedades "ABC" do ponto final do cliente, que os clientes usam para se conectar aos pontos finais do serviço. O [ \<](../../configure-apps/file-schema/wcf/client.md) elemento>[ \<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) cliente tem um elemento de>ponto final cujos atributos são usados para configurar os ABCs de ponto final. Esses atributos são discutidos na [seção Configurando pontos finais.](#configuring-endpoints)  
  
 O [ \<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elemento>ponto final também contém um [ \<](../../configure-apps/file-schema/wcf/metadata.md) elemento de>de metadados que é usado para especificar configurações para importar [ \<](../../configure-apps/file-schema/wcf/identity.md) e exportar metadados, um [ \<elemento de>de cabeçalhos](../../configure-apps/file-schema/wcf/headers.md) que contém uma coleção de cabeçalhos de endereço personalizados e um elemento de>de identidade que permite a autenticação de um ponto final por outros pontos finais trocando mensagens com ele. Os [ \<cabeçalhos>](../../configure-apps/file-schema/wcf/headers.md) e [ \<](../../configure-apps/file-schema/wcf/identity.md) os <xref:System.ServiceModel.EndpointAddress> elementos de>de identidade fazem parte do e são discutidos no artigo [Endereços.](../../wcf/feature-details/endpoint-addresses.md) Links para tópicos que explicam o uso de extensões de metadados são fornecidos na seção [Configurando metadados.](#configuring-metadata)  
  
## <a name="configuring-endpoints"></a>Configuração de pontos finais  
 A configuração do cliente foi projetada para permitir que o cliente especifique um ou mais pontos finais, cada um com seu próprio nome, endereço e contrato, com cada referência às [ \<vinculações>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) e [ \<comportamentos>elementos](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) na configuração do cliente a serem usados para configurar esse ponto final. O arquivo de configuração do cliente deve ser chamado de "App.config" porque este é o nome que o tempo de execução do WCF espera. O exemplo a seguir mostra um arquivo de configuração do cliente.  
  
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
  
 O `name` atributo opcional identifica exclusivamente um ponto final para um determinado contrato. Ele é usado <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> pelo <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> ou pelo para especificar qual ponto final na configuração do cliente está sendo direcionado e deve ser carregado quando um canal é criado para serviço. Um nome de configuração\*de ponto final <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> curinga " está disponível e indica para o método que ele deve carregar qualquer configuração de ponto final no arquivo, desde que haja precisamente um disponível, e de outra forma lança uma exceção. Se esse atributo for omitido, o ponto final correspondente será usado como o ponto final padrão associado ao tipo de contrato especificado. O valor padrão `name` do atributo é uma seqüência de string vazia que é combinada como qualquer outro nome.  
  
 Cada ponto final deve ter um endereço associado a ele para localizar e identificar o ponto final. O `address` atributo pode ser usado para especificar a URL que fornece a localização do ponto final. Mas o endereço para um ponto final de serviço também pode ser especificado em código <xref:System.ServiceModel.ServiceHost> criando um <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> URI (Uniform Resource Identifier, identificador de recursos uniformes) e é adicionado ao uso de um dos métodos. Para obter mais informações, consulte [Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Como a introdução indica, <xref:System.ServiceModel.EndpointAddress> os [ \<cabeçalhos>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [ \<elementos de>de identidade](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) fazem parte do e também são discutidos no tópico [Endereços.](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
  
 O `binding` atributo indica o tipo de vinculação que o ponto final espera usar ao se conectar a um serviço. O tipo deve ter uma seção de configuração registrada se for referenciada. No exemplo anterior, esta é a <xref:System.ServiceModel.WSHttpBinding> [ \<seção wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) que indica que o ponto final usa um . Mas pode haver mais de uma vinculação de um determinado tipo que o ponto final pode usar. Cada um deles [ \<](../../configure-apps/file-schema/wcf/bindings.md) tem seu próprio elemento de>de ligação dentro do elemento do tipo (vinculação). O `bindingconfiguration` atributo é usado para distinguir entre ligações do mesmo tipo. Seu valor é compatível `name` com o atributo do [ \<](../../configure-apps/file-schema/wcf/bindings.md) elemento de ligação>. Para obter mais informações sobre como configurar uma vinculação do cliente usando a configuração, consulte [Como: Especificar uma vinculação do cliente na configuração](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 O `behaviorConfiguration` atributo é [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) usado para especificar qual comportamento>do [ \<ponto finalComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) o ponto final deve ser usado. Seu valor é compatível `name` com o atributo do [ \<comportamento>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento. Para um exemplo de uso da configuração para especificar comportamentos do cliente, consulte [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 O `contract` atributo especifica qual contrato o ponto final está expondo. Este valor mapeia para o <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute>do . O valor padrão é o nome de tipo completo da classe que implementa o serviço.  
  
### <a name="configuring-metadata"></a>Configuração de metadados  
 O elemento [ \<>de metadados](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) é usado para especificar configurações usadas para registrar extensões de importação de metadados. Para obter mais informações sobre como estender o sistema de metadados, consulte [Estendendo o Sistema de Metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Confira também

- [Pontos de extremidade: endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md)
