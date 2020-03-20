---
title: Como importar asserções de políticas personalizadas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: ed8aae30875e3b17f65be5857c7d93af98db9b3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185561"
---
# <a name="how-to-import-custom-policy-assertions"></a>Como importar asserções de políticas personalizadas
As afirmações de políticas descrevem os recursos e requisitos de um ponto final de serviço.  Os aplicativos clientes podem usar afirmações de políticas em metadados de serviço para configurar a vinculação do cliente ou personalizar o contrato de serviço para um ponto final de serviço.  
  
 As afirmações de diretiva personalizadas <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> são importadas implementando a interface e passando esse objeto para o sistema de metadados ou registrando o tipo de implementação no arquivo de configuração do aplicativo.  As implementações <xref:System.ServiceModel.Description.IPolicyImportExtension> da interface devem fornecer um construtor sem parâmetros.  
  
### <a name="to-import-custom-policy-assertions"></a>Para importar afirmações de políticas personalizadas  
  
1. Implemente <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> a interface em uma classe. Veja os seguintes procedimentos.  
  
2. Insira o importador de políticas personalizadas por:  
  
3. Usando um arquivo de configuração. Veja os seguintes procedimentos.  
  
4. Usando um arquivo de configuração com [serviceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Veja os seguintes procedimentos.  
  
5. Inserindo programáticamente o importador de políticas. Veja os seguintes procedimentos.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Para implementar a interface System.ServiceModel.Description.IPolicyImportExtension em qualquer classe  
  
1. No <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> método, para cada assunto de política que você está interessado, encontre as afirmações de política que você deseja importar <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> chamando o método apropriado (dependendo do escopo da afirmação que você deseja) sobre o objeto passado para o método. O exemplo de código a <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> seguir mostra como usar o método para localizar a afirmação da política personalizada e removê-la da coleção em uma etapa. Se você usar o método remover para localizar e remover a afirmação, você não precisa executar a etapa 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Processe as afirmações políticas. Observe que o sistema de políticas não `wsp:optional`normaliza políticas aninhadas e . Você deve processar essas construções em sua implementação de extensão de importação de políticas.  
  
3. Realize a personalização da vinculação ou contrato que suporte o recurso ou requisito especificado pela afirmação da diretiva. Normalmente, as afirmações indicam que uma vinculação requer uma configuração específica ou um elemento de vinculação específico. Faça essas modificações acessando a <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> propriedade. Outras afirmações exigem que você modifique o contrato.  Você pode acessar e modificar <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> o contrato usando o imóvel.  Observe que o seu importador de apólices pode ser chamado várias vezes para o mesmo contrato e vinculação, mas alternativas de política diferentes se a importação de uma alternativa de política falhar. Seu código deve ser resistente a esse comportamento.  
  
4. Remova a afirmação da política personalizada da coleção de afirmações. Se você não remover a afirmação, a Windows Communication Foundation (WCF) assumirá que a importação de políticas não foi bem sucedida e não importa a vinculação associada. Se você <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> usou o método para localizar a afirmação da política personalizada e removê-la da coleção em uma etapa, você não precisa executar essa etapa.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Para inserir o importador de políticas personalizadas no sistema de metadados usando um arquivo de configuração  
  
1. Adicione o tipo `<extensions>` de importador ao elemento dentro da [ \<políticaImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) elemento no arquivo de configuração do cliente.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
  
2. Na aplicação do cliente, use o <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> para resolver os metadados e o importador é invocado automaticamente.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Para inserir o importador de políticas personalizadas no sistema de metadados usando Svcutil.exe  
  
1. Adicione o tipo `<extensions>` de importador ao elemento dentro da [ \<políticaImportadores>](../../configure-apps/file-schema/wcf/policyimporters.md) elemento no arquivo de configuração Svcutil.exe.config. Você também pode apontar Svcutil.exe para carregar tipos de importador `/svcutilConfig` de políticas registrados em um arquivo de configuração diferente usando a opção.  
  
2. Use [serviceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para importar os metadados e o importador é invocado automaticamente.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Para inserir o importador de políticas personalizadas no sistema de metadados de forma programática  
  
1. Adicione o importador <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> à propriedade (por exemplo, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>se você estiver usando o ) antes de importar os metadados.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Estendendo o sistema de metadados](extending-the-metadata-system.md)
