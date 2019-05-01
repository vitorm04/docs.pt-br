---
title: 'Como: publicar metadados utilizando código para um serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 870142724321629d6dbeccd4118b814283901776
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039124"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Como: publicar metadados utilizando código para um serviço
Esse é um dos dois tópicos que discutem os metadados de publicação para um serviço do Windows Communication Foundation (WCF). Há duas maneiras para especificar como um serviço deve publicar metadados, usando um arquivo de configuração e código. Este tópico mostra como publicar metadados para um serviço usando um código.  
  
> [!CAUTION]
>  Este tópico mostra como publicar metadados de maneira não segura. Qualquer cliente pode recuperar os metadados do serviço. Se você precisar de seu serviço para publicar os metadados de uma maneira segura. ver [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Para obter mais informações sobre metadados de publicação em um arquivo de configuração, consulte [como: Publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Metadados de publicação permite que os clientes recuperar os metadados usando uma solicitação GET do WS-Transfer ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta. Para certificar-se de que o código está funcionando você deve criar um serviço WCF básico. Um serviço auto-hospedado básico é fornecido no código a seguir.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Para publicar os metadados no código  
  
1. Dentro do método principal de um aplicativo de console, instanciar um <xref:System.ServiceModel.ServiceHost> objeto, passando o tipo de serviço e o endereço básico.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. Criar um bloco try, imediatamente abaixo do código para a etapa 1, e captura qualquer exceção que é gerada enquanto o serviço está em execução.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Verifique se o host de serviço já contém um <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, se não estiver, crie um novo <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. O <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contém um <xref:System.ServiceModel.Description.MetadataExporter> propriedade. O <xref:System.ServiceModel.Description.MetadataExporter> contém um <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade. Definir o valor de <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade para <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. O <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade também pode ser definida como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> o exportador de metadados gera informações de política com os metadados que "está em conformidade com WS-Policy 1.5. Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> o exportador de metadados gera informações de política que está em conformidade com WS-Policy 1.2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. Adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância à coleção de comportamentos do host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Adicione o ponto de extremidade de troca de metadados para o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Adicione um ponto de extremidade do aplicativo para o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você. Neste exemplo, porque o serviço tem um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> definido como `true`, o serviço tem metadados de publicação habilitados. Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificado](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Abra o host de serviço e aguarde até que as chamadas de entrada. Quando o usuário pressiona ENTER, feche o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Compile e execute o aplicativo de console.  
  
11. Usar o Internet Explorer para navegar até o endereço base do serviço (http://localhost:8001/MetadataSample neste exemplo) e verifique se a publicação de metadados está ligada. Você deve ver uma página da Web exibida informando que "Simple Service" na parte superior e imediatamente abaixo de "Você ter criado um serviço". Caso contrário, exibe uma mensagem na parte superior da página resultante: "Publicação de metadados para este serviço está desabilitada no momento."  
  
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
