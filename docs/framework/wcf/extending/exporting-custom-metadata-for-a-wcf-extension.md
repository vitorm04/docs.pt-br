---
title: Exportando metadados personalizados para uma extensão do WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: fa6a2751f8ef3326febc7fa6bed85e10603701c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616050"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Exportando metadados personalizados para uma extensão do WCF
No Windows Communication Foundation (WCF), a exportação de metadados é o processo de descrever os pontos de extremidade de serviço e Projetando-os em uma representação paralela e padronizada que os clientes podem usar para entender como usar o serviço. Metadados personalizados consistem em elementos XML que o Exportadores de metadados fornecidos pelo sistema não é possível exportar. Normalmente, isso inclui elementos WSDL personalizados para comportamentos definidos pelo usuário e elementos de associação e declarações de política sobre os recursos e requisitos de associações e contratos.  
  
 Esta seção descreve a exportação de WSDL personalizado ou declarações de política e não se concentra em que o processo de exportação. Para obter mais informações sobre como usar os tipos de exportação e importação de metadados, independentemente se os metadados são personalizadas ou sistema construído, consulte [exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Visão geral  
 Quando os metadados são publicados usando o <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, o <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> é examinado e XSD e WSDL – incluindo as declarações de política – são gerados para todos os contratos e associações WCF pode dar suporte a usando os atributos fornecidos pelo sistema e associações. No entanto, os atributos de comportamento personalizado ou elementos de associação exigem suporte antes que eles podem ser exportados corretamente.  
  
 Esta seção descreve:  
  
1.  Como implementar e usar o <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface, que expõe os dados de geração de WSDL para você antes de publicar o WSDL.  
  
2.  Como implementar e usar o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface, que expõe a política de dados para você antes de exportar as declarações de política nos dados WSDL.  
  
 Para obter mais informações sobre como importar WSDL personalizado e declarações de política, consulte [importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Exportando elementos WSDL personalizado  
 Implementar o <xref:System.ServiceModel.Description.IWsdlExportExtension> em um comportamento da operação, o comportamento de contrato, o comportamento de ponto de extremidade ou o elemento de associação (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, ou <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> , respectivamente) e insira o comportamentos ou elementos de associação para o Descrição do serviço que você está tentando exportar. (Para obter mais informações sobre a inserção de comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). O <xref:System.ServiceModel.Description.IWsdlExportExtension> é chamado para cada ponto de extremidade e cada ponto de extremidade exporta o contrato primeiro se ele já não foi exportado. Você pode participar de qualquer processo de exportação, dependendo das suas necessidades:  
  
-   Use o <xref:System.ServiceModel.Description.WsdlContractConversionContext> para modificar os metadados exportados no <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método.  
  
-   Use o <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> para modificar os metadados exportados para o ponto de extremidade no <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método.  
  
 O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método é chamado em todos os <xref:System.ServiceModel.Description.IWsdlExportExtension> implementações dentro de <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> instância que está sendo exportada.  O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método é chamado em todos os <xref:System.ServiceModel.Description.IWsdlExportExtension> implementações com o <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instância que está sendo exportada.  
  
 Para obter mais informações, confira [Como: Exportar o WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) e o exemplo [publicação de WSDL personalizado](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Exportando as declarações de política personalizada  
 Implemente a <xref:System.ServiceModel.Description.IPolicyExportExtension> em um <xref:System.ServiceModel.Channels.BindingElement> e adicione o elemento de associação para a associação para escrever declarações de política personalizadas sobre recursos de suporte e contrato no WSDL de ligação. O <xref:System.ServiceModel.Description.IPolicyExportExtension> é chamado uma vez ao exportar o elemento de associação implementado em uma associação e passa a <xref:System.ServiceModel.Description.PolicyConversionContext> para o <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> método. Você pode usar os métodos no <xref:System.ServiceModel.Description.PolicyConversionContext> instância a ser adicionada para as declarações de política anexada à associação WSDL nas entidades de mensagem, operação ou ponto de extremidade.  
  
 Para obter mais informações, confira [Como: Exportar declarações de política personalizada](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Consulte também
- [Como: Exportar o WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Como: Exportar declarações de política personalizada](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)
- [Importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
