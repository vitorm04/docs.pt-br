---
title: 'Como: publicar metadados utilizando código para um serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 5f60bcdb02f61d39711115b07ba989229e39c28c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929140"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Como: publicar metadados utilizando código para um serviço
Este é um dos dois tópicos de instruções que abordam a publicação de metadados para um serviço Windows Communication Foundation (WCF). Há duas maneiras de especificar como um serviço deve publicar metadados, usando um arquivo de configuração e usando código. Este tópico mostra como publicar metadados para um serviço usando um código.  
  
> [!CAUTION]
>  Este tópico mostra como publicar metadados de maneira não segura. Qualquer cliente pode recuperar os metadados do serviço. Se você precisar que seu serviço publique metadados de maneira segura. consulte [ponto de extremidade de metadados seguro personalizado](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Para obter mais informações sobre como publicar metadados em um arquivo de [configuração, consulte Como: Publicar metadados para um serviço usando um arquivo](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)de configuração. A publicação de metadados permite que os clientes recuperem os metadados usando uma solicitação WS-Transfer Get ou uma solicitação HTTP `?wsdl` /Get usando a cadeia de caracteres de consulta. Para ter certeza de que o código está funcionando, você deve criar um serviço WCF básico. Um serviço auto-hospedado básico é fornecido no código a seguir.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Para publicar metadados no código  
  
1. Dentro do método principal de um aplicativo de console, crie <xref:System.ServiceModel.ServiceHost> uma instância de um objeto passando o tipo de serviço e o endereço base.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. Crie um bloco try imediatamente abaixo do código da etapa 1. isso captura todas as exceções que são geradas durante a execução do serviço.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Verifique se o host de serviço já contém um <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, se não, criar uma nova <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. O <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contém uma <xref:System.ServiceModel.Description.MetadataExporter> propriedade. O <xref:System.ServiceModel.Description.MetadataExporter> contém uma <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade. Defina o valor da <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Propriedade como. <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> A <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Propriedade também pode ser definida como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> o exportador de metadados gera informações de política com os metadados que estão em conformidade com WS-Policy 1,5. Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> o exportador de metadados gera informações de política que estão em conformidade com WS-Policy 1,2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. Adicione a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância à coleção de comportamentos do host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Adicione o ponto de extremidade de troca de metadados ao host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Adicione um ponto de extremidade de aplicativo ao host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você. Neste exemplo, como o serviço tem um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> definido como `true`, o serviço tem metadados de publicação habilitados. Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Abra o host de serviço e aguarde as chamadas de entrada. Quando o usuário pressionar ENTER, feche o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Compile e execute o aplicativo de console.  
  
11. Use o Internet Explorer para navegar até o endereço base do serviço (http://localhost:8001/MetadataSample neste exemplo) e verificar se a publicação de metadados está ativada. Você deve ver uma página da Web exibida dizendo "serviço simples" na parte superior e imediatamente abaixo de "você criou um serviço". Caso contrário, uma mensagem na parte superior da página resultante exibe: "A publicação de metadados para este serviço está desabilitada no momento."  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra a implementação de um serviço WCF básico que publica metadados para o serviço no código.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Hospedar um serviço WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Auto-hospedagem](../../../../docs/framework/wcf/samples/self-host.md)
- [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Usando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Como: Publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
