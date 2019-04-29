---
title: 'Como: criar um RSS Feed básico'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 5bab8b5a19f33f8dcfcc5a5f5d882309a4b1cc99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781440"
---
# <a name="how-to-create-a-basic-rss-feed"></a>Como: criar um RSS Feed básico
Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um feed de sindicalização. Este tópico discute como criar um serviço de distribuição que expõe uma feed de sindicalização RSS.  
  
### <a name="to-create-a-basic-syndication-service"></a>Para criar um serviço básico de distribuição  
  
1. Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> atributo. Cada operação que é exposta como um feed de sindicalização deve retornar um <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> objeto.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Todas as operações de serviço que se aplicam a <xref:System.ServiceModel.Web.WebGetAttribute> atributos são mapeados para as solicitações HTTP GET. Para mapear sua operação para um método diferente de HTTP, use o <xref:System.ServiceModel.Web.WebInvokeAttribute> em vez disso. Para obter mais informações, confira [Como: Criar um serviço de Web HTTP WCF básico](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2. Implemente o contrato de serviço.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. Criar um <xref:System.ServiceModel.Syndication.SyndicationFeed> do objeto e adicionar um autor, categoria e descrição.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. Criar vários <xref:System.ServiceModel.Syndication.SyndicationItem> objetos.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. Adicionar o <xref:System.ServiceModel.Syndication.SyndicationItem> no feed.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. Retorne o feed.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>Para hospedar um serviço  
  
1. Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. Abra o host do serviço e aguarde até que o usuário pressione ENTER.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Para chamar GetBlog() com um HTTP GET  
  
1. Abra o Internet Explorer, digite a URL a seguir e pressione ENTER: `http://localhost:8000/BlogService/GetBlog`. A URL contém o endereço base do serviço (`http://localhost:8000/BlogService`), o endereço relativo do ponto de extremidade e a operação de serviço para chamar.  
  
### <a name="to-call-getblog-from-code"></a>Para chamar GetBlog() do código  
  
1. Criar um <xref:System.Xml.XmlReader> com o endereço básico e o método que você está chamando.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. Chamar estático <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> método, passando o <xref:System.Xml.XmlReader> você acabou de criar.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     Isso invoca a operação de serviço e preenche um novo <xref:System.ServiceModel.Syndication.SyndicationFeed> com o formatador retornado da operação de serviço.  
  
3. Acesse o objeto de feed.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Exemplo  
 A seguir está a listagem completa de códigos deste exemplo.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Ao compilar o código anterior, fazer referência a ServiceModel. dll e System.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
