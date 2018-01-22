---
title: "Configuração do cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75b594d01c8a9297f3383c2648b3853c2c024b9b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="client-configuration"></a>Configuração do cliente
Você pode usar o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuração do cliente para especificar o endereço, associação de comportamento e de contrato, as propriedades de "ABC" do ponto de extremidade de cliente, que os clientes usam para se conectar aos pontos de extremidade de serviço. O [ \<cliente >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) elemento tem um [ \<ponto de extremidade >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento cujos atributos são usados para configurar o ponto de extremidade ABC. Esses atributos são discutidos na seção "Configurando pontos de extremidade" deste tópico.  
  
 O [ \<ponto de extremidade >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) também contém um [ \<metadados >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) elemento que é usado para especificar configurações de importação e exportação de metadados, um [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento que contém uma coleção de cabeçalhos de endereço personalizado, e um [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento que permite a autenticação de um ponto de extremidade por outros pontos de extremidade troca de mensagens com ele. O [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementos fazem parte do <xref:System.ServiceModel.EndpointAddress> e são discutidas no [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tópico. Links para tópicos que explicam o uso de extensões de metadados são fornecidos na seção Configuração de metadados sub deste tópico.  
  
## <a name="configuring-endpoints"></a>Configurando pontos de extremidade  
 A configuração do cliente é projetada para permitir que o cliente especificar um ou mais pontos de extremidade, cada um com seu próprio nome, endereço e contrato, com cada referência a [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) e [ \< comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementos na configuração do cliente a ser usado para configurar o ponto de extremidade. O arquivo de configuração do cliente deve ser nomeado "App. config" porque esse é o nome que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] espera de tempo de execução. O exemplo a seguir mostra o arquivo de configuração de um cliente.  
  
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
  
 Opcional `name` atributo identifica exclusivamente um ponto de extremidade para um dado contrato. Ele é usado pelo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou o <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> para especificar qual ponto de extremidade na configuração do cliente está sendo direcionado e deve ser carregado quando um canal é criado para o serviço. Um nome de configuração de ponto de extremidade de curinga "*" está disponível e indica para o <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> método que ele deve carregar qualquer configuração de ponto de extremidade no arquivo, desde que haja precisamente uma disponível e, caso contrário gerará uma exceção. Se esse atributo for omitido, o ponto de extremidade correspondente é usado como o ponto de extremidade padrão associado ao tipo de contrato especificado. O valor padrão para o `name` atributo é uma cadeia de caracteres vazia, o que é comparada como qualquer outro nome.  
  
 Cada ponto de extremidade deve ter um endereço associado a ele para localizar e identificar o ponto de extremidade. O `address` atributo pode ser usado para especificar a URL que fornece o local do ponto de extremidade. Mas o endereço de um ponto de extremidade de serviço também pode ser especificado no código, criando um identificador de recurso uniforme (URI) e é adicionado para o <xref:System.ServiceModel.ServiceHost> usando um do <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Como introdução indica, o [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementos fazem parte do <xref:System.ServiceModel.EndpointAddress> e também são discutidas no [ Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tópico.  
  
 O `binding` atributo indica o tipo de ponto de extremidade de associação espera usar ao se conectar a um serviço. O tipo deve ter uma seção de configuração registrados se é para ser referenciado. No exemplo anterior, este é o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) seção, o que indica que o ponto de extremidade usa um <xref:System.ServiceModel.WSHttpBinding>. Mas, pode haver mais de uma associação de um determinado tipo pode usar o ponto de extremidade. Cada um deles tem seu próprio [ \<associação >](../../../../docs/framework/misc/binding.md) elemento dentro do elemento type (binding). O `bindingconfiguration` atributo é usado para distinguir entre as ligações do mesmo tipo. Seu valor é correspondido com o `name` atributo o [ \<associação >](../../../../docs/framework/misc/binding.md) elemento. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar um cliente de associação usando a configuração, consulte [como: especificar uma associação de cliente em configuração](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 O `behaviorConfiguration` atributo é usado para especificar quais [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) deve usar o ponto de extremidade. Seu valor é correspondido com o `name` atributo o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento. Para obter um exemplo do uso da configuração para especificar o comportamento do cliente, consulte [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 O `contract` atributo especifica qual contrato que o ponto de extremidade está expondo. Esse valor é mapeado para o <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> do <xref:System.ServiceModel.ServiceContractAttribute>. O valor padrão é o nome de tipo completo da classe que implementa o serviço.  
  
### <a name="configuring-metadata"></a>Configuração de metadados  
 O [ \<metadados >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) elemento é usado para especificar configurações usadas para registrar metadados importar extensões. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Estendendo o sistema de metadados, consulte[estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Consulte também  
 [Pontos de extremidade: endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md)
