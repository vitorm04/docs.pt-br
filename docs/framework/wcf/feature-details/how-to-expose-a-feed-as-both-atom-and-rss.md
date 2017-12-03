---
title: Como expor um feed como Atom e RSS
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
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dad8fe137cfc495d1edc6936d13830861e1654e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Como expor um feed como Atom e RSS
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]permite que você crie um serviço que expõe um feed de distribuição. Este tópico discute como criar um serviço de distribuição que expõe um feed usando RSS 2.0 e Atom 1.0 de distribuição. Esse serviço expõe um ponto de extremidade que pode retornar qualquer formato de distribuição. Para simplificar o serviço usado neste exemplo é auto-hospedado. Em um ambiente de produção um serviço desse tipo deve ser hospedado em IIS ou do WAS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]os diferentes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opções de hospedagem, consulte [hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Para criar um serviço básico de distribuição  
  
1.  Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> atributo. Cada operação que é exposta como um distribuição de alimentação retorna um <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objeto. Observe os parâmetros para o <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate`Especifica a URL usada para invocar esta operação de serviço. A cadeia de caracteres para este parâmetro contém literais e uma variável entre chaves ({*formato*}). Essa variável corresponde à operação de serviço `format` parâmetro. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.UriTemplate>. `BodyStyle`afeta como as mensagens que esta operação de serviço envia e recebe são gravadas. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Especifica que os dados enviados de e para esta operação de serviço não são encapsulados por elementos XML definido de infraestrutura. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Use o <xref:System.ServiceModel.ServiceKnownTypeAttribute> para especificar os tipos que são retornados pelas operações de serviço nesta interface.  
  
2.  Implemente o contrato de serviço.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Criar um <xref:System.ServiceModel.Syndication.SyndicationFeed> do objeto e adicionar um autor, categoria e descrição.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Criar diversos <xref:System.ServiceModel.Syndication.SyndicationItem> objetos.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Adicionar o <xref:System.ServiceModel.Syndication.SyndicationItem> objetos para o feed.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  Use o parâmetro de formato para retornar o formato solicitado.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Para hospedar o serviço  
  
1.  Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>. O <xref:System.ServiceModel.Web.WebServiceHost> classe adiciona automaticamente um ponto de extremidade no endereço base do serviço, a menos que é especificada na configuração ou código. Neste exemplo, nenhum ponto de extremidade é especificados para que o ponto de extremidade padrão é exposto.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Abrir o host de serviço, carregar o feed do serviço, exibir o feed e aguarde até que o usuário pressione ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Para chamar GetBlog com um HTTP GET  
  
1.  Abra o Internet Explorer, digite a URL a seguir e pressione ENTER. BlogService/http://localhost:8000/GetBlog  
  
     A URL contém o endereço base do serviço (http://localhost:8000/BlogService), o endereço relativo do ponto de extremidade e chamar a operação de serviço.  
  
### <a name="to-call-getblog-from-code"></a>Para chamar GetBlog() do código  
  
1.  Criar um <xref:System.Xml.XmlReader> com o endereço base e o método de chamada.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Chamar estático <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> método, passando o <xref:System.Xml.XmlReader> você acabou de criar.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Isso chama a operação de serviço e preenche um novo <xref:System.ServiceModel.Syndication.SyndicationFeed> com o formatador retornado da operação de serviço.  
  
3.  Acesse o objeto de feed.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Exemplo  
 A seguir está a listagem completa de códigos deste exemplo.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Ao compilar o código anterior, fazer referência a System.ServiceModel.dll e System.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
