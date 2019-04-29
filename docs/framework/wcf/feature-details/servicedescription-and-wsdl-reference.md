---
title: ServiceDescription and WSDL Reference
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 6690bea3d3df0f39a5581c3a6c14723c0f30f40c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748157"
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription and WSDL Reference
Este tópico descreve como o Windows Communication Foundation (WCF) mapeia documentos de descrição linguagem WSDL (Web Services) para e de <xref:System.ServiceModel.Description.ServiceDescription> instâncias.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>Como o ServiceDescription é mapeada para o WSDL 1.1  
 Você pode usar o WCF para exportar documentos WSDL de um <xref:System.ServiceModel.Description.ServiceDescription> instância para o seu serviço. Documentos WSDL são gerados automaticamente para seu serviço quando você publica pontos de extremidade de metadados.  
  
 Você também pode importar <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias, <xref:System.ServiceModel.Description.ContractDescription> instâncias, e <xref:System.ServiceModel.Channels.Binding> instâncias de documentos WSDL usando o `WsdlImporter` tipo.  
  
 Os documentos WSDL, exportados pelo WCF, importar quaisquer definições de esquema XML usadas de documentos de esquema XML externos. Um documento separado do esquema XML é exportado para cada namespace de destino, que os tipos de dados usam no serviço. Da mesma forma, um documento WSDL separado é exportado para cada namespace de destino o serviço de uso de contratos.  
  
### <a name="servicedescription"></a>ServiceDescription  
 Um <xref:System.ServiceModel.Description.ServiceDescription> instância é mapeado para um `wsdl:service` elemento. Um <xref:System.ServiceModel.Description.ServiceDescription> instância contém uma coleção de <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias que cada mapa individuais para `wsdl:port` elementos.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|O `wsdl:service` /@name valor para o serviço.|  
|`Namespace`|O targetNamespace para o `wsdl:service` definição para o serviço.|  
|`Endpoints`|O `wsdl:port` definições para o serviço.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 Um <xref:System.ServiceModel.Description.ServiceEndpoint> instância é mapeado para um `wsdl:port` elemento. Um <xref:System.ServiceModel.Description.ServiceEndpoint> instância contém um endereço, uma ligação e um contrato.  
  
 Comportamentos de ponto de extremidade que implementam o <xref:System.ServiceModel.Description.IWsdlExportExtension> interface pode modificar o `wsdl:port` elemento para o ponto de extremidade que eles estão conectados.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|O `wsdl:port` /@name valor para o ponto de extremidade e o `wsdl:binding` /@name valor para a associação de ponto de extremidade.|  
|`Address`|O endereço para o `wsdl:port` definição para o ponto de extremidade.<br /><br /> O transporte para o ponto de extremidade determina o formato do endereço. Por exemplo, para transportes com suporte do WCF, ele poderia ser um endereço SOAP ou uma referência de ponto de extremidade.|  
|`Binding`|O `wsdl:binding` definição para o ponto de extremidade.<br /><br /> Ao contrário de `wsdl:binding` definições de associações do WCF não estão vinculadas a qualquer um contrato.|  
|`Contract`|O `wsdl:portType` definição para o ponto de extremidade.|  
|`Behaviors`|Comportamentos de ponto de extremidade que implementam o <xref:System.ServiceModel.Description.IWsdlExportExtension> interface pode modificar o `wsdl:port` para o ponto de extremidade.|  
  
### <a name="bindings"></a>Associações  
 A instância de ligação para um `ServiceEndpoint` instância é mapeado para um `wsdl:binding` definição. Diferentemente `wsdl:binding` definições, que devem ser associadas um determinado `wsdl:portType` definição, ligações do WCF são independentes de qualquer contrato.  
  
 Uma associação é composta por uma coleção de elementos de associação. Cada elemento descreve alguns aspectos de como o ponto de extremidade se comunica com clientes. Além disso, uma binding tem um <xref:System.ServiceModel.Channels.MessageVersion> que indica a <xref:System.ServiceModel.EnvelopeVersion> e <xref:System.ServiceModel.Channels.AddressingVersion> para o ponto de extremidade.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|Usado no nome do padrão de um ponto de extremidade, que é o nome da associação com o nome de contrato anexado separados por um caractere de sublinhado.|  
