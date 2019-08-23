---
title: Importando metadados personalizados para uma extensão do WCF
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 36bc4c9291b60ae5ad6e9964c361ed9e7a7c8317
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963494"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>Importando metadados personalizados para uma extensão do WCF
No Windows Communication Foundation (WCF), a importação de metadados é o processo de gerar uma representação abstrata de um serviço ou de suas partes de componente a partir de seus metadados. Por exemplo, o WCF pode <xref:System.ServiceModel.Description.ServiceEndpoint> importar instâncias <xref:System.ServiceModel.Channels.Binding> , instâncias <xref:System.ServiceModel.Description.ContractDescription> ou instâncias de um documento WSDL para um serviço. Para importar metadados de serviço no WCF, use uma implementação da <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> classe abstrata. Os tipos que derivam <xref:System.ServiceModel.Description.MetadataImporter> da classe implementam o suporte à importação de formatos de metadados que aproveitam a lógica de importação de WS-Policy no WCF.  
  
 Metadados personalizados consistem em elementos XML que os importadores de metadados fornecidos pelo sistema não podem importar. Normalmente, isso inclui extensões WSDL personalizadas e declarações de política personalizadas.  
  
 Esta seção descreve como importar extensões WSDL personalizadas e declarações de política. Ele não se concentra no próprio processo de importação. Para obter mais informações sobre como usar os tipos que exportam e importam metadados independentemente de os metadados serem personalizados ou compatíveis com o sistema, consulte Exportando [e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
## <a name="overview"></a>Visão geral  
 O <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> tipo é a implementação <xref:System.ServiceModel.Description.MetadataImporter> da classe abstrata incluída no WCF. O <xref:System.ServiceModel.Description.WsdlImporter> tipo importa metadados WSDL com políticas anexadas que são agrupadas em <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> um objeto. As declarações de política e as extensões WSDL que os importadores padrão não reconhecem são passadas para qualquer política personalizada registrada e importadores WSDL para importação. Normalmente, importadores são implementados para dar suporte a elementos de associação definidos pelo usuário ou para modificar o contrato importado.  
  
 Esta seção descreve:  
  
1. Como implementar e usar a <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface, que expõe os dados WSDL para importadores personalizados antes da geração de descrições e da geração de código. Você pode usar essa interface para examinar ou modificar os tipos de descrição e a compilação de código executada usando um determinado conjunto de metadados.  
  
2. Como implementar e usar a interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> , que expõe as declarações de política para importadores antes da geração de objetos de descrição. Você pode usar essa interface para examinar ou modificar a associação ou o contrato com base nas políticas baixadas.  
  
 Para obter mais informações sobre como exportar declarações WSDL e de política personalizadas, consulte Exportando [metadados personalizados para uma extensão WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md).  
  
## <a name="importing-custom-wsdl-extensions"></a>Importando extensões WSDL personalizadas  
 Para adicionar suporte para importar extensões WSDL, implemente <xref:System.ServiceModel.Description.IWsdlImportExtension> a interface e, em seguida, adicione <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> sua implementação à propriedade. O <xref:System.ServiceModel.Description.WsdlImporter> também pode carregar implementações <xref:System.ServiceModel.Description.IWsdlImportExtension> da interface registrada em seu arquivo de configuração de aplicativo. Observe que vários importadores WSDL são registrados por padrão e a ordem dos importadores WSDL registrados é significativa.  
  
 Quando o importador WSDL personalizado é carregado e usado pelo <xref:System.ServiceModel.Description.WsdlImporter>, primeiro o <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> método é chamado para habilitar a modificação de metadados antes do processo de importação. Em seguida, os contratos são importados <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> após o qual o método é chamado para habilitar a modificação dos contratos importados dos metadados. Por fim, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> o método é chamado para habilitar a modificação dos pontos de extremidade importados.  
  
 Para obter mais informações, confira [Como: Importe o WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)personalizado.  
  
### <a name="importing-custom-policy-assertions"></a>Importando declarações de política personalizada  
 O <xref:System.ServiceModel.Description.WsdlImporter> tipo e a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tratam automaticamente do processamento de uma variedade de tipos de declaração de política em expressões de política anexadas a documentos WSDL. Essas ferramentas coletam, normalizam e mesclam expressões de política anexadas a associações WSDL e a portas WSDL.  
  
 Para adicionar suporte para importar declarações de política personalizada, implemente <xref:System.ServiceModel.Description.IPolicyImportExtension> a interface e, em seguida, adicione <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> sua implementação à propriedade. O <xref:System.ServiceModel.Description.MetadataImporter> também pode carregar implementações <xref:System.ServiceModel.Description.IPolicyImportExtension> da interface registrada em seu arquivo de configuração de aplicativo. Observe que um número de importadores de política é registrado por padrão e a ordem dos importadores de política registrados é significativa.  
  
 O sistema de metadados chama repetidamente <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> o método em todas as extensões de importação de política registradas para cada combinação de alternativas de política anexadas à mensagem, à operação e aos assuntos da política de ponto de extremidade. Ao importar uma porta WSDL, as políticas anexadas à porta e à associação WSDL correspondente são mescladas antes de chamar as extensões de importação de política. As alternativas de política são disponibilizadas por <xref:System.ServiceModel.Description.PolicyConversionContext> meio <xref:System.ServiceModel.Description.PolicyAssertionCollection> de um como objetos. Cada <xref:System.ServiceModel.Description.PolicyAssertionCollection> um é uma coleção de declarações de política representada <xref:System.Xml.XmlElement> por objetos.  
  
 As <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> propriedades <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> e <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.BindingElement> no <xref:System.ServiceModel.Description.PolicyConversionContext> objeto expõem os objetos e que foram importados do WSDL. Extensões de importação de política processam declarações de política localizando instâncias de um determinado tipo de declaração de política, <xref:System.ServiceModel.Description.ContractDescription> fazendo <xref:System.ServiceModel.Channels.BindingElement> alterações correspondentes aos objetos ou e, em seguida, removendo as declarações de política do correspondente <xref:System.ServiceModel.Description.PolicyAssertionCollection> instância.  
  
 As `wsp:Optional` expressões de política aninhada e atributo não são normalizadas, portanto, as extensões de importação de política devem lidar com essas construções de política. Além disso, as extensões de importação de política podem ser chamadas várias <xref:System.ServiceModel.Description.ContractDescription> vezes <xref:System.ServiceModel.Channels.BindingElement> com os mesmos objetos e, portanto, as extensões de importação de política devem ser robustas para esse comportamento.  
  
> [!IMPORTANT]
> Metadados inválidos ou inadequados podem ser passados para o importador. Certifique-se de que importadores personalizados sejam robustos para todas as formas de XML.  
  
## <a name="see-also"></a>Consulte também

- [Como: Importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [Como: Importar declarações de política personalizada](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [Como: Gravar uma extensão para o ServiceContractGenerator](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
