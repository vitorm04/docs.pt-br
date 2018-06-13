---
title: Como exportar declarações de política personalizadas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 4182007d32ea857aa333542b4df29da18b8062df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488212"
---
# <a name="how-to-export-custom-policy-assertions"></a>Como exportar declarações de política personalizadas
Declarações de política descrevem os recursos e requisitos de um ponto de extremidade de serviço. Aplicativos de serviço podem usar declarações de política personalizada nos metadados de serviço para comunicar-se o ponto de extremidade, informações de personalização de associação ou o contrato para o aplicativo cliente. Você pode usar o Windows Communication Foundation (WCF) para exportar declarações em expressões de política anexadas em associações de WSDL no ponto de extremidade, operação ou entidades de mensagem, dependendo do modo como os recursos ou os requisitos que você está se comunicando.  
  
 Declarações de política personalizadas são exportadas Implementando o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface em um <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> e inserindo o elemento de associação diretamente para a associação do ponto de extremidade de serviço ou registrando o elemento de associação em seu aplicativo arquivo de configuração. A implementação de exportação de política deve adicionar a declaração de política personalizada como um <xref:System.Xml.XmlElement?displayProperty=nameWithType> instância apropriada <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> no <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passado para o <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> método.  
  
 Além disso, você deve verificar o <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade o <xref:System.ServiceModel.Description.WsdlExporter> classe e exportar expressões de política aninhados e atributos de estrutura de política no namespace correto com base na versão de política especificada.  
  
 Para importar asserções de políticas personalizadas, consulte <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> e [como: importar declarações de política personalizada](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).  
  
### <a name="to-export-custom-policy-assertions"></a>Para exportar declarações de política personalizada  
  
1.  Implementar o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface em um <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. O exemplo de código a seguir mostra a implementação de uma declaração de política personalizada no nível de associação.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  Inserir o elemento de associação para o ponto de extremidade de associação seja programaticamente ou usando um arquivo de configuração do aplicativo. Consulte os procedimentos a seguir.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Para inserir um elemento de associação usando um arquivo de configuração do aplicativo  
  
1.  Implementar <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> para o elemento de associação de declaração de política personalizada.  
  
2.  Adicionar a extensão de elemento de associação para o arquivo de configuração usando o [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) elemento.  
  
3.  Criar uma associação personalizada usando o <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Para inserir um elemento de associação programaticamente  
  
1.  Criar um novo <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> e adicioná-lo para um <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2.  Adicione a associação personalizada da etapa 1. para um novo ponto de extremidade e adicionar esse novo ponto de extremidade de serviço para o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> chamando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.  
  
3.  Abra o <xref:System.ServiceModel.ServiceHost>. O exemplo de código a seguir mostra a criação de uma associação personalizada e a inserção de programação de elementos de associação.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [Como importar declarações de políticas personalizadas](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