|`Namespace`|O `targetNamespace` para o `wsdl:binding` definição.<br /><br /> Na importação, se uma política é anexada à porta WSDL, o namespace da associação importado é mapeado para o `targetNamespace` para o `wsdl:port` definição.|  
|`BindingElementCollection`, conforme retornado pelo `CreateBindingElements`método)|Várias extensões específicas de domínio para o `wsdl:binding` definição, geralmente, as declarações de política.|  
|`MessageVersion`|O `EnvelopeVersion` e `AddressingVersion` para o ponto de extremidade.<br /><br /> Quando `MessageVersion.None` for especificado, a associação WSDL não contém uma associação SOAP e a porta WSDL não contêm conteúdo do WS-Addressing. Essa configuração é usada normalmente para pontos de extremidade de XML (POX) antigo simples.|  
  
#### <a name="bindingelements"></a>BindingElements  
 Os elementos de associação para uma associação de ponto de extremidade mapeados para várias extensões WSDL no `wsdl:binding`, como declarações de política.  
  
 O <xref:System.ServiceModel.Channels.TransportBindingElement> para a associação determina o identificador de recurso uniforme (URI) de transporte para uma associação SOAP.  
  
#### <a name="addressingversion"></a>AddressingVersion  
 O `AddressingVersion` em uma associação é mapeado para a versão de endereçamento usado no `wsd:port`. O WCF oferece suporte a SOAP 1.1 e SOAP 1.2 endereços e WS-Addressing 08/2004 e referências de ponto de extremidade do WS-Addressing 1.0.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 O `EnvelopeVersion` em uma associação é mapeado para a versão do SOAP é usado no `wsdl:binding`. O WCF oferece suporte a associações SOAP 1.1 e SOAP 1.2.  
  
### <a name="contracts"></a>Contratos  
 O <xref:System.ServiceModel.Description.ContractDescription> de instância para uma `ServiceEndpoint` instância é mapeado para um `wsdl:portType`. Um `ContractDescription` instância descreve todas as operações para um determinado contrato.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|O `wsdl:portType` /@name valor para o contrato.|  
|`Namespace`|O targetNamespace para o `wsdl:portType` definição.|  
|`SessionMode`|O `wsdl:portType` /@msc:usingSession valor para o contrato. Esse atributo é uma extensão do WCF para WSDL 1.1.|  
|`Operations`|O `wsdl:operation` definições para o contrato.|  
  
### <a name="operations"></a>Operações  
 Uma <xref:System.ServiceModel.Description.OperationDescription> instância é mapeado para um `wsdl:portType` / `wsdl:operation`. Uma `OperationDescription` contém uma coleção de `MessageDescription` instâncias que descrevem as mensagens para a operação.  
  
 Dois comportamentos de operação participarem muito como uma `OperationDescription` é mapeado para um documento WSDL: `DataContractSerializerOperationBehavior` e `XmlSerializerOperationBehavior`.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|O `wsdl:portType` / `wsdl:operation` /@name valor para a operação.|  
|`ProtectionLevel`|Asserções de proteção na política de segurança anexada ao `wsdl:binding/wsdl:operation` mensagens para essa operação.|  
|`IsInitiating`|O `wsdl:portType` / `wsdl:operation` /@msc:isInitiating valor para a operação. Esse atributo é uma extensão do WCF para WSDL 1.1.|  
|`IsTerminating`|O `wsdl:portType` / `wsdl:operation` /@msc:isTerminating valor para a operação. Esse atributo é uma extensão do WCF para WSDL 1.1.|  
|`Messages`|O `wsdl:portType` / `wsdl:operation` / `wsdl:input` e `wsdl:portType` / `wsdl:operation` / `wsdl:output` mensagens para a operação.|  
|`Faults`|O `wsdl:portType` / `wsdl:operation` / `wsdl:fault` definições para a operação.|  
|`Behaviors`|O `DataContractSerializerOperationBehavior` e `XmlSerializerOperationBehavior` lidar com a associação da operação e as mensagens de operação.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>O DataContractSerializerOperationBehavior  
 O `DataContractSerializerOperationBehavior` para uma operação é um `IWsdlExportExtension` implementação que exporta as mensagens WSDL e a associação para essa operação. Os tipos de esquema XML são exportados usando o `XsdDataContractExporter`. O `DataContractSerializerOperationBehavior` também determina o exportador de uso, o estilo e o esquema e o importador a ser usado para essa operação.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|O `Style` propriedade para esse atributo é mapeado para o `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style valor para a operação.<br /><br /> O `DataContractSerializerOperationBehavior` oferece suporte apenas para o uso dos tipos de esquema literal no WSDL.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>O XmlSerializerOperationBehavior  
 O `XmlSerializerOperationBehavior` para uma operação é um `IWsdlExportExtension` implementação que exporta as mensagens WSDL e a associação para essa operação. Os tipos de esquema XML são exportados usando o `XmlSchemaExporter`. O `XmlSerializerOperationBehavior` também determina o exportador de uso, o estilo e o esquema e o importador a ser usado para essa operação.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|O `Style` propriedade para esse atributo é mapeado para o `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style valor para a operação.<br /><br /> O `Use` propriedade para esse atributo é mapeado para o `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use valores para todas as mensagens na operação.|  
  
### <a name="messages"></a>Mensagens  
 Um `MessageDescription` instância é mapeado para um `wsdl:message` que é referenciado por uma `wsdl:portType` / `wsdl:operation` / `wsdl:input` ou uma `wsdl:portType` / `wsdl:operation` / `wsdl:output`mensagem em uma operação. Um `MessageDescription` tem um corpo e cabeçalhos.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Action`|A ação SOAP ou WS-Addressing da mensagem.<br /><br /> Observe que as operações que usam a cadeia de caracteres de ação "*" não são representados no WSDL.|  
