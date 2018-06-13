---
title: Exportando metadados personalizados para uma extensão do WCF
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: c2ae547f10e96a1fdc16fc428e98145fc81c59d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804038"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>Exportando metadados personalizados para uma extensão do WCF
No Windows Communication Foundation (WCF), a exportação de metadados é o processo de descrever os pontos de extremidade de serviço e projeção-los em uma representação padronizada paralela que os clientes podem usar para entender como usar o serviço. Metadados personalizados consistem em elementos XML que não é possível exportar os exporters metadados fornecidos pelo sistema. Normalmente, isso inclui elementos WSDL personalizados para elementos de associação e comportamentos definidos pelo usuário e declarações de política sobre os recursos e requisitos de associações e contratos.  
  
 Esta seção descreve a exportação WSDL personalizado ou declarações de política e não se concentra em que o processo de exportação. Para obter mais informações sobre como usar os tipos que exportar e importar metadados seja metadados personalizados ou construída pelo sistema, consulte [exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Visão geral  
 Quando os metadados são publicados usando o <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>, o <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> é examinado e XSD e WSDL – incluindo as declarações de política – são gerados para todos os contratos e associações WCF pode suportar usando atributos fornecidos pelo sistema e associações. No entanto, os atributos de comportamento personalizado ou elementos de associação requerem suporte antes que eles podem ser exportados corretamente.  
  
 Esta seção descreve:  
  
1.  Como implementar e usar o <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface, que expõe os dados de geração de WSDL para você antes de publicar o WSDL.  
  
2.  Como implementar e usar o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface, que expõe os dados de política para você antes de exportar as declarações de política em dados WSDL.  
  
 Para obter mais informações sobre como importar WSDL personalizado e declarações de política, consulte [importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="exporting-custom-wsdl-elements"></a>Exportando elementos WSDL personalizado  
 Implementar o <xref:System.ServiceModel.Description.IWsdlExportExtension> em um comportamento de operação, o comportamento de contrato, o comportamento de ponto de extremidade ou o elemento de associação (<xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>, <xref:System.ServiceModel.Description.IEndpointBehavior>, ou <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> respectivamente) e insira os comportamentos ou elementos de associação para o Descrição do serviço que você está tentando exportar. (Para obter mais informações sobre a inserção de comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)). O <xref:System.ServiceModel.Description.IWsdlExportExtension> é chamado para cada ponto de extremidade e cada ponto de extremidade exporta o contrato primeiro se ele já não foi exportado. Você pode participar de qualquer processo de exportação, dependendo das suas necessidades:  
  
-   Use o <xref:System.ServiceModel.Description.WsdlContractConversionContext> para modificar os metadados exportado o <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método.  
  
-   Use o <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> para modificar os metadados exportado para o ponto de extremidade no <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método.  
  
 O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método é chamado em todos os <xref:System.ServiceModel.Description.IWsdlExportExtension> implementações dentro de <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> instância que está sendo exportada.  O <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> método é chamado em todos os <xref:System.ServiceModel.Description.IWsdlExportExtension> implementações com a <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> instância que está sendo exportada.  
  
 Para obter mais informações, consulte [como: exportar personalizado WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) e o exemplo [publicação de WSDL personalizado](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md).  
  
## <a name="exporting-custom-policy-assertions"></a>Exportar declarações de política personalizada  
 Implementar o <xref:System.ServiceModel.Description.IPolicyExportExtension> em um <xref:System.ServiceModel.Channels.BindingElement> e adicione o elemento de associação para a associação para gravar asserções de políticas personalizadas sobre associação de recursos de suporte e contrato em WSDL. O <xref:System.ServiceModel.Description.IPolicyExportExtension> é chamado uma vez ao exportar o elemento de associação implementados em uma associação e passa o <xref:System.ServiceModel.Description.PolicyConversionContext> para o <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> método. Você pode usar os métodos no <xref:System.ServiceModel.Description.PolicyConversionContext> instância para adicionar a declarações de política anexada à associação de WSDL nas entidades de mensagem, a operação ou ponto de extremidade.  
  
 Para obter mais informações, consulte [como: exportar declarações de política personalizada](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como exportar o WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Como exportar declarações de política personalizada](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)  
 [Importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
