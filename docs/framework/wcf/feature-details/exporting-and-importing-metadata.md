---
title: Exportando e importando metadados
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], exporting and importing
ms.assetid: 614a75bb-e0b0-4c95-b6d8-02cb5e5ddb38
ms.openlocfilehash: 497feb80d5930a784022877cfaa6e6c76a3047a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495418"
---
# <a name="exporting-and-importing-metadata"></a>Exportando e importando metadados
No Windows Communication Foundation (WCF), exportação de metadados é o processo de descrever os pontos de extremidade de serviço e projeção-los em uma representação padronizada paralela que os clientes podem usar para entender como usar o serviço. Importação de metadados de serviço é o processo de geração de <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias ou partes de metadados de serviço.  
  
## <a name="exporting-metadata"></a>Exportação de metadados  
 Para exportar metadados de <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instâncias, use uma implementação do <xref:System.ServiceModel.Description.MetadataExporter> classe abstrata. O <xref:System.ServiceModel.Description.WsdlExporter> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataExporter> incluído com o WCF de classe abstrata.  
  
 O <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> tipo gera metadados de WSDL Web Services Description Language () com expressões de política anexada encapsuladas em um <xref:System.ServiceModel.Description.MetadataSet> instância. Você pode usar um <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> instância iterativamente exportar metadados para <xref:System.ServiceModel.Description.ContractDescription> objetos e <xref:System.ServiceModel.Description.ServiceEndpoint> objetos. Você também pode exportar uma coleção de <xref:System.ServiceModel.Description.ServiceEndpoint> objetos e associá-los com um nome de serviço específico.  
  
> [!NOTE]
>  Você só pode usar o `WsdlExporter` para exportar metadados de `ContractDescription` instâncias que contêm o common language runtime (CLR) digite informações, como um `ContractDescription` instância criada usando o `ContractDescription.GetContract` método ou criado como parte do `ServiceDescription` para um `ServiceHost` instância. Não é possível usar o `WsdlExporter` para exportar metadados de `ContractDescription` instâncias importados de metadados de serviço ou construída sem informações de tipo.  
  
## <a name="importing-metadata"></a>Importação de metadados  
  
### <a name="importing-wsdl-documents"></a>Importando documentos WSDL  
 Para importar metadados de serviço do WCF, use uma implementação de <xref:System.ServiceModel.Description.MetadataImporter> classe abstrata. O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataImporter> incluído com o WCF de classe abstrata. O <xref:System.ServiceModel.Description.WsdlImporter> digite importa metadados WSDL com políticas anexados agrupados em um <xref:System.ServiceModel.Description.MetadataSet> objeto.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo lhe dá controle sobre como importar os metadados. Você pode importar todos os pontos de extremidade, todas as associações de ou em todos os contratos. Você pode importar todos os pontos de extremidade associados a um serviço específico de WSDL, associação ou tipo de porta. Você também pode importar o ponto de extremidade para uma porta específica do WSDL, a associação para uma associação WSDL específica ou o contrato para um tipo específico de porta WSDL.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> também expõe um <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> propriedade que permite que você especifique um conjunto de contratos que não precisam ser importados. O <xref:System.ServiceModel.Description.WsdlImporter> usa os contratos no <xref:System.ServiceModel.Description.MetadataImporter.KnownContracts%2A> propriedade em vez de importar um contrato com o mesmo nome qualificado de metadados.  
  
### <a name="importing-policies"></a>Importação de políticas  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo coleta as expressões de política anexadas à mensagem, operação, e a política de ponto de extremidade assuntos e, em seguida, usa o <xref:System.ServiceModel.Description.IPolicyImportExtension> implementações no <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> coleção para importar as expressões de política.  
  
 A lógica de política de importação lida com referências de política para expressões de política no mesmo documento WSDL automaticamente e é identificada com um `wsu:Id` ou `xml:id` atributo. A lógica de política de importação protege os aplicativos referências circulares política limitando o tamanho de uma expressão de diretiva para 4096 nós, em que um nó é um dos seguintes elementos: `wsp:Policy`, `wsp:All`, `wsp:ExactlyOne`, `wsp:policyReference`.  
  
 A lógica de política de importação automaticamente normaliza expressões de política. Aninhados expressões de política e o `wsp:Optional` atributo não são normalizados. A quantidade de processamento de normalização feito é limitada a 4096 etapas, onde cada etapa resulta em uma declaração de política ou um elemento filho de um `wsp:ExactlyOne` elemento.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo tenta até 32 combinações de alternativas de política anexadas para as entidades de política WSDL diferentes. Se nenhuma combinação importa corretamente, a primeira combinação é usada para construir uma associação personalizada parcial.  
  
## <a name="error-handling"></a>Tratamento de erros  
 Tanto o <xref:System.ServiceModel.Description.MetadataExporter> e <xref:System.ServiceModel.Description.MetadataImporter> tipos expor um `Errors` propriedade que pode conter uma coleção de mensagens de erro e aviso encontradas durante os processos de importação e exportação, respectivamente, que pode ser usado durante a implementação de ferramentas.  
  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo geralmente gera uma exceção de uma exceção capturada durante o processo de importação e adiciona um erro correspondente ao seu `Errors` propriedade. O <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A>, e <xref:System.ServiceModel.Description.WsdlImporter.ImportEndpoints%2A> métodos, no entanto, não gerar essas exceções, por isso, você deve verificar o `Errors` propriedade para determinar se os problemas ocorreram ao chamar esses métodos.  
  
 O <xref:System.ServiceModel.Description.WsdlExporter> tipo relança qualquer exceção capturada durante o processo de exportação. Essas exceções não são capturadas como erros de `Errors` propriedade. Uma vez o <xref:System.ServiceModel.Description.WsdlExporter> lançará uma exceção, ele está em um estado de falha e não pode ser reutilizado. O <xref:System.ServiceModel.Description.WsdlExporter> Adicionar avisos para sua `Errors` propriedade quando uma operação não pode ser exportada porque ele usa o curinga ações e quando os nomes de associação duplicada forem encontrados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como importar metadados para pontos de extremidade de serviço](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)  
 Descreve como importar metadados baixado para objetos de descrição.  
  
 [Como exportar metadados de pontos de extremidade de serviço](../../../../docs/framework/wcf/feature-details/how-to-export-metadata-from-service-endpoints.md)  
 Descreve como exportar objetos de descrição nos metadados.  
  
 [Referência WSDL e ServiceDescription](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)  
 Descreve o mapeamento entre os objetos de descrição e WSDL.  
  
 [Como usar o Svcutil.exe para exportar metadados de código de serviço compilado](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)  
 Descreve o uso de Svcutil.exe para exportar metadados para os serviços, contratos e tipos de dados em assemblies compilados.  
  
 [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 Descreve o subconjunto do esquema XML (XSD) usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever o common language runtime (CLR) tipos de serialização de XML.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Description.WsdlExporter>  
  
 <xref:System.ServiceModel.Description.WsdlImporter>  
  
## <a name="see-also"></a>Consulte também  
 [Exportando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 [Importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
