---
title: A classe XslTransform implementa do processador XSLT
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
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167cd81ecbc25ca243e3b4a7a6aa7327679528e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="e1e8e-102">A classe XslTransform implementa do processador XSLT</span><span class="sxs-lookup"><span data-stu-id="e1e8e-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="e1e8e-103">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1e8e-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="e1e8e-104">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e1e8e-105">Consulte [usando a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [migrar da classe de XslTransform o](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="e1e8e-106">A classe de <xref:System.Xml.Xsl.XslTransform> é um processador XSLT que implementa a recomendação de versão 1,0 de transformações XSL (XSLT).</span><span class="sxs-lookup"><span data-stu-id="e1e8e-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="e1e8e-107">O método de <xref:System.Xml.Xsl.XslTransform.Load%2A> localiza e ler as folhas de estilos, e o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> torna o documento de origem determinado.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="e1e8e-108">Qualquer armazenamento que implemente a interface de <xref:System.Xml.XPath.IXPathNavigable> pode ser usado como o documento de origem para <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="e1e8e-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] atualmente implementa a interface de <xref:System.Xml.XPath.IXPathNavigable> em <xref:System.Xml.XmlDocument>, em <xref:System.Xml.XmlDataDocument>, e em <xref:System.Xml.XPath.XPathDocument>, para que todos estes pode ser usado como o documento de fonte de entrada para uma transformação.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="e1e8e-110">O objeto de <xref:System.Xml.Xsl.XslTransform> em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferece suporte somente a especificação XSLT 1,0, definida com a seguir namespace:</span><span class="sxs-lookup"><span data-stu-id="e1e8e-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="e1e8e-111">A folha de estilos pode ser carregada, usando o método <xref:System.Xml.Xsl.XslTransform.Load%2A> , de uma das seguintes classes:</span><span class="sxs-lookup"><span data-stu-id="e1e8e-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="e1e8e-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e1e8e-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="e1e8e-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="e1e8e-113">XmlReader</span></span>  
  
-   <span data-ttu-id="e1e8e-114">Uma cadeia de caracteres que representa um URL</span><span class="sxs-lookup"><span data-stu-id="e1e8e-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="e1e8e-115">Há um método diferente de <xref:System.Xml.Xsl.XslTransform.Load%2A> para cada uma das classes acima de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="e1e8e-116">Alguns métodos recolhem uma combinação de uma dessas classes e a classe de <xref:System.Xml.XmlResolver> como argumentos.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="e1e8e-117"><xref:System.Xml.XmlResolver> encontrar os recursos referenciados por `<xsl:import>` ou `<xsl:include>` encontrado na folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="e1e8e-118">Os seguintes métodos recebem uma cadeia de caracteres, <xref:System.Xml.XmlReader>, ou <xref:System.Xml.XPath.XPathNavigator> como entrada.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
```vb  
Overloads Public Sub Load(String)  
```  
  
```csharp  
public void Load(string);  
```  
  
```vb  
Overloads Public Sub Load(String, XmlResolver)  
```  
  
```csharp  
public void Load(string, XmlResolver);  
```  
  
```vb  
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XmlReader, XmlResolver, Evidence);  
```  
  
```vb  
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XPathNavigator, XmlResolver, Evidence);  
```  
  
 <span data-ttu-id="e1e8e-119">A maioria dos métodos de <xref:System.Xml.Xsl.XslTransform.Load%2A> mostradas acima recebem <xref:System.Xml.XmlResolver> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="e1e8e-120"><xref:System.Xml.XmlResolver> é usado para carregar a folha de estilos e qualquer folha de estilos referenciadas em XSL: importação e XSL: inclua elementos.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="e1e8e-121">A maioria dos métodos de <xref:System.Xml.Xsl.XslTransform.Load%2A> também têm a evidência como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="e1e8e-122">O parâmetro de evidência é <xref:System.Security.Policy.Evidence> que está associado com a folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="e1e8e-123">O nível de segurança de folha de estilo afeta o nível de segurança todos os recursos que subsequentes referência, como o script contém, quaisquer funções de `document()` usa, e todos os objetos de extensão usados por <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="e1e8e-124">Se a folha de estilos é carregada usando um método de <xref:System.Xml.Xsl.XslTransform.Load%2A> que não contenha um parâmetro de URL e nenhuma evidência é fornecida, a evidência de folha de estilos é calculada pelo URL dado com suas site e zona.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="e1e8e-125">Se nenhum URI ou evidência é fornecido, então a evidência definida para a folha de estilos é totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="e1e8e-126">Não carregar folhas de estilos de fontes não confiáveis, ou adicionar objetos não confiáveis de extensão em <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="e1e8e-127">Para obter mais informações sobre níveis de segurança e evidência e como ele afeta a execução de scripts, consulte [XSLT folha de estilos de script usando \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="e1e8e-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="e1e8e-128">Para obter informações sobre os níveis de segurança e evidência e como ele afeta os objetos de extensão, consulte [XsltArgumentList para parâmetros de folha de estilos e objetos de extensão](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="e1e8e-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="e1e8e-129">Para obter informações sobre os níveis de segurança e evidência e como ele afeta o `document()` funcionam, consulte [Resolvendo folhas de estilos XSLT externa e documentos](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="e1e8e-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="e1e8e-130">Uma folha de estilos pode ser fornecida com um número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="e1e8e-131">A folha de estilos também pode chamar funções em objetos de extensão.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="e1e8e-132">Os parâmetros e objetos de extensão são fornecidos para a folha de estilos usando a classe de <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="e1e8e-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="e1e8e-133">Para obter mais informações sobre <xref:System.Xml.Xsl.XsltArgumentList>, consulte <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="e1e8e-134">Seguro uso recomendado da classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="e1e8e-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="e1e8e-135">Os privilégios de segurança de folha de estilos depende evidências fornecida.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="e1e8e-136">A tabela a seguir resume o local de folha de estilos e fornece uma explicação do tipo de evidência para dar.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="e1e8e-137">A folha de estilos XSLT não tem nenhuma referência externo, ou a folha de estilos vem de uma base de código que você confie.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="e1e8e-138">Fornecer a evidência do seu conjunto:</span><span class="sxs-lookup"><span data-stu-id="e1e8e-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="e1e8e-139">A folha de estilos XSLT vem de uma fonte externa.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="e1e8e-140">A origem de origem é conhecida e há URI verificável.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="e1e8e-141">Crie a evidência usando um URI.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="e1e8e-142">A folha de estilos XSLT vem de uma fonte externa.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="e1e8e-143">A origem de origem não é conhecida.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="e1e8e-144">Defina a evidência a `null`.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-144">Set evidence to `null`.</span></span> <span data-ttu-id="e1e8e-145">Blocos de script não são processados, a função XSLT `document()` não é suportada, e objetos privilegiados de extensão não é permitida.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="e1e8e-146">Além disso, você pode também definir o parâmetro de `resolver` a `null` que isso garante que `xsl:import` e elementos de `xsl:include` não sejam processadas.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="e1e8e-147">A folha de estilos XSLT vem de uma fonte externa.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="e1e8e-148">A origem de origem não é conhecido, mas você precisar de suporte de script.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="e1e8e-149">Evidência de solicitação do chamador.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="e1e8e-150">Transformação de dados XML</span><span class="sxs-lookup"><span data-stu-id="e1e8e-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="e1e8e-151">Uma vez que uma folha de estilos é carregada, a transformação chamando um dos métodos de <xref:System.Xml.Xsl.XslTransform.Transform%2A> e fornecendo um documento de fonte de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="e1e8e-152">O método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> é sobrecarregado para fornecer saída diferente de transformação.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="e1e8e-153">A transformação pode levar a seguir formata de saída:</span><span class="sxs-lookup"><span data-stu-id="e1e8e-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="e1e8e-154">URL de cadeia de caracteres de arquivo</span><span class="sxs-lookup"><span data-stu-id="e1e8e-154">String URL of file</span></span>  
  
 <span data-ttu-id="e1e8e-155">Esse último formato, o URL de cadeia de caracteres, fornece um cenário de uso geral em transformar um documento de entrada localizado em um URL e gravar no documento a URL de saída.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="e1e8e-156">Este método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> é um método conveniente para carregar um documento XML de um arquivo, para executar a transformação XSLT, e para escrever a saída para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="e1e8e-157">Isso impede que você tem que criar e carregar o documento de fonte de entrada, e grava a um fluxo de arquivos.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="e1e8e-158">O exemplo de código a seguir mostra o uso do método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> usando o URL de cadeia de caracteres como entrada e saída:</span><span class="sxs-lookup"><span data-stu-id="e1e8e-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
```vb  
Dim xsltransform As XslTransform = New XslTransform()  
xsltransform.Load("favorite.xsl")  
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)  
```  
  
```csharp  
XslTransform xsltransform = new XslTransform();  
xsltransform.Load("favorite.xsl");  
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);  
```  
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="e1e8e-159">Transformando uma seção de um documento XML</span><span class="sxs-lookup"><span data-stu-id="e1e8e-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="e1e8e-160">As transformações são aplicadas ao documento no dataset.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="e1e8e-161">Ou seja se você passar em um nó que não seja o nó de diretório base, isso não impede que o processo de transformação acessar todos os nós do documento carregado.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="e1e8e-162">Para transformar um fragmento da árvore de resultado, você deve criar <xref:System.Xml.XmlDocument> que contém apenas o fragmento da árvore de resultado e passe o <xref:System.Xml.XmlDocument> para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1e8e-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="e1e8e-163">O exemplo a seguir executa uma transformação em um fragmento da árvore de resultado.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
```vb  
Dim xslt As New XslTransform()  
xslt.Load("print_root.xsl")  
Dim doc As New XmlDocument()  
doc.Load("library.xml")  
' Create a new document containing just the result tree fragment.  
Dim testNode As XmlNode = doc.DocumentElement.FirstChild  
Dim tmpDoc As New XmlDocument()  
tmpDoc.LoadXml(testNode.OuterXml)  
' Pass the document containing the result tree fragment   
' to the Transform method.  
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))  
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)  
```  
  
```csharp  
XslTransform xslt = new XslTransform();       
xslt.Load("print_root.xsl");  
XmlDocument doc = new XmlDocument();  
doc.Load("library.xml");  
// Create a new document containing just the result tree fragment.  
XmlNode testNode = doc.DocumentElement.FirstChild;   
XmlDocument tmpDoc = new XmlDocument();   
tmpDoc.LoadXml(testNode.OuterXml);  
// Pass the document containing the result tree fragment   
// to the Transform method.  
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");  
xslt.Transform(tmpDoc, null, Console.Out, null);  
```  
  
 <span data-ttu-id="e1e8e-164">O exemplo usa os arquivos de library.xml e de print_root.xsl como entrada e saída o seguinte no console.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="e1e8e-165">library.xml</span><span class="sxs-lookup"><span data-stu-id="e1e8e-165">library.xml</span></span>  
  
```xml  
<library>  
  <book genre='novel' ISBN='1-861001-57-5'>  
     <title>Pride And Prejudice</title>  
  </book>  
  <book genre='novel' ISBN='1-81920-21-2'>  
     <title>Hook</title>  
  </book>  
</library>  
```  
  
 <span data-ttu-id="e1e8e-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="e1e8e-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="e1e8e-167">Migração XSLT do .NET Framework versão 1,0 para a versão 1,1 do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e1e8e-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="e1e8e-168">A tabela a seguir mostra a versão obsoleta de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1,0 métodos e a nova versão de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1,1 métodos para o método de <xref:System.Xml.Xsl.XslTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1e8e-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="e1e8e-169">Novos métodos permitem que você limitar as permissões de folha de estilos especificando a evidência.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="e1e8e-170">Métodos de carregamento do .NET Framework versão 1.0 e obsoleto</span><span class="sxs-lookup"><span data-stu-id="e1e8e-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="e1e8e-171">Métodos de carregamento substituição do .NET Framework versão 1.1</span><span class="sxs-lookup"><span data-stu-id="e1e8e-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="e1e8e-172">Carregamento XPathNavigator conectado (;)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="e1e8e-173">Carregando (entrada de XPathNavigator, resolvedor de XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="e1e8e-174">Carregando (folha de estilos de XPathNavigator, resolvedor de XmlResolver, evidência de evidência);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="e1e8e-175">Carregando (folha de estilos de IXPathNavigable);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="e1e8e-176">Carregando (folha de estilos de IXPathNavigable, resolvedor de XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="e1e8e-177">Carregando (folha de estilos de IXPathNavigable, resolvedor de XmlResolver, evidência de evidência);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="e1e8e-178">Carregando (folha de estilos de XmlReader);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="e1e8e-179">Carregando (folha de estilos de XmlReader, resolvedor de XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="e1e8e-180">Carregando (folha de estilos de XmlReader, resolvedor de XmlResolver, evidência de evidência);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="e1e8e-181">A tabela a seguir mostra os métodos obsoletos e novos para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="e1e8e-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="e1e8e-182">Novos métodos recebem um objeto de <xref:System.Xml.XmlResolver> .</span><span class="sxs-lookup"><span data-stu-id="e1e8e-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="e1e8e-183">Obsoleto métodos de transformação do .NET Framework versão 1.0</span><span class="sxs-lookup"><span data-stu-id="e1e8e-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="e1e8e-184">Versão do .NET Framework de substituição transformar 1.1 métodos</span><span class="sxs-lookup"><span data-stu-id="e1e8e-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="e1e8e-185">XmlReader transformação (entrada de XPathNavigator, os args de XsltArgumentList)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="e1e8e-186">XmlReader transformação (entrada de XPathNavigator, args de XsltArgumentList, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-187">XmlReader transformação (entrada de IXPathNavigable, os args de XsltArgumentList)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="e1e8e-188">XmlReader transformação (entrada de IXPathNavigable, args de XsltArgumentList, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-189">O vácuo transformação (entrada de XPathNavigator, args de XsltArgumentList, a saída de XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="e1e8e-190">O vácuo transformação (entrada de XPathNavigator, args de XsltArgumentList, a saída de XmlWriter, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-191">O vácuo transformação (entrada de IXPathNavigable, args de XsltArgumentList, a saída de XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="e1e8e-192">O vácuo transformação (entrada de IXpathNavigable, args de XsltArgumentList, a saída de XmlWriter, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-193">O vácuo transformação (entrada de XPathNavigator, args de XsltArgumentList, a saída de Textreader)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="e1e8e-194">O vácuo transformação (entrada de XPathNavigator, args de XsltArgumentList, a saída de Textreader, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-195">O vácuo transformação (entrada de IXPathNavigable, args de XsltArgumentList, a saída de Textreader)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="e1e8e-196">O vácuo transformação (entrada de IXPathNavigable, args de XsltArgumentList, a saída de Textreader, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-197">O vácuo transformação (entrada de XPathNavigator, args de XsltArgumentList, a saída de fluxo)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="e1e8e-198">O vácuo transformação (entrada de XPathNavigator, args de XsltArgumentList, a saída de fluxo, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-199">O vácuo transformação (entrada de IXPathNavigable, args de XsltArgumentList, a saída de fluxo)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="e1e8e-200">O vácuo transformação (entrada de IXPathNavigable, args de XsltArgumentList, a saída de fluxo, o resolvedor de XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="e1e8e-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="e1e8e-201">O vácuo transformação (entrada de cadeia de caracteres, a saída de cadeia de caracteres);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="e1e8e-202">O vácuo transformação (entrada de cadeia de caracteres, a saída de cadeia de caracteres, resolvedor de XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="e1e8e-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="e1e8e-203">A propriedade de <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> é obsoleta na versão 1,1 de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e1e8e-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="e1e8e-204">Em vez disso, use o novo <xref:System.Xml.Xsl.XslTransform.Transform%2A> sobrecargas que têm um <xref:System.Xml.XmlResolver> objeto.</span><span class="sxs-lookup"><span data-stu-id="e1e8e-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e8e-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1e8e-205">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="e1e8e-206">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="e1e8e-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="e1e8e-207">XPathNavigator nas transformações</span><span class="sxs-lookup"><span data-stu-id="e1e8e-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="e1e8e-208">XPathNodeIterator nas transformações</span><span class="sxs-lookup"><span data-stu-id="e1e8e-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="e1e8e-209">Entrada XPathDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="e1e8e-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="e1e8e-210">Entrada de XmlDataDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="e1e8e-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="e1e8e-211">Entrada de XmlDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="e1e8e-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
