---
title: 'Como: Migrar o código de XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7022a0f55cd7994141148bc6b2faefb10bfea416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966986"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="9cc83-102">Como: Migrar o código de XslTransform</span><span class="sxs-lookup"><span data-stu-id="9cc83-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="9cc83-103">As novas classes XSLT foram criadas para ser muito semelhantes às classes existentes.</span><span class="sxs-lookup"><span data-stu-id="9cc83-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="9cc83-104">A classe de <xref:System.Xml.Xsl.XslCompiledTransform> substitui a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="9cc83-105">As folhas de estilos são criadas usando o método de <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="9cc83-106">Transforms é executado usando o método <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="9cc83-107">Os procedimentos a seguir mostram tarefas comuns XSLT, e comparam o código usando a classe de <xref:System.Xml.Xsl.XslTransform> contra a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="9cc83-108">Para transformar um arquivo e uma saída para o URI</span><span class="sxs-lookup"><span data-stu-id="9cc83-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="9cc83-109">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="9cc83-110">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="9cc83-111">Para criar uma folha de estilos e usar um resolvedor com credenciais padrão</span><span class="sxs-lookup"><span data-stu-id="9cc83-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="9cc83-112">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="9cc83-113">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="9cc83-114">Para usar um parâmetro XSLT</span><span class="sxs-lookup"><span data-stu-id="9cc83-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="9cc83-115">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="9cc83-116">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="9cc83-117">Para habilitar scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="9cc83-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="9cc83-118">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="9cc83-119">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="9cc83-120">Para carregar os resultados nos objetos DOM</span><span class="sxs-lookup"><span data-stu-id="9cc83-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="9cc83-121">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="9cc83-122">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9cc83-123">A classe de <xref:System.Xml.Xsl.XslCompiledTransform> não tem um método que retorna os resultados da transformação XSLT como um objeto de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="9cc83-124">No entanto, você pode dar saída a um arquivo XML e carregar o arquivo XML em outro objeto.</span><span class="sxs-lookup"><span data-stu-id="9cc83-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="9cc83-125">Para passar os resultados em outro armazenamento de dados</span><span class="sxs-lookup"><span data-stu-id="9cc83-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="9cc83-126">Código usando a classe de <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="9cc83-127">Código usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9cc83-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="9cc83-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cc83-128">See also</span></span>

- [<span data-ttu-id="9cc83-129">Migrando da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="9cc83-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="9cc83-130">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="9cc83-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
