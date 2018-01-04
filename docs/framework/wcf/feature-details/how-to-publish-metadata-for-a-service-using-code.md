---
title: "Como publicar metadados utilizando código para um serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 455929144f771128ca070cd02e65c919ce4c741f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Como publicar metadados utilizando código para um serviço
Este é um dos dois tópicos que abordam os metadados de publicação para um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço. Há duas maneiras de especificar como um serviço deve publicar metadados, usando um arquivo de configuração e código. Este tópico mostra como publicar metadados utilizando um código para um serviço.  
  
> [!CAUTION]
>  Este tópico mostra como publicar metadados de maneira insegura. Qualquer cliente pode recuperar os metadados do serviço. Se você precisar de seu serviço para publicar metadados de uma maneira segura. consulte [personalizado proteger metadados de ponto de extremidade](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]metadados de publicação em um arquivo de configuração, consulte [como: publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Metadados de publicação permite que os clientes recuperar os metadados usando uma solicitação GET do WS-transferência ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta. Para certificar-se de que o código estiver trabalhando, você deve criar um serviço WCF básico. Um serviço auto-hospedado básico é fornecido no código a seguir.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Para publicar metadados no código  
  
1.  Dentro do método principal de um aplicativo de console, instanciar uma <xref:System.ServiceModel.ServiceHost> objeto passando o tipo de serviço e o endereço base.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  Criar um bloco try imediatamente abaixo do código para a etapa 1, e captura todas as exceções que ser geradas enquanto o serviço está em execução.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Verifique se o host de serviço já contém um <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, se não estiver, crie um novo <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  O <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contém um <xref:System.ServiceModel.Description.MetadataExporter> propriedade. O <xref:System.ServiceModel.Description.MetadataExporter> contém um <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade. Definir o valor de <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. O <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> propriedade também pode ser definida como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> o exportador de metadados gera informações de política com os metadados que "está em conformidade com o WS-Policy 1.5. Quando definido como <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> o exportador de metadados gera informações de política que está de acordo com WS-Policy 1.2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância para a coleção de comportamentos do host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Adicione o ponto de extremidade de troca de metadados para o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Adicione um ponto de extremidade do aplicativo para o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você. Neste exemplo, porque o serviço possui um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> definida como `true`, o serviço tem metadados de publicação habilitado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pontos de extremidade padrão, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Abrir o host de serviço e aguarde até que as chamadas de entrada. Quando o usuário pressiona ENTER, feche o host de serviço.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Compilar e executar o aplicativo de console.  
  
11. Use o Internet Explorer para navegar até o endereço base do serviço (http://localhost:8001/MetadataSample neste exemplo) e verifique se a publicação de metadados está ligada. Você deve ver uma página da Web exibida dizendo "Serviço simples" na parte superior e imediatamente abaixo "Você criou um serviço." Se não, uma mensagem na parte superior da página resultante é exibida: "a publicação de metadados para este serviço está atualmente desabilitada."  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra a implementação de um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que publica os metadados para o serviço no código.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Consulte também  
 [Como hospedar um serviço do WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Auto-hospedagem](../../../../docs/framework/wcf/samples/self-host.md)  
 [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Usando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Como publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
