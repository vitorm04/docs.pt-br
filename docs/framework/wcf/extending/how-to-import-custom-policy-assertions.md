---
title: 'Como: importar declarações de política personalizadas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: 64e639e5fd6200b525ef6face56f7df2e804d7ae
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320672"
---
# <a name="how-to-import-custom-policy-assertions"></a>Como: importar declarações de política personalizadas
Declarações de política descrevem os recursos e os requisitos de um ponto de extremidade de serviço.  Aplicativos cliente podem usar as declarações de política nos metadados de serviço para configurar a associação de cliente ou para personalizar o contrato de serviço para um ponto de extremidade de serviço.  
  
 Declarações de política personalizadas são importadas, Implementando o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface e passando esse objeto para o sistema de metadados ou Registrando a implementação do tipo em seu arquivo de configuração do aplicativo.  Implementações do <xref:System.ServiceModel.Description.IPolicyImportExtension> interface deve fornecer um construtor padrão.  
  
### <a name="to-import-custom-policy-assertions"></a>Para importar asserções de política personalizada  
  
1. Implementar o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface em uma classe. Consulte os procedimentos a seguir.  
  
2. Inserir o importador de política personalizada ou por:  
  
3. Usando um arquivo de configuração. Consulte os procedimentos a seguir.  
  
4. Usando um arquivo de configuração com [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Consulte os procedimentos a seguir.  
  
5. Programaticamente, inserindo o importador de política. Consulte os procedimentos a seguir.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Para implementar a interface System.ServiceModel.Description.IPolicyImportExtension em qualquer classe  
  
1. No <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> método, para cada entidade de política que você está interessado, encontrar as declarações de política que você deseja importar, chamando o método apropriado (dependendo do escopo da asserção que você deseja) no <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> objeto passado para o método. O exemplo de código a seguir mostra como usar o <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> método para localizar a declaração de política personalizada e removê-lo da coleção em uma única etapa. Se você usar o método remove para localizar e remover a asserção, você não precisa executar a etapa 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Processe as declarações de política. Observe que o sistema de política não normalizará aninhados políticas e `wsp:optional`. Você deve processar essas construções em sua implementação de extensão de importação de política.  
  
3. Realize a personalização para a associação ou o contrato que ofereça suporte a recurso ou requisitos especificados, a declaração de política. Normalmente, asserções indicam que uma associação requer uma configuração específica ou um elemento de associação específica. Faça essas modificações, acessando o <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> propriedade. Outras declarações exigem que você modifique o contrato.  Você pode acessar e modificar o contrato usando o <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> propriedade.  Observe que o importador de política pode obter chamado várias vezes para a mesma associação e contrato, mas falha de alternativas de políticas diferentes se estiver importando uma alternativa de política. Seu código deve ser resiliente em relação a esse comportamento.  
  
4. Remova a declaração de política personalizada da coleção de asserção. Se você não remover a Windows Communication Foundation (WCF) pressupõe que a importação de política não foi bem-sucedida e não importa a ligação associada de asserção. Se você tiver usado o <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> método para localizar a declaração de política personalizada e removê-lo da coleção em uma única etapa, você não precisa executar essa etapa.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Para inserir o importador de política personalizada em metadados usando um arquivo de configuração do sistema  
  
1. Adicione o tipo de importador para o `<extensions>` elemento dentro de [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) elemento no arquivo de configuração do cliente.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2. No aplicativo cliente, use o <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> para resolver os metadados e o importador é invocado automaticamente.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Para inserir o importador de política personalizada no sistema de metadados usando Svcutil.exe  
  
1. Adicione o tipo de importador para o `<extensions>` elemento dentro de [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) elemento no arquivo de configuração de svcutil. Você também pode Svcutil.exe ponto para carregar tipos de Importador de política registrados em um arquivo de configuração diferente usando o `/svcutilConfig` opção.  
  
2. Use [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) importar os metadados e o importador é invocado automaticamente.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Para inserir o importador de política personalizada para o sistema de metadados de forma programática  
  
1. Adicionar o importador para o <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> propriedade (por exemplo, se você estiver usando o <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) antes de importar os metadados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
