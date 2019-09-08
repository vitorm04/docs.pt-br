---
title: Exportando metadados personalizados para uma extensão do WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797188"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Exportando metadados personalizados para uma extensão do WCF
No Windows Communication Foundation (WCF), a exportação de metadados é o processo de descrever os pontos de extremidade de serviço e projetar-los em uma representação paralela e padronizada que os clientes podem usar para entender como usar o serviço. Metadados personalizados consistem em elementos XML que os exportadores de metadados fornecidos pelo sistema não podem exportar. Normalmente, isso inclui elementos WSDL personalizados para comportamentos definidos pelo usuário e elementos de ligação e declarações de política sobre os recursos e requisitos de associações e contratos.  
  
 Esta seção descreve como exportar declarações WSDL ou de política personalizadas e não se concentra no processo de exportação em si. Para obter mais informações sobre como usar os tipos que exportam e importam metadados independentemente de os metadados terem sido personalizados ou construídos pelo sistema, consulte [exportando e importando metadados](../feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Visão geral  
 Quando os metadados são publicados usando <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>o, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> o é examinado e XSD e o WSDL, incluindo as asserções de política, são gerados para todos os contratos e associações que o WCF pode dar suporte usando atributos e associações fornecidos pelo sistema. No entanto, os atributos de comportamento personalizado ou os elementos de ligação exigem suporte antes que possam ser exportados corretamente.  
  
 Esta seção descreve:  
  
1. Como implementar e usar a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface, que expõe os dados de geração WSDL para você antes de publicar o WSDL.  
  
2. Como implementar e usar a <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface, que expõe os dados de política para você antes de exportar as declarações de política em dados WSDL.  
  
 Para obter mais informações sobre como importar declarações personalizadas de WSDL e de política, consulte [importando metadados personalizados para uma extensão WCF](importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Exportando elementos WSDL personalizados  
 Implemente <xref:System.ServiceModel.Description.IWsdlExportExtension> o em um comportamento de operação, comportamento de contrato, comportamento de ponto<xref:System.ServiceModel.Description.IOperationBehavior>de extremidade ou elemento <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> de associação (, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>ou respectivamente) e insira os comportamentos ou elementos de associação no Descrição do serviço que você está tentando exportar. (Para obter mais informações sobre como inserir comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md)). O <xref:System.ServiceModel.Description.IWsdlExportExtension> será chamado para cada ponto de extremidade e cada ponto de extremidade exportará o contrato primeiro se ele ainda não tiver sido exportado. Você pode participar de um processo de exportação, dependendo das suas necessidades:  
  
- Use o <xref:System.ServiceModel.Description.WsdlContractConversionContext> para modificar os metadados exportados <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> no método.  
  
- Use o <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> para modificar os metadados exportados para o ponto <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> de extremidade no método.  
  
 O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método é chamado em todas <xref:System.ServiceModel.Description.IWsdlExportExtension> as implementações <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> na instância que está sendo exportada.  O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método é chamado em todas <xref:System.ServiceModel.Description.IWsdlExportExtension> as implementações <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> com a instância que está sendo exportada.  
  
 Para obter mais informações, confira [Como: Exporte o](how-to-export-custom-wsdl.md) WSDL personalizado e a [publicação de WSDL personalizada](../samples/custom-wsdl-publication.md)de exemplo.  
  
## <a name="exporting-custom-policy-assertions"></a>Exportando declarações de política personalizada  
 Implemente <xref:System.ServiceModel.Description.IPolicyExportExtension> o em <xref:System.ServiceModel.Channels.BindingElement> a e adicione o elemento Binding à associação para escrever declarações de política personalizada sobre suporte de associação e recursos de contrato no WSDL. O <xref:System.ServiceModel.Description.IPolicyExportExtension> é chamado uma vez ao exportar o elemento de associação implementado em uma associação e <xref:System.ServiceModel.Description.PolicyConversionContext> passa o <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> para o método. Você pode usar os métodos na <xref:System.ServiceModel.Description.PolicyConversionContext> instância para adicionar às declarações de política anexadas à associação WSDL na mensagem, na operação ou nos assuntos do ponto de extremidade.  
  
 Para obter mais informações, confira [Como: Exportar declarações](how-to-export-custom-policy-assertions.md)de política personalizada.  
  
## <a name="see-also"></a>Consulte também

- [Como: Exportar WSDL personalizado](how-to-export-custom-wsdl.md)
- [Como: Exportar declarações de política personalizada](how-to-export-custom-policy-assertions.md)
- [Importando metadados personalizados para uma extensão do WCF](importing-custom-metadata-for-a-wcf-extension.md)
