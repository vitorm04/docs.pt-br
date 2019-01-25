---
title: Como o modelo de objeto de sindicalização do WCF mapeia para Atom e RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: 7619dbfcdb0a3a219c9245d30518ffec8b586360
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671415"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="98cf5-102">Como o modelo de objeto de sindicalização do WCF mapeia para Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="98cf5-102">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>
<span data-ttu-id="98cf5-103">Ao desenvolver um serviço de distribuição do Windows Communication Foundation (WCF), você deve criar feeds e itens usando as classes a seguir:</span><span class="sxs-lookup"><span data-stu-id="98cf5-103">When developing a Windows Communication Foundation (WCF) syndication service, you create feeds and items using the following classes:</span></span>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="98cf5-104">Um <xref:System.ServiceModel.Syndication.SyndicationFeed> pode ser serializado em qualquer formato de distribuição para o qual um formatador é definido.</span><span class="sxs-lookup"><span data-stu-id="98cf5-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> <span data-ttu-id="98cf5-105">O WCF é fornecido com dois formatadores: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> e <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="98cf5-105">WCF ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="98cf5-106">O modelo de objeto em torno <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> é alinhado mais estreitamente com a especificação Atom 1.0 que a especificação RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-106">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="98cf5-107">Isso ocorre porque o Atom 1.0 é uma especificação mais significativa que define os elementos que são ambíguas ou omitida da especificação do RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-107">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="98cf5-108">Por isso, muitos itens no modelo de objeto de sindicalização do WCF não tem nenhuma representação direta na especificação do RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-108">Because of this, many items in the WCF syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="98cf5-109">Ao serializar <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> objetos em RSS 2.0, o WCF permite que você serializar os elementos de dados específicos do Atom como elementos de extensão qualificado de namespace que se adequa à especificação do Atom.</span><span class="sxs-lookup"><span data-stu-id="98cf5-109">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, WCF allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="98cf5-110">Você pode controlar isso com um parâmetro passado para o <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> construtor.</span><span class="sxs-lookup"><span data-stu-id="98cf5-110">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="98cf5-111">Os exemplos de código neste tópico usam um destes dois métodos definidos aqui para fazer a serialização real.</span><span class="sxs-lookup"><span data-stu-id="98cf5-111">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="98cf5-112">`SerializeFeed` serializa um feed de sindicalização.</span><span class="sxs-lookup"><span data-stu-id="98cf5-112">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="98cf5-113">`SerializeItem` serializa um item de sindicalização.</span><span class="sxs-lookup"><span data-stu-id="98cf5-113">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="98cf5-114">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="98cf5-114">SyndicationFeed</span></span>  
 <span data-ttu-id="98cf5-115">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.SyndicationFeed> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-115">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="98cf5-116">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationFeed> é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-116">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 <span data-ttu-id="98cf5-117">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationFeed> é serializado em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a><span data-ttu-id="98cf5-118">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="98cf5-118">SyndicationItem</span></span>  
 <span data-ttu-id="98cf5-119">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.SyndicationItem> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-119">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="98cf5-120">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationItem> é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-120">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 <span data-ttu-id="98cf5-121">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationItem> é serializado em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a><span data-ttu-id="98cf5-122">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="98cf5-122">SyndicationPerson</span></span>  
 <span data-ttu-id="98cf5-123">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.SyndicationPerson> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-123">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="98cf5-124">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationPerson> é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-124">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 <span data-ttu-id="98cf5-125">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationPerson> classe é serializada em RSS 2.0, se houver apenas uma <xref:System.ServiceModel.Syndication.SyndicationPerson> existe na `Authors` ou `Contributors` coleções, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="98cf5-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="98cf5-126">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationPerson> classe é serializada em RSS 2.0, se houver mais de um <xref:System.ServiceModel.Syndication.SyndicationPerson> existe na `Authors` ou `Contributors` coleções, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="98cf5-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a><span data-ttu-id="98cf5-127">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="98cf5-127">SyndicationLink</span></span>  
 <span data-ttu-id="98cf5-128">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.SyndicationLink> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-128">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="98cf5-129">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationLink> é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-129">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="98cf5-130">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationLink> é serializado em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="98cf5-131">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="98cf5-131">SyndicationCategory</span></span>  
 <span data-ttu-id="98cf5-132">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.SyndicationCategory> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-132">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="98cf5-133">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationCategory> é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-133">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="98cf5-134">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationCategory> é serializado em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="98cf5-135">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="98cf5-135">TextSyndicationContent</span></span>  
 <span data-ttu-id="98cf5-136">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe Atom 1.0 e RSS 2.0 quando <xref:System.ServiceModel.Syndication.TextSyndicationContent> é criado com um conteúdo HTML.</span><span class="sxs-lookup"><span data-stu-id="98cf5-136">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="98cf5-137">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com um conteúdo HTML é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-137">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="98cf5-138">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com um conteúdo HTML é serializada em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="98cf5-139">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe Atom 1.0 e RSS 2.0 quando <xref:System.ServiceModel.Syndication.TextSyndicationContent> é criado com o conteúdo de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="98cf5-139">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="98cf5-140">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com o conteúdo de texto sem formatação é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-140">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="98cf5-141">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com o conteúdo de texto sem formatação é serializada em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="98cf5-142">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe Atom 1.0 e RSS 2.0 quando <xref:System.ServiceModel.Syndication.TextSyndicationContent> é criado com o conteúdo XHTML.</span><span class="sxs-lookup"><span data-stu-id="98cf5-142">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="98cf5-143">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo XHTML é serializado para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-143">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="98cf5-144">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com o conteúdo XHTML é serializada em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="98cf5-145">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="98cf5-145">UrlSyndicationContent</span></span>  
 <span data-ttu-id="98cf5-146">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.UrlSyndicationContent> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-146">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="98cf5-147">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.UrlSyndicationContent> classe é serializada para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-147">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="98cf5-148">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.UrlSyndicationContent> classe com o conteúdo XHTML é serializada em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="98cf5-149">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="98cf5-149">XmlSyndicationContent</span></span>  
 <span data-ttu-id="98cf5-150">O exemplo de código a seguir mostra como serializar o <xref:System.ServiceModel.Syndication.XmlSyndicationContent> classe Atom 1.0 e RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-150">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="98cf5-151">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.XmlSyndicationContent> classe é serializada para Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-151">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="98cf5-152">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.XmlSyndicationContent> classe com o conteúdo XHTML é serializada em RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="98cf5-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="98cf5-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98cf5-153">See also</span></span>
- [<span data-ttu-id="98cf5-154">Visão geral de sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="98cf5-154">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [<span data-ttu-id="98cf5-155">Arquitetura de sindicalização</span><span class="sxs-lookup"><span data-stu-id="98cf5-155">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
- [<span data-ttu-id="98cf5-156">Como: Criar um RSS Feed básico</span><span class="sxs-lookup"><span data-stu-id="98cf5-156">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)
- [<span data-ttu-id="98cf5-157">Como: Criar um Feed Atom básico</span><span class="sxs-lookup"><span data-stu-id="98cf5-157">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)
- [<span data-ttu-id="98cf5-158">Como: Expor um Feed como Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="98cf5-158">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)
