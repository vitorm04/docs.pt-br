---
title: "Importando metadados personalizados para uma extensão do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d05cbb3091eb3a6bae3341947e14fcc1e78d1207
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Importando metadados personalizados para uma extensão do WCF
Em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], importação de metadados é o processo de geração de uma representação abstrata de um serviço ou seus componentes de seus metadados. Por exemplo, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode importar <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias, <xref:System.ServiceModel.Channels.Binding> instâncias ou <xref:System.ServiceModel.Description.ContractDescription> instâncias de um WSDL documentos para um serviço. Para importar os metadados de serviço em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], use uma implementação do <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> classe abstrata. Tipos que derivam de <xref:System.ServiceModel.Description.MetadataImporter> classe implementa o suporte para formatos de metadados de importação que aproveitam o WS-Policy importar lógica em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Metadados personalizados consistem em elementos XML que não é possível importar os importadores de metadados fornecidos pelo sistema. Normalmente, isso inclui as extensões WSDL e declarações de política personalizada.  
  
 Esta seção descreve como importar as extensões WSDL e declarações de política. Ele não se concentra em que o processo de importação. Para obter mais informações sobre como usar os tipos que exportar e importar metadados independentemente se os metadados são personalizados ou suporte de sistema, consulte [exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Visão Geral  
 O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataImporter> acompanha de classe abstrata [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. O <xref:System.ServiceModel.Description.WsdlImporter> tipo importa os metadados WSDL anexado políticas que são empacotadas em um <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objeto. Declarações de política e as extensões WSDL que não reconhecem os importadores padrão são passadas com todos os importadores WSDL e política personalizada registrado para a importação. Normalmente, importers são implementados para dar suporte a elementos de associação definida pelo usuário ou para modificar o contrato importado.  
  
 Esta seção descreve:  
  
1.  Como implementar e usar o <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface, que expõe os dados WSDL personalizados importadores antes da geração de descrições e a geração de código. Você pode usar essa interface para examinar ou modificar os tipos de descrição e a compilação de código executada usando um determinado conjunto de metadados.  
  
2.  Como implementar e usar o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface, que expõe as declarações de política para importadores antes da geração de objetos de descrição. Você pode usar essa interface para examinar ou modificar a associação ou o contrato com base nas políticas de download.  
  
 Para obter mais informações sobre a exportação WSDL personalizado e declarações de política, consulte [exportando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Extensões de importação WSDL personalizado  
 Para adicionar suporte para a importação de extensões WSDL, implementar a <xref:System.ServiceModel.Description.IWsdlImportExtension> de interface e, em seguida, adicione sua implementação para o <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> propriedade. O <xref:System.ServiceModel.Description.WsdlImporter> também pode carregar implementações do <xref:System.ServiceModel.Description.IWsdlImportExtension> interface registrada no arquivo de configuração de aplicativo. Observe que um número de importadores WSDL é registrado por padrão e a ordem dos importadores WSDL registrados é significativa.  
  
 Quando o importador WSDL personalizado é carregado e usado pelo <xref:System.ServiceModel.Description.WsdlImporter>, primeiro o <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> método é chamado para habilitar a modificação de metadados antes do processo de importação. Em seguida, os contratos são importados após o qual o <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> método é chamado para habilitar a modificação dos contratos importados dos metadados. Por fim, o <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> método é chamado para habilitar a modificação dos pontos de extremidade importados.  
  
 Para obter mais informações, consulte [como: importar personalizado WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Importação de declarações de política personalizada  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo e o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tratar automaticamente o processamento de uma variedade de tipos de declaração de política em expressões de política anexados a documentos WSDL. Essas ferramentas coletam, normalizam e mesclagem as expressões de política anexadas às portas WSDL e associações de WSDL.  
  
 Para adicionar suporte para a importação de declarações de política personalizada, implementar a <xref:System.ServiceModel.Description.IPolicyImportExtension> de interface e, em seguida, adicione sua implementação para o <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> propriedade. O <xref:System.ServiceModel.Description.MetadataImporter> também pode carregar implementações do <xref:System.ServiceModel.Description.IPolicyImportExtension> interface registrada no arquivo de configuração de aplicativo. Observe que um número de importadores de política é registrado por padrão e a ordem dos importadores de política registrado é significativa.  
  
 O sistema de metadados chama repetidamente o <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> método em toda a diretiva registrado importar extensões para cada combinação de alternativas de política anexado para as entidades de política de mensagem, a operação e o ponto de extremidade. Ao importar uma porta WSDL, políticas anexadas para a porta e a associação WSDL correspondente são mescladas antes de chamar as extensões de importação de política. As alternativas de política são disponibilizadas por meio de um <xref:System.ServiceModel.Description.PolicyConversionContext> como <xref:System.ServiceModel.Description.PolicyAssertionCollection> objetos. Cada <xref:System.ServiceModel.Description.PolicyAssertionCollection> é uma coleção de declarações de política representado por <xref:System.Xml.XmlElement> objetos.  
  
 O <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> e <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> propriedades o <xref:System.ServiceModel.Description.PolicyConversionContext> objeto expor o <xref:System.ServiceModel.Description.ContractDescription> e <xref:System.ServiceModel.Channels.BindingElement> objetos que foram importados do WSDL. Declarações de política de processo de política importação extensões Localizando instâncias de um tipo de declaração de política específica, fazer as alterações correspondentes no <xref:System.ServiceModel.Description.ContractDescription> ou <xref:System.ServiceModel.Channels.BindingElement> objetos e, em seguida, removendo as declarações de política de ocorrespondente<xref:System.ServiceModel.Description.PolicyAssertionCollection> instância.  
  
 O `wsp:Optional` atributo e expressões de política aninhadas não são normalizadas, para que as extensões de importação de política devem tratar essas construções de política. Além disso, as extensões de importação de política podem ser chamadas várias vezes com o mesmo <xref:System.ServiceModel.Description.ContractDescription> e <xref:System.ServiceModel.Channels.BindingElement> objetos extensões de importação de política devem ser robustas para esse comportamento.  
  
> [!IMPORTANT]
>  Metadados inválidos ou inadequado podem ser passado para o importador. Certifique-se de que importadores personalizados são robustos em todas as formas de XML.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)  
 [Como: importar asserções de políticas personalizadas](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)  
 [Como: gravar uma extensão para o ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
