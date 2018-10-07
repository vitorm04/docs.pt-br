---
title: Como expor um feed como Atom e RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 6b26dabb9ed5c2c7bb2410dc1e844add6a69bdf3
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842717"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Como expor um feed como Atom e RSS
Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um feed de sindicalização. Este tópico discute como criar um serviço de distribuição que expõe um feed usando RSS 2.0 e Atom 1.0 de distribuição. Este serviço expõe um ponto de extremidade que pode retornar qualquer um dos formatos de distribuição. Para simplificar, o serviço usado neste exemplo é auto-hospedado. Em um ambiente de produção um serviço desse tipo deve ser hospedado no IIS ou WAS. Para obter mais informações sobre o WCF diferente opções de hospedagem, consulte [hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Para criar um serviço básico de distribuição  
  
1.  Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> atributo. Cada operação que é exposta como um distribuição de alimentação retorna um <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objeto. Observe os parâmetros para o <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate` Especifica a URL usada para invocar a operação de serviço. A cadeia de caracteres para este parâmetro contém os literais e uma variável entre chaves ({*formato*}). Essa variável corresponde à operação de serviço `format` parâmetro. Para obter mais informações, consulte <xref:System.UriTemplate>. `BodyStyle` afeta como as mensagens que essa operação de serviço envia e recebe são gravadas. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Especifica que os dados enviados de e para essa operação de serviço não são encapsulados por elementos definidos pela infraestrutura XML. Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Use o <xref:System.ServiceModel.ServiceKnownTypeAttribute> para especificar os tipos que são retornados pelas operações de serviço nessa interface.  
  
2.  Implemente o contrato de serviço.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Criar um <xref:System.ServiceModel.Syndication.SyndicationFeed> do objeto e adicionar um autor, categoria e descrição.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Criar vários <xref:System.ServiceModel.Syndication.SyndicationItem> objetos.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Adicionar o <xref:System.ServiceModel.Syndication.SyndicationItem> objetos para o feed.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  Use o parâmetro de formato para retornar o formato solicitado.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Para hospedar o serviço  
  
1.  Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>. O <xref:System.ServiceModel.Web.WebServiceHost> classe adiciona automaticamente um ponto de extremidade no endereço base do serviço, a menos que um for especificado no código ou configuração. Neste exemplo, nenhum ponto de extremidade é especificados para que o ponto de extremidade padrão é exposto.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Abra o host de serviço, carregar o feed do serviço, exibir a transmissão e aguarde até que o usuário pressione ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Para chamar GetBlog com um HTTP GET  
  
1.  Abra o Internet Explorer, digite a URL a seguir e pressione ENTER: `http://localhost:8000/BlogService/GetBlog`.
  
     A URL contém o endereço base do serviço (`http://localhost:8000/BlogService`), o endereço relativo do ponto de extremidade e a operação de serviço para chamar.  
  
### <a name="to-call-getblog-from-code"></a>Para chamar GetBlog() do código  
  
1.  Criar um <xref:System.Xml.XmlReader> com o endereço básico e o método que você está chamando.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Chamar estático <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> método, passando o <xref:System.Xml.XmlReader> você acabou de criar.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Isso invoca a operação de serviço e preenche um novo <xref:System.ServiceModel.Syndication.SyndicationFeed> com o formatador retornado da operação de serviço.  
  
3.  Acesse o objeto de feed.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Exemplo  
 A seguir está a listagem completa de códigos deste exemplo.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Ao compilar o código anterior, fazer referência a ServiceModel. dll e System.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
