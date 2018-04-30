---
title: Atributos de ServiceModel e referência de ServiceDescription
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ba8888c2a1bd3c16ab6d216c365870c0df0e499a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atributos de ServiceModel e referência de ServiceDescription
O *árvore descrição* é a hierarquia de tipos (começando com o <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> classe) que juntas descrevem todos os aspectos de um serviço. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usa uma descrição de árvore para criar um tempo de execução de serviço válido, para publicar Web Services Description Language (WSDL), linguagem de definição de esquema XML (XSD) e declarações de política (metadados) sobre o serviço que os clientes podem usar para conectar e usar o serviço e Gere diversas representações de arquivo de código e configuração dos valores de árvore de descrição.  
  
 Este tópico descreve as propriedades como relacionadas ao contrato são obtidos do contrato de serviço e como eles são implementados e adicionados à árvore de descrição. Em alguns casos, os valores de atributo são convertidos em Propriedades de comportamento e comportamento é inserido na árvore de descrição. Para obter mais informações sobre como os valores de árvore de descrição são convertidos em metadados, consulte [ServiceDescription e referência de WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Operações de mapeamento à árvore de descrição  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos, contratos de serviço são modelados por (classes ou interfaces) que usam atributos para marcar a interface ou classe e seus métodos como um agrupamento de operações. Quando um <xref:System.ServiceModel.ServiceHost> classe é aberta, quaisquer contratos de serviço e as implementações são refletidas em e mescladas com informações de configuração em uma árvore de descrição.  
  
 Há dois tipos de modelos de operação: o *parâmetro* modelo e o *contrato de mensagem* modelo. O modelo de parâmetro usa métodos gerenciados que não têm um parâmetro ou tipo de valor de retorno que foi marcado pelo <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> classe. Nesse modelo, os desenvolvedores controlar a serialização de parâmetros em valores de retorno, mas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera os valores que são usados para popular a árvore de descrição para o serviço e seu contrato.  
  
 Associações especificadas nos arquivos de configuração são carregadas diretamente para o <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> propriedade.  
  
|Propriedade ServiceBehaviorAttribute|Valor de árvore de descrição afetado|  
|---------------------------------------|-------------------------------------|  
|Nome|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Namespace|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Conjuntos de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> propriedade para todas as operações.|  
|MaxItemsInObjectGraph|Conjuntos de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> propriedade para todas as operações.|  
  
|Propriedade ServiceContractAttribute|Valor de árvore de descrição afetado|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> adicionado a todas as operações <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> e possivelmente os níveis de proteção do filho. Para obter mais informações sobre a hierarquia de nível de proteção, consulte [Noções básicas sobre nível de proteção](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|Valor de ServiceKnownTypesAttribute|Valor de árvore de descrição afetado|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Valor de OperationContractAttribute|Valor de árvore de descrição afetado|  
|--------------------------------------|-------------------------------------|  
|Ação|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> para a mensagem de saída ou a mensagem de entrada, dependendo do contrato de retorno de chamada/contrato.|  
|AsyncPattern|Se true, <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> e <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mapeia para uma única <xref:System.ServiceModel.Description.MessageDescription> em <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Nome|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> e possivelmente os níveis de proteção do filho. Para obter mais informações sobre a hierarquia de nível de proteção, consulte [Noções básicas sobre nível de proteção](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> para a mensagem de saída ou a mensagem de entrada, dependendo do contrato de retorno de chamada/contrato.|  
  
|Valor de FaultContractAttribute|Valor de árvore de descrição afetado|  
|----------------------------------|-------------------------------------|  
|Ação|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> Dependendo de contrato de retorno de chamada/contrato.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Nome|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Namespace|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|Valor de DataContractFormatAttribute|Valor de árvore de descrição afetado|  
|---------------------------------------|-------------------------------------|  
|Use|O <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> valor é definido no <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> para a operação.|  
  
|Valor de XmlSerializerFormatAttribute|Valor de árvore de descrição afetado|  
|----------------------------------------|-------------------------------------|  
|Estilo|Isso <xref:System.ServiceModel.XmlSerializerFormatAttribute> propriedade é definida no <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> para a operação.|  
|Use|O <xref:System.ServiceModel.XmlSerializerFormatAttribute> é ativada a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> para a operação.|  
  
|Valor de TransactionFlowAttribute|Valor de árvore de descrição afetado|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|O <xref:System.ServiceModel.TransactionFlowAttribute> é adicionado como um comportamento de operação para o <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> propriedade.|  
  
|Valor MessageContractAttribute|Valor de árvore de descrição afetado|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Valor de MessageHeaderAttribute|Valor de árvore de descrição afetado|  
|----------------------------------|-------------------------------------|  
|ator|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> no cabeçalho correspondente <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> no cabeçalho correspondente <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Nome|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> no cabeçalho correspondente <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Namespace|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> no cabeçalho correspondente <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> no cabeçalho correspondente <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Retransmissão|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> no cabeçalho correspondente <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Valor de MessageBodyMemberAttribute|Valor de árvore de descrição afetado|  
|--------------------------------------|-------------------------------------|  
|Nome|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> para a parte correspondente em <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Namespace|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> para a parte correspondente em <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Pedido|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> para a parte correspondente em <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> para a parte correspondente em <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Valor de MessageHeaderArrayAttribute|Valor de árvore de descrição afetado|  
|---------------------------------------|-------------------------------------|  
|ator|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Nome|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Namespace|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Retransmissão|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Valor de MessagePropertyAttribute|Valor de árvore de descrição afetado|  
|------------------------------------|-------------------------------------|  
|Nome|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Valor de MessageParameterAttribute|Valor de árvore de descrição afetado|  
|-------------------------------------|-------------------------------------|  
|Nome|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> para a parte correspondente em <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Para obter mais informações sobre como os valores de árvore de descrição são convertidos em metadados, consulte [ServiceDescription e referência de WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência WSDL e ServiceDescription](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
