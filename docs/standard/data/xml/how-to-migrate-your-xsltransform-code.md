---
title: "Como: Migrar seu código de XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9bfef535ecfae48ce09ef0eaca3f11de0a8d6667
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="60350-102">Como: Migrar seu código de XslTransform</span><span class="sxs-lookup"><span data-stu-id="60350-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="60350-103">As novas classes XSLT foram criadas para ser muito semelhantes às classes existentes.</span><span class="sxs-lookup"><span data-stu-id="60350-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="60350-104">A classe de <xref:System.Xml.Xsl.XslCompiledTransform> substitui a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="60350-105">As folhas de estilos são criadas usando o método de <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="60350-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="60350-106">Transforms é executado usando o método <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="60350-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="60350-107">Os procedimentos a seguir mostram tarefas comuns XSLT, e comparam o código usando a classe de <xref:System.Xml.Xsl.XslTransform> contra a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="60350-108">Para transformar um arquivo e uma saída para o URI</span><span class="sxs-lookup"><span data-stu-id="60350-108">To transform a file and output to a URI</span></span>  
  
-   <span data-ttu-id="60350-109">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
-   <span data-ttu-id="60350-110">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="60350-111">Para criar uma folha de estilos e usar um resolvedor com credenciais padrão</span><span class="sxs-lookup"><span data-stu-id="60350-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
-   <span data-ttu-id="60350-112">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
-   <span data-ttu-id="60350-113">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="60350-114">Para usar um parâmetro XSLT</span><span class="sxs-lookup"><span data-stu-id="60350-114">To use an XSLT parameter</span></span>  
  
-   <span data-ttu-id="60350-115">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
-   <span data-ttu-id="60350-116">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="60350-117">Para habilitar scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="60350-117">To enable XSLT scripting</span></span>  
  
-   <span data-ttu-id="60350-118">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
-   <span data-ttu-id="60350-119">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="60350-120">Para carregar os resultados nos objetos DOM</span><span class="sxs-lookup"><span data-stu-id="60350-120">To load the results into a DOM object</span></span>  
  
-   <span data-ttu-id="60350-121">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
-   <span data-ttu-id="60350-122">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="60350-123">A classe de <xref:System.Xml.Xsl.XslCompiledTransform> não tem um método que retorna os resultados da transformação XSLT como um objeto de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="60350-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="60350-124">No entanto, você pode dar saída a um arquivo XML e carregar o arquivo XML em outro objeto.</span><span class="sxs-lookup"><span data-stu-id="60350-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="60350-125">Para passar os resultados em outro armazenamento de dados</span><span class="sxs-lookup"><span data-stu-id="60350-125">To stream the results into another data store</span></span>  
  
-   <span data-ttu-id="60350-126">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
-   <span data-ttu-id="60350-127">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="60350-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="60350-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60350-128">See Also</span></span>  
 [<span data-ttu-id="60350-129">Migrando da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="60350-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 [<span data-ttu-id="60350-130">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="60350-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
