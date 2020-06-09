---
title: Como o modelo de objeto de sindicalização do WCF mapeia para Atom e RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: 67fbbb035a3a6683cefbf24e299f32579b674bbd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597248"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="a0c0f-102">Como o modelo de objeto de sindicalização do WCF mapeia para Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="a0c0f-102">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>
<span data-ttu-id="a0c0f-103">Ao desenvolver um serviço de distribuição do Windows Communication Foundation (WCF), você cria feeds e itens usando as seguintes classes:</span><span class="sxs-lookup"><span data-stu-id="a0c0f-103">When developing a Windows Communication Foundation (WCF) syndication service, you create feeds and items using the following classes:</span></span>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="a0c0f-104">Um <xref:System.ServiceModel.Syndication.SyndicationFeed> pode ser serializado em qualquer formato de distribuição para o qual um formatador é definido.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> <span data-ttu-id="a0c0f-105">O WCF é fornecido com dois formatadores: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> e <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="a0c0f-105">WCF ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="a0c0f-106">O modelo de objeto <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> é alinhado mais de perto com a especificação Atom 1,0 do que a especificação RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-106">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="a0c0f-107">Isso ocorre porque o Atom 1,0 é uma especificação mais significativa que define os elementos que são ambíguos ou omitidos da especificação RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-107">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="a0c0f-108">Por isso, muitos itens no modelo de objeto de distribuição do WCF não têm nenhuma representação direta na especificação RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-108">Because of this, many items in the WCF syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="a0c0f-109">Ao serializar <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> os objetos no RSS 2,0, o WCF permite serializar elementos de dados específicos de Atom como elementos de extensão qualificados por namespace que estão em conformidade com a especificação Atom.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-109">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, WCF allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="a0c0f-110">Você pode controlar isso com um parâmetro passado para o <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> Construtor.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-110">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="a0c0f-111">Os exemplos de código neste tópico usam um dos dois métodos definidos aqui para fazer a serialização real.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-111">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="a0c0f-112">`SerializeFeed`Serializa um feed de agregação.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-112">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="a0c0f-113">`SerializeItem`Serializa um item de distribuição.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-113">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="a0c0f-114">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="a0c0f-114">SyndicationFeed</span></span>  
 <span data-ttu-id="a0c0f-115">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-115">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="a0c0f-116">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationFeed> é serializado para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-116">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="a0c0f-117">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationFeed> é serializado para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationitem"></a><span data-ttu-id="a0c0f-118">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="a0c0f-118">SyndicationItem</span></span>  
 <span data-ttu-id="a0c0f-119">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.SyndicationItem> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-119">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="a0c0f-120">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationItem> é serializado para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-120">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="a0c0f-121">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationItem> é serializado para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
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
  
## <a name="syndicationperson"></a><span data-ttu-id="a0c0f-122">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="a0c0f-122">SyndicationPerson</span></span>  
 <span data-ttu-id="a0c0f-123">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.SyndicationPerson> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-123">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="a0c0f-124">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationPerson> é serializado para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-124">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
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
  
 <span data-ttu-id="a0c0f-125">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.SyndicationPerson> classe é serializada para RSS 2,0 se <xref:System.ServiceModel.Syndication.SyndicationPerson> existir apenas uma `Authors` nas `Contributors` coleções ou, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="a0c0f-126">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.SyndicationPerson> classe é serializada para RSS 2,0 se houver mais de um <xref:System.ServiceModel.Syndication.SyndicationPerson> nas `Authors` `Contributors` coleções ou, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
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
  
## <a name="syndicationlink"></a><span data-ttu-id="a0c0f-127">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="a0c0f-127">SyndicationLink</span></span>  
 <span data-ttu-id="a0c0f-128">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.SyndicationLink> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-128">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="a0c0f-129">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationLink> é serializado para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-129">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="a0c0f-130">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationLink> é serializado para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="a0c0f-131">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="a0c0f-131">SyndicationCategory</span></span>  
 <span data-ttu-id="a0c0f-132">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.SyndicationCategory> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-132">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="a0c0f-133">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationCategory> é serializado para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-133">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="a0c0f-134">O XML a seguir mostra como o <xref:System.ServiceModel.Syndication.SyndicationCategory> é serializado para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="a0c0f-135">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="a0c0f-135">TextSyndicationContent</span></span>  
 <span data-ttu-id="a0c0f-136">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe para Atom 1,0 e RSS 2,0 quando <xref:System.ServiceModel.Syndication.TextSyndicationContent> é criado com conteúdo HTML.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-136">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="a0c0f-137">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo HTML é serializada para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-137">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="a0c0f-138">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo HTML é serializada para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="a0c0f-139">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe para Atom 1,0 e RSS 2,0 quando <xref:System.ServiceModel.Syndication.TextSyndicationContent> é criado com conteúdo de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-139">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="a0c0f-140">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo de texto sem formatação é serializada para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-140">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="a0c0f-141">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo de texto sem formatação é serializada para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="a0c0f-142">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe para Atom 1,0 e RSS 2,0 quando <xref:System.ServiceModel.Syndication.TextSyndicationContent> é criado com conteúdo XHTML.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-142">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="a0c0f-143">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo XHTML é serializada para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-143">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="a0c0f-144">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.TextSyndicationContent> classe com conteúdo XHTML é serializada para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="a0c0f-145">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="a0c0f-145">UrlSyndicationContent</span></span>  
 <span data-ttu-id="a0c0f-146">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.UrlSyndicationContent> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-146">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="a0c0f-147">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.UrlSyndicationContent> classe é serializada para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-147">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="a0c0f-148">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.UrlSyndicationContent> classe com conteúdo XHTML é serializada para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="a0c0f-149">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="a0c0f-149">XmlSyndicationContent</span></span>  
 <span data-ttu-id="a0c0f-150">O exemplo de código a seguir mostra como serializar a <xref:System.ServiceModel.Syndication.XmlSyndicationContent> classe para Atom 1,0 e RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-150">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="a0c0f-151">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.XmlSyndicationContent> classe é serializada para Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-151">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="a0c0f-152">O XML a seguir mostra como a <xref:System.ServiceModel.Syndication.XmlSyndicationContent> classe com conteúdo XHTML é serializada para RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0c0f-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="a0c0f-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0c0f-153">See also</span></span>

- [<span data-ttu-id="a0c0f-154">Visão geral de sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="a0c0f-154">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)
- [<span data-ttu-id="a0c0f-155">Arquitetura de sindicalização</span><span class="sxs-lookup"><span data-stu-id="a0c0f-155">Architecture of Syndication</span></span>](architecture-of-syndication.md)
- [<span data-ttu-id="a0c0f-156">Como criar um feed RSS básico</span><span class="sxs-lookup"><span data-stu-id="a0c0f-156">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)
- [<span data-ttu-id="a0c0f-157">Como criar um Feed Atom básico</span><span class="sxs-lookup"><span data-stu-id="a0c0f-157">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)
- [<span data-ttu-id="a0c0f-158">Como expor um feed como Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="a0c0f-158">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)
