---
title: 'Como: criar um RSS Feed básico'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 5bab8b5a19f33f8dcfcc5a5f5d882309a4b1cc99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771134"
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="426e8-102">Como: criar um RSS Feed básico</span><span class="sxs-lookup"><span data-stu-id="426e8-102">How to: Create a Basic RSS Feed</span></span>
<span data-ttu-id="426e8-103">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um feed de sindicalização.</span><span class="sxs-lookup"><span data-stu-id="426e8-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="426e8-104">Este tópico discute como criar um serviço de distribuição que expõe uma feed de sindicalização RSS.</span><span class="sxs-lookup"><span data-stu-id="426e8-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="426e8-105">Para criar um serviço básico de distribuição</span><span class="sxs-lookup"><span data-stu-id="426e8-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="426e8-106">Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="426e8-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="426e8-107">Cada operação que é exposta como um feed de sindicalização deve retornar um <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> objeto.</span><span class="sxs-lookup"><span data-stu-id="426e8-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="426e8-108">Todas as operações de serviço que se aplicam a <xref:System.ServiceModel.Web.WebGetAttribute> atributos são mapeados para as solicitações HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="426e8-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="426e8-109">Para mapear sua operação para um método diferente de HTTP, use o <xref:System.ServiceModel.Web.WebInvokeAttribute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="426e8-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="426e8-110">Para obter mais informações, confira [Como: Criar um serviço de Web HTTP WCF básico](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="426e8-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="426e8-111">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="426e8-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="426e8-112">Criar um <xref:System.ServiceModel.Syndication.SyndicationFeed> do objeto e adicionar um autor, categoria e descrição.</span><span class="sxs-lookup"><span data-stu-id="426e8-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="426e8-113">Criar vários <xref:System.ServiceModel.Syndication.SyndicationItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="426e8-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="426e8-114">Adicionar o <xref:System.ServiceModel.Syndication.SyndicationItem> no feed.</span><span class="sxs-lookup"><span data-stu-id="426e8-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="426e8-115">Retorne o feed.</span><span class="sxs-lookup"><span data-stu-id="426e8-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="426e8-116">Para hospedar um serviço</span><span class="sxs-lookup"><span data-stu-id="426e8-116">To host a service</span></span>  
  
1. <span data-ttu-id="426e8-117">Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="426e8-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="426e8-118">Abra o host do serviço e aguarde até que o usuário pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="426e8-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="426e8-119">Para chamar GetBlog() com um HTTP GET</span><span class="sxs-lookup"><span data-stu-id="426e8-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="426e8-120">Abra o Internet Explorer, digite a URL a seguir e pressione ENTER: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="426e8-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span> <span data-ttu-id="426e8-121">A URL contém o endereço base do serviço (`http://localhost:8000/BlogService`), o endereço relativo do ponto de extremidade e a operação de serviço para chamar.</span><span class="sxs-lookup"><span data-stu-id="426e8-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="426e8-122">Para chamar GetBlog() do código</span><span class="sxs-lookup"><span data-stu-id="426e8-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="426e8-123">Criar um <xref:System.Xml.XmlReader> com o endereço básico e o método que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="426e8-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="426e8-124">Chamar estático <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> método, passando o <xref:System.Xml.XmlReader> você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="426e8-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="426e8-125">Isso invoca a operação de serviço e preenche um novo <xref:System.ServiceModel.Syndication.SyndicationFeed> com o formatador retornado da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="426e8-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="426e8-126">Acesse o objeto de feed.</span><span class="sxs-lookup"><span data-stu-id="426e8-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="426e8-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="426e8-127">Example</span></span>  
 <span data-ttu-id="426e8-128">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="426e8-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="426e8-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="426e8-129">Compiling the Code</span></span>  
 <span data-ttu-id="426e8-130">Ao compilar o código anterior, fazer referência a ServiceModel. dll e System.</span><span class="sxs-lookup"><span data-stu-id="426e8-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426e8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="426e8-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
