---
title: 'Como: criar um feed Atom básico'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 11aa71f82af5a1bd764a4cc9e3514a795d559fc2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311845"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="72911-102">Como: criar um feed Atom básico</span><span class="sxs-lookup"><span data-stu-id="72911-102">How to: Create a Basic Atom Feed</span></span>
<span data-ttu-id="72911-103">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um feed de sindicalização.</span><span class="sxs-lookup"><span data-stu-id="72911-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="72911-104">Este tópico discute como criar um serviço de distribuição que expõe um feed de distribuição Atom.</span><span class="sxs-lookup"><span data-stu-id="72911-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="72911-105">Para criar um serviço básico de distribuição</span><span class="sxs-lookup"><span data-stu-id="72911-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="72911-106">Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="72911-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="72911-107">Cada operação que é exposta como um feed de sindicalização deve retornar um <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> objeto.</span><span class="sxs-lookup"><span data-stu-id="72911-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="72911-108">Todas as operações de serviço que se aplicam a <xref:System.ServiceModel.Web.WebGetAttribute> são mapeados para as solicitações HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="72911-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="72911-109">Para mapear sua operação para um método diferente de HTTP, use o <xref:System.ServiceModel.Web.WebInvokeAttribute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="72911-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="72911-110">Para obter mais informações, confira [Como: Criar um serviço de Web HTTP WCF básico](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="72911-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="72911-111">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="72911-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="72911-112">Criar um <xref:System.ServiceModel.Syndication.SyndicationFeed> do objeto e adicionar um autor, categoria e descrição.</span><span class="sxs-lookup"><span data-stu-id="72911-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="72911-113">Criar vários <xref:System.ServiceModel.Syndication.SyndicationItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="72911-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="72911-114">Adicionar o <xref:System.ServiceModel.Syndication.SyndicationItem> objetos para o feed.</span><span class="sxs-lookup"><span data-stu-id="72911-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="72911-115">Retorne o feed.</span><span class="sxs-lookup"><span data-stu-id="72911-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="72911-116">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="72911-116">To host the service</span></span>  
  
1. <span data-ttu-id="72911-117">Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="72911-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="72911-118">Abra o host de serviço, carregar o feed do serviço, exibir a transmissão e aguarde até que o usuário pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="72911-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="72911-119">Para chamar GetBlog() com um HTTP GET</span><span class="sxs-lookup"><span data-stu-id="72911-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="72911-120">Abra o Internet Explorer, digite a URL a seguir e pressione ENTER:</span><span class="sxs-lookup"><span data-stu-id="72911-120">Open Internet Explorer, type the following URL, and press ENTER:</span></span> `http://localhost:8000/BlogService/GetBlog`  
  
     <span data-ttu-id="72911-121">A URL contém o endereço base do serviço (`http://localhost:8000/BlogService`), o endereço relativo do ponto de extremidade e a operação de serviço para chamar.</span><span class="sxs-lookup"><span data-stu-id="72911-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="72911-122">Para chamar GetBlog() do código</span><span class="sxs-lookup"><span data-stu-id="72911-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="72911-123">Criar um <xref:System.Xml.XmlReader> com o endereço básico e o método que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="72911-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="72911-124">Chamar estático <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> método, passando o <xref:System.Xml.XmlReader> você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="72911-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="72911-125">Isso invoca a operação de serviço e preenche um novo <xref:System.ServiceModel.Syndication.SyndicationFeed> com o formatador retornado da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="72911-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="72911-126">Acesse o objeto de feed.</span><span class="sxs-lookup"><span data-stu-id="72911-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="72911-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72911-127">Example</span></span>  
 <span data-ttu-id="72911-128">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="72911-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72911-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="72911-129">Compiling the Code</span></span>  
 <span data-ttu-id="72911-130">Ao compilar o código anterior, fazer referência a ServiceModel. dll e System.</span><span class="sxs-lookup"><span data-stu-id="72911-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72911-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72911-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