|`Direction`|`MessageDirection.Input` mapeia para `wsdl:input`.<br /><br /> `MessageDirection.Output` mapeia para `wsdl:output`.|  
|`ProtectionLevel`|Asserções de proteção na política de segurança anexada ao `wsdl:message` definição para esta mensagem.|  
|`Body`|O corpo da mensagem para a mensagem.|  
|`Headers`|Os cabeçalhos da mensagem.|  
|`ContractDescription.Name`, `OperationContract.Name`|Na exportação, usada para derivar a `wsdl:message` /@name valor.|  
  
#### <a name="message-body"></a>Corpo da mensagem  
 Um `MessageBodyDescription` instância é mapeado para o `wsdl:message` / `wsdl:part` definições para o corpo de uma mensagem. O corpo da mensagem pode ser encapsulado ou vazio.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`WrapperName`|Se o estilo não é RPC, o `WrapperName` mapeia para o nome do elemento referenciado pelo `wsdl:message` / `wsdl:part` com @name definido como "parâmetros".|  
|`WrapperNamespace`|Se o estilo não é RPC, o `WrapperNamespace` mapeia para o namespace do elemento para o `wsdl:message` / `wsdl:part` com @name definido como "parâmetros".|  
|`Parts`|As partes da mensagem para o corpo da mensagem.|  
|`ReturnValue`|O elemento filho do elemento wrapper se um elemento wrapper existir (estilo de documento encapsulado ou estilo RPC), caso contrário, a primeira `wsdl:message` / `wsdl:part` na mensagem.|  
  
#### <a name="message-parts"></a>Partes da mensagem  
 Um `MessagePartDescription` instância é mapeado para um `wsdl:message` / `wsdl:part` e o tipo de esquema XML ou o elemento que a parte da mensagem aponta para.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|O `wsd:message` / `wsdl:part` /@name valor para a parte da mensagem e o nome do elemento que aponta a parte da mensagem.|  
|`Namespace`|O namespace do elemento que aponta a parte da mensagem.|  
|`Index`|O índice do `wsdl:message` / `wsdl:part` para a mensagem.|  
|`ProtectionLevel`|Asserções de proteção na política de segurança anexada ao `wsdl:message` definição para essa parte da mensagem. A política é parametrizada para apontar para a parte de mensagem específica.|  
|`MessageType`|O tipo de esquema XML do elemento que aponta a parte da mensagem.|  
  
#### <a name="message-headers"></a>Cabeçalhos de mensagem  
 Um `MessageHeaderDescription` instância é uma parte da mensagem que também é mapeado para um `soap:header` de associação para a parte da mensagem.  
  
### <a name="faults"></a>Falhas  
 Um `FaultDescription` instância é mapeado para um `wsdl:portType` / `wsdl:operation` / `wsdl:fault` definição e seus respectivos `wsdl:message` definição. O `wsdl:message` é adicionado ao namespace de destino como seu tipo de porta WSDL associado. O `wsdl:message` tem uma parte da mensagem único chamada "detail" que aponta para o elemento de esquema XML que corresponde do `DefaultType` valor da propriedade para o `FaultDescription` instância.  
  
|Propriedades|Mapeamento de WSDL|  
|----------------|------------------|  
|`Name`|O `wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name valor para a falha.|  
|`Namespace`|O namespace do elemento de esquema XML parte da mensagem de detalhe de falha aponta para.|  
|`Action`|A ação SOAP ou WS-Addressing para a falha.|  
|`ProtectionLevel`|Asserções de proteção na política de segurança anexada ao `wsdl:message` definição para essa falha.|  
|`DetailType`|O tipo de esquema XML do elemento que a parte da mensagem de detalhe aponta.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Usado para derivar a `wsdl:message` /@name valor para a mensagem de falha.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description>
