---
title: 'Como: exportar declarações de política personalizadas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795672"
---
# <a name="how-to-export-custom-policy-assertions"></a>Como: exportar declarações de política personalizadas
As declarações de política descrevem os recursos e os requisitos de um ponto de extremidade de serviço. Os aplicativos de serviço podem usar declarações de política personalizadas em metadados de serviço para comunicar ponto de extremidade, associação ou informações de personalização de contrato ao aplicativo cliente. Você pode usar Windows Communication Foundation (WCF) para exportar declarações em expressões de política anexadas em associações WSDL no ponto de extremidade, operação ou assuntos de mensagem, dependendo dos recursos ou requisitos que você está comunicando.  
  
 As declarações de política personalizada são exportadas <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementando a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> interface em um e inserindo o elemento de associação diretamente na associação do ponto de extremidade de serviço ou registrando o elemento de associação em seu aplicativo arquivo de configuração. Sua implementação de exportação de política deve adicionar sua declaração de política <xref:System.Xml.XmlElement?displayProperty=nameWithType> personalizada como uma instância <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> para a <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> apropriada no passado <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> para o método.  
  
 Além disso, você deve verificar <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> a propriedade <xref:System.ServiceModel.Description.WsdlExporter> da classe e exportar as expressões de política aninhada e os atributos da estrutura de política no namespace correto com base na versão de política especificada.  
  
 Para importar declarações de política personalizada, consulte <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> e [como: Importar declarações](how-to-import-custom-policy-assertions.md)de política personalizada.  
  
### <a name="to-export-custom-policy-assertions"></a>Para exportar declarações de política personalizada  
  
1. Implemente <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> a interface em <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>um. O exemplo de código a seguir mostra a implementação de uma declaração de política personalizada no nível de associação.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Insira o elemento de associação na associação de ponto de extremidade de forma programática ou usando um arquivo de configuração de aplicativo. Consulte os procedimentos a seguir.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Para inserir um elemento de associação usando um arquivo de configuração de aplicativo  
  
1. Implemente <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> para seu elemento de associação de declaração de política personalizada.  
  
2. Adicione a extensão do elemento de associação ao arquivo de configuração usando o elemento de [ \<> bindingElementExtensions](../../configure-apps/file-schema/wcf/bindingelementextensions.md) .  
  
3. Crie uma associação personalizada usando o <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Para inserir um elemento de associação programaticamente  
  
1. Crie um novo <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> e adicione-o a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>um.  
  
2. Adicione a associação personalizada da etapa 1. para um novo ponto de extremidade e adicione esse novo ponto de <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> extremidade de serviço <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> ao chamando o método.  
  
3. Abra o <xref:System.ServiceModel.ServiceHost>. O exemplo de código a seguir mostra a criação de uma associação personalizada e a inserção programática de elementos de associação.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Como: Importar declarações de política personalizada](how-to-import-custom-policy-assertions.md)
