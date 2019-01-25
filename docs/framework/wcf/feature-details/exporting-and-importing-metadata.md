---
title: Exportando e importando metadados
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: f99b8626ca4a89bf94e44652e8277f8b2c147fe3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706372"
---
# <a name="exporting-and-importing-metadata"></a>Exportando e importando metadados
No Windows Communication Foundation (WCF), exportação de metadados é o processo de descrever os pontos de extremidade de serviço e Projetando-os em uma representação paralela e padronizada que os clientes podem usar para entender como usar o serviço. Importação de metadados de serviço é o processo de geração <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias ou partes de metadados de serviço.  
  
## <a name="exporting-metadata"></a>Exportando metadados  
 Para exportar metadados de <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instâncias, use uma implementação do <xref:System.ServiceModel.Description.MetadataExporter> classe abstrata. O <xref:System.ServiceModel.Description.WsdlExporter> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataExporter> incluído com o WCF de classe abstrata.  
  
 O <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> tipo gera metadados de descrição linguagem WSDL (Web Services) com expressões de política anexada encapsuladas em um <xref:System.ServiceModel.Description.MetadataSet> instância. Você pode usar um <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instância para exportar os metadados para iterativamente <xref:System.ServiceModel.Description.ContractDescription> objetos e <xref:System.ServiceModel.Description.ServiceEndpoint> objetos. Você também pode exportar uma coleção de <xref:System.ServiceModel.Description.ServiceEndpoint> objetos e associá-los com um nome de serviço específico.  
  
> [!NOTE]
>  Você só pode usar o `WsdlExporter` para exportar metadados de `ContractDescription` instâncias que contêm o common language runtime (CLR) informações de tipo, como um `ContractDescription` instância criada usando o `ContractDescription.GetContract` método ou criado como parte do `ServiceDescription` para um `ServiceHost` instância. Não é possível usar o `WsdlExporter` para exportar metadados de `ContractDescription` instâncias importado dos metadados de serviço ou construído sem informações de tipo.  
  
## <a name="importing-metadata"></a>Importando metadados  
  
### <a name="importing-wsdl-documents"></a>Importar documentos WSDL  
 Para importar metadados de serviço do WCF, use uma implementação do <xref:System.ServiceModel.Description.MetadataImporter> classe abstrata. O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataImporter> incluído com o WCF de classe abstrata. O <xref:System.ServiceModel.Description.WsdlImporter> digite importações metadados WSDL com políticas anexadas agrupado em um <xref:System.ServiceModel.Description.MetadataSet> objeto.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo lhe dá controle sobre como importar os metadados. Você pode importar todos os pontos de extremidade, todas as associações, ou todos os contratos. Você pode importar todos os pontos de extremidade associados a um serviço específico do WSDL, a associação ou o tipo de porta. Você também pode importar o ponto de extremidade para uma porta WSDL específica, a associação para uma associação específica do WSDL ou o contrato para um tipo específico de porta WSDL.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> também expõe um <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> propriedade que permite que você especifique um conjunto de contratos que não precisam ser importados. O <xref:System.ServiceModel.Description.WsdlImporter> usa os contratos no <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> propriedade em vez de importar um contrato com o mesmo nome qualificado de metadados.  
  
### <a name="importing-policies"></a>Importando políticas  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo de coleta as expressões de política anexadas à mensagem, operação, e a política de ponto de extremidade assuntos e, em seguida, usa o <xref:System.ServiceModel.Description.IPolicyImportExtension> implementações no <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> coleção para importar as expressões de política.  
  
 A lógica de importação de política automaticamente trata referências de diretiva a expressões de política no mesmo documento WSDL e é identificada com uma `wsu:Id` ou `xml:id` atributo. A lógica de política de importação protege os aplicativos contra referências circulares de política, limitando o tamanho de uma expressão de política para 4096 nós, em que um nó é um dos seguintes elementos: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 A lógica de importação de política também normaliza automaticamente expressões de política. Aninhado expressões de política e o `wsp:Optional` atributo não são normalizados. A quantidade de processamento de normalização feito é limitada a 4096 etapas, onde cada etapa resulta em uma declaração de política ou um elemento filho de um `wsp:ExactlyOne` elemento.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo tenta até 32 combinações de alternativas de política anexadas para as entidades de política WSDL diferentes. Se nenhuma combinação importa corretamente, a primeira combinação é usada para construir uma ligação personalizada parcial.  
  
## <a name="error-handling"></a>Tratamento de erros  
 Tanto a <xref:System.ServiceModel.Description.MetadataExporter> e o <xref:System.ServiceModel.Description.MetadataImporter> tipos expõem um `Errors` que pode conter uma coleção de mensagens de erro e aviso encontradas durante os processos de importação e exportação, respectivamente, que pode ser usado ao implementar ferramentas de propriedade.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo geralmente gera uma exceção para uma exceção capturada durante o processo de importação e adiciona um erro correspondente ao seu `Errors` propriedade. O <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, e <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> métodos, no entanto, não geram essas exceções, por isso, você deve verificar o `Errors` propriedade para determinar se qualquer problema ocorreu ao chamar esses métodos.  
  
 O <xref:System.ServiceModel.Description.WsdlExporter> tipo lança novamente todas as exceções capturadas durante o processo de exportação. Essas exceções não são capturadas como erros no `Errors` propriedade. Uma vez o <xref:System.ServiceModel.Description.WsdlExporter> gera uma exceção, ele está em um estado de falha e não pode ser reutilizado. O <xref:System.ServiceModel.Description.WsdlExporter> Adicionar avisos para seu `Errors` propriedade quando uma operação não pode ser exportada porque ele usa ações de curinga e quando são encontrados nomes de associação duplicada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Importar metadados para pontos de extremidade de serviço](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Descreve como importar metadados baixado para objetos de descrição.  
  
 [Como: Exportar metadados de pontos de extremidade de serviço](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Descreve como exportar objetos de descrição nos metadados.  
  
 [Referência WSDL e ServiceDescription](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Descreve o mapeamento entre os objetos de descrição e o WSDL.  
  
 [Como: Use Svcutil.exe para exportar metadados de código de serviço compilado](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Descreve o uso de Svcutil.exe para exportar metadados para os serviços, contratos e tipos de dados em assemblies compilados.  
  
 [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Descreve o subconjunto do esquema XML (XSD) usada pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever o common language runtime (CLR) tipos para serialização de XML.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Consulte também
- [Exportando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)
- [Importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
