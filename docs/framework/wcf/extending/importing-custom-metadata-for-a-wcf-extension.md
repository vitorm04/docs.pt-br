---
title: Importando metadados personalizados para uma extensão do WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 830829be98202c97a9fc2b34e31da25967292efb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339964"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Importando metadados personalizados para uma extensão do WCF
No Windows Communication Foundation (WCF), a importação de metadados é o processo de geração de uma representação abstrata de um serviço ou seus componentes de seus metadados. Por exemplo, o WCF pode importar <xref:System.ServiceModel.Description.ServiceEndpoint> instâncias, <xref:System.ServiceModel.Channels.Binding> instâncias ou <xref:System.ServiceModel.Description.ContractDescription> instâncias de uma WSDL de documento para um serviço. Para importar metadados de serviço do WCF, use uma implementação do <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> classe abstrata. Tipos que derivam de <xref:System.ServiceModel.Description.MetadataImporter> classe implementar o suporte para formatos de metadados de importação que aproveitam o WS-Policy importar lógica no WCF.  
  
 Metadados personalizados consistem em elementos XML que não é possível importar aos importadores de metadados fornecidos pelo sistema. Normalmente, isso inclui as extensões WSDL e declarações de política personalizada.  
  
 Esta seção descreve como importar as extensões WSDL e declarações de política. Ele não tem como foco sobre o processo de importação. Para obter mais informações sobre como usar os tipos de exportação e importação de metadados, independentemente se os metadados são personalizadas ou suporte para o sistema, consulte [exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Visão geral  
 O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação do <xref:System.ServiceModel.Description.MetadataImporter> incluído com o WCF de classe abstrata. O <xref:System.ServiceModel.Description.WsdlImporter> tipo importa os metadados WSDL com políticas anexados que estão agrupados em um <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objeto. Declarações de política e as extensões WSDL que não reconhecem os importadores de padrão são passadas com todos os importadores WSDL e política personalizada registrada para a importação. Normalmente, a importadores são implementados para dar suporte a elementos de associação definidas pelo usuário ou para modificar o contrato importado.  
  
 Esta seção descreve:  
  
1. Como implementar e usar o <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface, que expõe os dados WSDL para importadores personalizados antes da geração de descrições e a geração de código. Você pode usar essa interface para examinar ou modificar os tipos de descrição e a compilação de código executada usando um determinado conjunto de metadados.  
  
2. Como implementar e usar o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface, que expõe declarações de política para importadores antes da geração de objetos de descrição. Você pode usar essa interface para examinar ou modificar a associação ou contrato com base nas políticas de baixado.  
  
 Para obter mais informações sobre como exportar o WSDL personalizado e declarações de política, consulte [exportando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Importar extensões WSDL personalizado  
 Para adicionar suporte para a importação de extensões WSDL, implementar o <xref:System.ServiceModel.Description.IWsdlImportExtension> da interface e, em seguida, adicione sua implementação para o <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> propriedade. O <xref:System.ServiceModel.Description.WsdlImporter> também pode carregar a implementações do <xref:System.ServiceModel.Description.IWsdlImportExtension> interface registrada no arquivo de configuração do aplicativo. Observe que um número de importadores WSDL é registrado por padrão e a ordem dos importadores WSDL registrados é significativa.  
  
 Quando o importador WSDL personalizado é carregado e usado pelas <xref:System.ServiceModel.Description.WsdlImporter>, primeiro o <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> método é chamado para habilitar a modificação de metadados antes do processo de importação. Em seguida, os contratos são importados após o qual o <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> método é chamado para habilitar a modificação dos contratos importados dos metadados. Por fim, o <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> método é chamado para habilitar a modificação dos pontos de extremidade importados.  
  
 Para obter mais informações, confira [Como: Importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md).  
  
### <a name="importing-custom-policy-assertions"></a>Importar asserções de política personalizada  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo e o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tratam automaticamente o processamento de uma variedade de tipos de declaração de política em expressões de política anexadas a documentos WSDL. Essas ferramentas coletam, normalizam e anexadas a associações de WSDL e portas WSDL de expressões de política de mesclagem.  
  
 Para adicionar suporte para importar asserções de política personalizada, implementar o <xref:System.ServiceModel.Description.IPolicyImportExtension> da interface e, em seguida, adicione sua implementação para o <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> propriedade. O <xref:System.ServiceModel.Description.MetadataImporter> também pode carregar a implementações do <xref:System.ServiceModel.Description.IPolicyImportExtension> interface registrada no arquivo de configuração do aplicativo. Observe que um número de importadores de políticas é registrado por padrão e a ordem dos importadores de políticas registrado é significativa.  
  
 O sistema de metadados chama repetidamente o <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> método em toda a diretiva registrado importar extensões para cada combinação de alternativas de política anexada para as entidades de política de mensagem, a operação e o ponto de extremidade. Ao importar uma porta WSDL, políticas anexadas para a porta e a associação WSDL correspondente são mescladas antes de chamar as extensões de importação de política. As alternativas de política são disponibilizadas por meio de um <xref:System.ServiceModel.Description.PolicyConversionContext> como <xref:System.ServiceModel.Description.PolicyAssertionCollection> objetos. Cada <xref:System.ServiceModel.Description.PolicyAssertionCollection> é uma coleção de declarações de política representado por <xref:System.Xml.XmlElement> objetos.  
  
 O <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> e <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> propriedades na <xref:System.ServiceModel.Description.PolicyConversionContext> objeto expõem as <xref:System.ServiceModel.Description.ContractDescription> e <xref:System.ServiceModel.Channels.BindingElement> objetos que foram importados do WSDL. Extensões de importação de política de processam as declarações de política, localizando instâncias de um tipo de declaração de política específica, tornando as alterações correspondentes a <xref:System.ServiceModel.Description.ContractDescription> ou <xref:System.ServiceModel.Channels.BindingElement> objetos e, em seguida, removendo as declarações de política do correspondente <xref:System.ServiceModel.Description.PolicyAssertionCollection> instância.  
  
 O `wsp:Optional` atributo e expressões de política aninhada não são normalizadas, portanto, as extensões de importação de política devem tratar essas construções de política. Além disso, as extensões de importação de política podem ser chamadas várias vezes com o mesmo <xref:System.ServiceModel.Description.ContractDescription> e <xref:System.ServiceModel.Channels.BindingElement> objetos, portanto, as extensões de importação de política devem ser robustas para esse comportamento.  
  
> [!IMPORTANT]
>  Metadados inválido ou incorreto podem ser passado para o importador. Certifique-se de que importadores personalizados são robustos em todas as formas de XML.  
  
## <a name="see-also"></a>Consulte também

- [Como: Importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Como: Importar asserções de política personalizada](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Como: Escrever uma extensão para o ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
