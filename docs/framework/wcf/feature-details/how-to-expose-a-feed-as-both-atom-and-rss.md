---
title: Como expor um feed como Atom e RSS
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 14059ebc3efe57a38a093faed9cfbd254c372920
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="a3c6a-102">Como expor um feed como Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="a3c6a-102">How to: Expose a Feed as Both Atom and RSS</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a3c6a-103"> permite que você crie um serviço que expõe um feed de distribuição.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="a3c6a-104">Este tópico discute como criar um serviço de distribuição que expõe um feed usando RSS 2.0 e Atom 1.0 de distribuição.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="a3c6a-105">Esse serviço expõe um ponto de extremidade que pode retornar qualquer formato de distribuição.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="a3c6a-106">Para simplificar o serviço usado neste exemplo é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="a3c6a-107">Em um ambiente de produção um serviço desse tipo deve ser hospedado em IIS ou do WAS.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="a3c6a-108">Para obter mais informações sobre os diferentes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opções de hospedagem, consulte [hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="a3c6a-108">For more information about the different [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="a3c6a-109">Para criar um serviço básico de distribuição</span><span class="sxs-lookup"><span data-stu-id="a3c6a-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="a3c6a-110">Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="a3c6a-111">Cada operação que é exposta como um distribuição de alimentação retorna um <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objeto.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="a3c6a-112">Observe os parâmetros para o <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="a3c6a-113">`UriTemplate` Especifica a URL usada para invocar esta operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="a3c6a-114">A cadeia de caracteres para este parâmetro contém literais e uma variável entre chaves ({*formato*}).</span><span class="sxs-lookup"><span data-stu-id="a3c6a-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="a3c6a-115">Essa variável corresponde à operação de serviço `format` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="a3c6a-116">Para obter mais informações, consulte <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="a3c6a-117">`BodyStyle` afeta como as mensagens que esta operação de serviço envia e recebe são gravadas.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="a3c6a-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Especifica que os dados enviados de e para esta operação de serviço não são encapsulados por elementos XML definido de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="a3c6a-119">Para obter mais informações, consulte <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a3c6a-120">Use o <xref:System.ServiceModel.ServiceKnownTypeAttribute> para especificar os tipos que são retornados pelas operações de serviço nesta interface.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="a3c6a-121">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="a3c6a-122">Criar um <xref:System.ServiceModel.Syndication.SyndicationFeed> do objeto e adicionar um autor, categoria e descrição.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="a3c6a-123">Criar diversos <xref:System.ServiceModel.Syndication.SyndicationItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="a3c6a-124">Adicionar o <xref:System.ServiceModel.Syndication.SyndicationItem> objetos para o feed.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="a3c6a-125">Use o parâmetro de formato para retornar o formato solicitado.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="a3c6a-126">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="a3c6a-126">To host the service</span></span>  
  
1.  <span data-ttu-id="a3c6a-127">Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="a3c6a-128">O <xref:System.ServiceModel.Web.WebServiceHost> classe adiciona automaticamente um ponto de extremidade no endereço base do serviço, a menos que é especificada na configuração ou código.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="a3c6a-129">Neste exemplo, nenhum ponto de extremidade é especificados para que o ponto de extremidade padrão é exposto.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="a3c6a-130">Abrir o host de serviço, carregar o feed do serviço, exibir o feed e aguarde até que o usuário pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="a3c6a-131">Para chamar GetBlog com um HTTP GET</span><span class="sxs-lookup"><span data-stu-id="a3c6a-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="a3c6a-132">Abra o Internet Explorer, digite a URL a seguir e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-132">Open Internet Explorer, type the following URL, and press ENTER.</span></span> <span data-ttu-id="a3c6a-133">http://localhost:8000/BlogService/GetBlog</span><span class="sxs-lookup"><span data-stu-id="a3c6a-133">http://localhost:8000/BlogService/GetBlog</span></span>  
  
     <span data-ttu-id="a3c6a-134">A URL contém o endereço base do serviço (http://localhost:8000/BlogService), o endereço relativo do ponto de extremidade e chamar a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-134">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="a3c6a-135">Para chamar GetBlog() do código</span><span class="sxs-lookup"><span data-stu-id="a3c6a-135">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="a3c6a-136">Criar um <xref:System.Xml.XmlReader> com o endereço base e o método de chamada.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-136">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="a3c6a-137">Chamar estático <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> método, passando o <xref:System.Xml.XmlReader> você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-137">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="a3c6a-138">Isso chama a operação de serviço e preenche um novo <xref:System.ServiceModel.Syndication.SyndicationFeed> com o formatador retornado da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-138">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="a3c6a-139">Acesse o objeto de feed.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-139">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="a3c6a-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3c6a-140">Example</span></span>  
 <span data-ttu-id="a3c6a-141">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-141">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a3c6a-142">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a3c6a-142">Compiling the Code</span></span>  
 <span data-ttu-id="a3c6a-143">Ao compilar o código anterior, fazer referência a System.ServiceModel.dll e System.</span><span class="sxs-lookup"><span data-stu-id="a3c6a-143">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c6a-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3c6a-144">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
