---
title: Saída de um XslTransform
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 647f3829f4b26791c063d5646669b2fcb7ab6684
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="4b55c-102">Saída de um XslTransform</span><span class="sxs-lookup"><span data-stu-id="4b55c-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="4b55c-103">Como as folhas de estilos podem determinar o formato de saída usando uma instrução de `<xsl:output>` com o atributo de `method` , a tabela a seguir descreve quais o formato de saída é quando o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> é usado para gravar a saída, e o formato de saída é declarado como <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="4b55c-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b55c-104">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b55c-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="4b55c-105">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4b55c-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4b55c-106">Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4b55c-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="4b55c-107">Como as folhas de estilos podem determinar o formato de saída usando uma instrução de `<xsl:output>` com o atributo de `method` , a tabela a seguir descreve quais o formato de saída é quando o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> é usado para gravar a saída, e o formato de saída é declarado como <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="4b55c-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="4b55c-108">A tabela a seguir descreve o que acontece quando um tipo de saída é declarado pelo método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> em conjunto com o uso de uma instrução de `<xsl:output>` :</span><span class="sxs-lookup"><span data-stu-id="4b55c-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="4b55c-109">\<xsl:output method = > attribute</span><span class="sxs-lookup"><span data-stu-id="4b55c-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="4b55c-110">Formato de resultado</span><span class="sxs-lookup"><span data-stu-id="4b55c-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="4b55c-111">method= " XML”</span><span class="sxs-lookup"><span data-stu-id="4b55c-111">method="xml"</span></span>|<span data-ttu-id="4b55c-112">XML</span><span class="sxs-lookup"><span data-stu-id="4b55c-112">XML</span></span>|  
|<span data-ttu-id="4b55c-113">method= " HTML”</span><span class="sxs-lookup"><span data-stu-id="4b55c-113">method="html"</span></span>|<span data-ttu-id="4b55c-114">HTML</span><span class="sxs-lookup"><span data-stu-id="4b55c-114">HTML</span></span>|  
|<span data-ttu-id="4b55c-115">method= " texto”</span><span class="sxs-lookup"><span data-stu-id="4b55c-115">method="text"</span></span>|<span data-ttu-id="4b55c-116">Texto</span><span class="sxs-lookup"><span data-stu-id="4b55c-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4b55c-117">Observação: A declaração de `<xsl:output>` é ignorado quando a saída de método <xref:System.Xml.Xsl.XslTransform.Transform%2A> são <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4b55c-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="4b55c-118">Os seguintes atributos são suportados quando a saída de método <xref:System.Xml.Xsl.XslTransform.Transform%2A> são <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="4b55c-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="4b55c-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="4b55c-119">encoding\*</span></span>  
  
-   <span data-ttu-id="4b55c-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="4b55c-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="4b55c-121">autônomos</span><span class="sxs-lookup"><span data-stu-id="4b55c-121">standalone</span></span>  
  
-   <span data-ttu-id="4b55c-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="4b55c-122">doctype-public</span></span>  
  
-   <span data-ttu-id="4b55c-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="4b55c-123">doctype-system</span></span>  
  
-   <span data-ttu-id="4b55c-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="4b55c-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="4b55c-125">indent</span><span class="sxs-lookup"><span data-stu-id="4b55c-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b55c-126">o atributo de codificação de \*the é ignorado quando o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> está enviando saída a <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="4b55c-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="4b55c-127">A propriedade de codificação em <xref:System.IO.TextWriter> é usada em vez.</span><span class="sxs-lookup"><span data-stu-id="4b55c-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="4b55c-128">O seguinte atributo é ignorado quando a saída de método <xref:System.Xml.Xsl.XslTransform.Transform%2A> são <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="4b55c-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="4b55c-129">versão: a versão é sempre 1,0</span><span class="sxs-lookup"><span data-stu-id="4b55c-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="4b55c-130">médio tipo: o tipo médio</span><span class="sxs-lookup"><span data-stu-id="4b55c-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="4b55c-131">Caracteres de escape especiais</span><span class="sxs-lookup"><span data-stu-id="4b55c-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="4b55c-132">A marca de `<xsl:text disable-output-escaping>` é usada para indicar se os caracteres especiais precisam ser escapados em um formulário XML (por exemplo, usando `<&lt>` no lugar do símbolo de `"<"` ) ou esquerdo em condição atual.</span><span class="sxs-lookup"><span data-stu-id="4b55c-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="4b55c-133">O atributo de `disable-output-escaping` é ignorado quando uma transformação a <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> objetos e não tem efeito em caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="4b55c-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b55c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b55c-134">See Also</span></span>  
 [<span data-ttu-id="4b55c-135">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="4b55c-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
