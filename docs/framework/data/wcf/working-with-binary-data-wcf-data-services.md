---
title: "Trabalhando com dados binários (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e02a98a327947e32acd42ccf79d922f5dff6fb6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-binary-data-wcf-data-services"></a>Trabalhando com dados binários (WCF Data Services)
O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente permite recuperar e atualizar dados binários de uma [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed em uma das seguintes maneiras:  
  
-   Como uma propriedade de tipo primitivo de uma entidade. Esse é o método recomendado para trabalhar com objetos de dados binários pequenos que podem ser facilmente carregados na memória. Nesse caso, a propriedade binária é uma propriedade de entidade exposta pelo modelo de dados, e o serviço de dados serializa os dados binários como XML com codificação binária de Base 64 na mensagem de resposta.  
  
-   Como um fluxo de recursos binários separado. Esse é o método recomendado para acessar e alterar dados BLOB (objeto binário grande) que podem representar uma fotografia, um vídeo ou qualquer outro tipo de dados codificados binários.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]implementa o streaming de dados binários usando HTTP, conforme definido no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Este mecanismo, dados binários são tratados como um recurso de mídia que é separado do mas relacionados a uma entidade, que é chamada de uma entrada de link de mídia. Para obter mais informações, consulte [provedor Streaming](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Para obter um exemplo passo a passo de como criar um [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] aplicativo cliente que baixa os arquivos de imagem binária de um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] serviço que armazena fotos, consulte a postagem [dados Services Streaming provedor série-parte 2: Acessando uma mídia Fluxo de recursos do cliente](http://go.microsoft.com/fwlink/?LinkId=201637). Para baixar o código de exemplo para o serviço de dados do fluxo foto em destaque na postagem do blog, consulte o [Streaming exemplo de serviço de dados de foto](http://go.microsoft.com/fwlink/?LinkId=198988) na Galeria de códigos do MSDN.  
  
## <a name="entity-metadata"></a>Metadados de entidade  
 Uma entidade que tenha um fluxo de recursos de mídia relacionado é indicada nos metadados do serviço de dados pelo atributo `HasStream` aplicado a um tipo de entidade que é a entrada do link da mídia. No exemplo a seguir, o `PhotoInfo` entidade é uma media link entry que tem um recurso de mídia relacionada, indicado pelo `HasStream` atributo.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Os outros exemplos deste tópico mostram como acessar e alterar o fluxo de recursos de mídia. Para obter um exemplo completo de como consumir um fluxo de recursos de mídia em um aplicativo de cliente do .NET Framework usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente, consulte a postagem [acessar um fluxo de recursos de mídia do cliente](http://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>Acessando o fluxo de recursos binários  
 A biblioteca de cliente do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] fornece métodos para acessar fluxos de recursos binários de um serviço de dados baseado no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Ao baixar um recurso de mídia, você pode usar o URI do recurso de mídia ou obter um fluxo binário que contém os dados próprios do recurso de mídia. Você também pode carregar dados dos recursos de mídia como um fluxo binário.  
  
> [!TIP]
>  Para obter um exemplo passo a passo de como criar um [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] aplicativo cliente que baixa os arquivos de imagem binária de um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] serviço que armazena fotos, consulte a postagem [dados Services Streaming provedor série-parte 2: Acessando uma mídia Fluxo de recursos do cliente](http://go.microsoft.com/fwlink/?LinkId=201637). Para baixar o código de exemplo para o serviço de dados do fluxo foto em destaque na postagem do blog, consulte o [Streaming exemplo de serviço de dados de foto](http://go.microsoft.com/fwlink/?LinkId=198988) na Galeria de códigos do MSDN.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Obtendo o URI do fluxo binário  
 Para recuperar determinados tipos de recursos de mídia, como imagens e outros arquivos de mídia, geralmente é mais fácil usar o URI do recurso de mídia em seu aplicativo do que manipular o próprio fluxo de dados binários. Para obter o URI de um fluxo de recursos associado a uma determinada entrada de link de mídia, você deve chamar o método <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> na instância de <xref:System.Data.Services.Client.DataServiceContext> que está controlando a entidade. O exemplo a seguir mostra como chamar o método <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> para obter o URI de um fluxo de recursos de mídia que é usado para criar uma nova imagem no cliente:  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Baixando o fluxo de recursos binários  
 Para recuperar um fluxo de recursos binários, você deve chamar o método <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> na instância de <xref:System.Data.Services.Client.DataServiceContext> que está controlando a entrada de link de mídia. Esse método envia uma solicitação ao serviço de dados que retorna um objeto <xref:System.Data.Services.Client.DataServiceStreamResponse>, que tem uma referência ao fluxo que contém o recurso. Use esse método quando o aplicativo exigir o recurso binário como um <xref:System.IO.Stream>. O exemplo a seguir mostra como chamar o método <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> para recuperar um fluxo que é usado para criar uma nova imagem no cliente:  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  O cabeçalho do comprimento do conteúdo na mensagem de resposta que contém o vapor binário não é definido pelo serviço de dados. Esse valor pode não refletir o comprimento real do fluxo de dados binários.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Carregando um recurso de mídia como um fluxo  
 Para inserir ou atualizar um recurso de mídia, chame o método <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> na instância de <xref:System.Data.Services.Client.DataServiceContext> que está controlando a entidade. Esse método envia uma solicitação para o serviço de dados que contém a leitura dos recursos de mídia do fluxo fornecido. O exemplo a seguir mostra como chamar o método <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> para enviar uma imagem ao serviço de dados:  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 Neste exemplo, o método <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> é chamado fornecendo um valor de `true` para o parâmetro `closeStream`. Isso garante que o <xref:System.Data.Services.Client.DataServiceContext> feche o fluxo depois que os dados binários forem carregados no serviço de dados.  
  
> [!NOTE]
>  Quando você chama o <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, o fluxo não é enviado ao serviço de dados até que <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> seja chamado.  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)  
 [Associando dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
