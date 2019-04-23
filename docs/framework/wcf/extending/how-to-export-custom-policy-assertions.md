---
title: 'Como: exportar declarações de política personalizadas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: b3d3afdd1e3fba2a77186d1cd644d723c445600c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306216"
---
# <a name="how-to-export-custom-policy-assertions"></a>Como: exportar declarações de política personalizadas
Declarações de política descrevem os recursos e os requisitos de um ponto de extremidade de serviço. Aplicativos de serviço podem usar declarações de política personalizadas nos metadados de serviço para se comunicar o ponto de extremidade, contrato ou associação de informações de personalização para o aplicativo cliente. Você pode usar o Windows Communication Foundation (WCF) para exportar declarações em expressões de política anexadas em associações WSDL no ponto de extremidade, operação ou entidades de mensagem, dependendo dos recursos ou requisitos que você está se comunicando.  
  
 Declarações de política personalizadas são exportadas, Implementando a <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> da interface em um <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> e inserindo o elemento de associação diretamente para a associação do ponto de extremidade de serviço ou registrando-se o elemento de associação em seu aplicativo arquivo de configuração. Sua implementação de exportação de política deve adicionar sua declaração de política personalizada como um <xref:System.Xml.XmlElement?displayProperty=nameWithType> instância apropriado <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passado para o <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> método.  
  
 Além disso, você deve verificar a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade do <xref:System.ServiceModel.Description.WsdlExporter> de classe e exportar expressões de política aninhados e atributos da estrutura de política no namespace correto com base na versão de política especificada.  
  
 Para importar asserções de política personalizada, consulte <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> e [como: Importar asserções de política personalizada](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Para exportar as declarações de política personalizada  
  
1. Implemente a <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> da interface em um <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. O exemplo de código a seguir mostra a implementação de uma asserção de política personalizada no nível da associação.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Inserir o elemento de associação para o ponto de extremidade de associação seja programaticamente ou usando um arquivo de configuração do aplicativo. Consulte os procedimentos a seguir.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Para inserir um elemento de associação usando um arquivo de configuração de aplicativo  
  
1. Implemente <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> para seu elemento de associação de asserção de política personalizada.  
  
2. Adicionar a extensão de elemento de associação para o arquivo de configuração usando o [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) elemento.  
  
3. Criar uma ligação personalizada usando o <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Para inserir um elemento de associação de forma programática  
  
1. Criar um novo <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> e adicione-o a um <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2. Adicione a associação personalizada da etapa 1. para um novo ponto de extremidade e adicionar esse novo ponto de extremidade de serviço para o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> chamando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.  
  
3. Abra o <xref:System.ServiceModel.ServiceHost>. O exemplo de código a seguir mostra a criação de uma ligação personalizada e a inserção de programação de elementos de associação.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Como: Importar asserções de política personalizada](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
