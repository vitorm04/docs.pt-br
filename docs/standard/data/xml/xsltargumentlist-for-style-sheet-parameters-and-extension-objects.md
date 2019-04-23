---
title: XsltArgumentList para parâmetros de folha de estilos e objetos de extensão
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6209df7d226d7e3acb938801d1fb77afbe1249b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322401"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="2a88d-102">XsltArgumentList para parâmetros de folha de estilos e objetos de extensão</span><span class="sxs-lookup"><span data-stu-id="2a88d-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="2a88d-103">A classe de <xref:System.Xml.Xsl.XsltArgumentList> contém o idioma extensível de folha de estilos para objetos de parâmetros de transformações (XSLT) e a extensão XSLT.</span><span class="sxs-lookup"><span data-stu-id="2a88d-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="2a88d-104">Quando passados para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> , esses parâmetros e objetos de extensão podem ser chamados de folhas de estilos.</span><span class="sxs-lookup"><span data-stu-id="2a88d-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a88d-105">As classes de <xref:System.Xml.Xsl.XslTransform> e de <xref:System.Xml.Xsl.XsltArgumentList> são obsoletas em [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a88d-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="2a88d-106">Você pode realizar transformações XSLT usando a classe de <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="2a88d-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="2a88d-107">Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="2a88d-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="2a88d-108">A classe de <xref:System.Xml.Xsl.XsltArgumentList> contém objetos de parâmetros XSLT e de extensão XSLT.</span><span class="sxs-lookup"><span data-stu-id="2a88d-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="2a88d-109">Quando passados para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> , esses parâmetros e objetos de extensão podem ser chamados de folhas de estilos.</span><span class="sxs-lookup"><span data-stu-id="2a88d-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="2a88d-110">Os seguintes são vantagens de passar um objeto em vez de usar um script inserido:</span><span class="sxs-lookup"><span data-stu-id="2a88d-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
-   <span data-ttu-id="2a88d-111">Fornece a melhor encapsulamento e reutilização de classes.</span><span class="sxs-lookup"><span data-stu-id="2a88d-111">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="2a88d-112">Permite que as folhas de estilos são menores e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="2a88d-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
-   <span data-ttu-id="2a88d-113">Suporte que chamam métodos nas classes que pertencem aos espaços para nomes diferentes de aquelas definidas dentro do conjunto de namespaces suporte de <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="2a88d-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
-   <span data-ttu-id="2a88d-114">Suporte que passam partes da árvore de resultado à folha de estilos com o uso de <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="2a88d-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="2a88d-115">Parâmetros de folha de estilos XSLT</span><span class="sxs-lookup"><span data-stu-id="2a88d-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="2a88d-116">Os parâmetros XSLT são adicionados a <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="2a88d-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="2a88d-117">Um nome qualificado e um namespace Uniform Resource Identifier (URI) são associados com o objeto de parâmetro no momento.</span><span class="sxs-lookup"><span data-stu-id="2a88d-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="2a88d-118">O objeto de parâmetro deve corresponder a um tipo de World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="2a88d-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="2a88d-119">A tabela seguinte mostra tipos correspondentes W3C, as classes equivalentes de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (tipo), e se o tipo W3C é um tipo de idioma do caminho de XML (XPath) ou tipo de fonte.</span><span class="sxs-lookup"><span data-stu-id="2a88d-119">The following table shows the corresponding W3C types, the equivalent [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="2a88d-120">Tipo W3C</span><span class="sxs-lookup"><span data-stu-id="2a88d-120">W3C Type</span></span>|<span data-ttu-id="2a88d-121">Classe equivalente do .NET Framework (tipo)</span><span class="sxs-lookup"><span data-stu-id="2a88d-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="2a88d-122">Tipo XPath ou XSLT</span><span class="sxs-lookup"><span data-stu-id="2a88d-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="2a88d-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="2a88d-123">String</span></span>|<span data-ttu-id="2a88d-124">System.String</span><span class="sxs-lookup"><span data-stu-id="2a88d-124">System.String</span></span>|<span data-ttu-id="2a88d-125">XPath</span><span class="sxs-lookup"><span data-stu-id="2a88d-125">XPath</span></span>|  
|<span data-ttu-id="2a88d-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="2a88d-126">Boolean</span></span>|<span data-ttu-id="2a88d-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="2a88d-127">System.Boolean</span></span>|<span data-ttu-id="2a88d-128">XPath</span><span class="sxs-lookup"><span data-stu-id="2a88d-128">XPath</span></span>|  
|<span data-ttu-id="2a88d-129">Número</span><span class="sxs-lookup"><span data-stu-id="2a88d-129">Number</span></span>|<span data-ttu-id="2a88d-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="2a88d-130">System.Double</span></span>|<span data-ttu-id="2a88d-131">XPath</span><span class="sxs-lookup"><span data-stu-id="2a88d-131">XPath</span></span>|  
|<span data-ttu-id="2a88d-132">Fragmento da árvore de resultado</span><span class="sxs-lookup"><span data-stu-id="2a88d-132">Result Tree Fragment</span></span>|<span data-ttu-id="2a88d-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2a88d-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="2a88d-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="2a88d-134">XSLT</span></span>|  
|<span data-ttu-id="2a88d-135">Node Set</span><span class="sxs-lookup"><span data-stu-id="2a88d-135">Node Set</span></span>|<span data-ttu-id="2a88d-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="2a88d-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="2a88d-137">XPath</span><span class="sxs-lookup"><span data-stu-id="2a88d-137">XPath</span></span>|  
  
 <span data-ttu-id="2a88d-138">Se o objeto de parâmetro não é uma das classes anterior, é forçado a um double ou para a cadeia de caracteres, como apropriado.</span><span class="sxs-lookup"><span data-stu-id="2a88d-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="2a88d-139">Int16, UInt16, Int32, UInt32, UInt64, Int64, e escolha os tipos decimais são forçados para um double.</span><span class="sxs-lookup"><span data-stu-id="2a88d-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="2a88d-140">Todos os outros tipos são forçados a uma cadeia de caracteres usando o método `ToString` .</span><span class="sxs-lookup"><span data-stu-id="2a88d-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="2a88d-141">Para usar o parâmetro XSLT, o usuário precisará fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2a88d-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="2a88d-142">Crie <xref:System.Xml.Xsl.XsltArgumentList> e adicione os objetos usando <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a88d-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="2a88d-143">Chame os parâmetros de folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="2a88d-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="2a88d-144">Passar <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="2a88d-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2a88d-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a88d-145">Example</span></span>  
 <span data-ttu-id="2a88d-146">O exemplo a seguir usa o método de <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> para criar um parâmetro para conter uma data calculada de desconto.</span><span class="sxs-lookup"><span data-stu-id="2a88d-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="2a88d-147">A data de desconto é calculada para ser a 20 dias de data pedido.</span><span class="sxs-lookup"><span data-stu-id="2a88d-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="2a88d-148">Entrada</span><span class="sxs-lookup"><span data-stu-id="2a88d-148">Input</span></span>  
 <span data-ttu-id="2a88d-149">order.xml</span><span class="sxs-lookup"><span data-stu-id="2a88d-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="2a88d-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="2a88d-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="2a88d-151">Saída</span><span class="sxs-lookup"><span data-stu-id="2a88d-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="2a88d-152">Objetos de extensão XSLT</span><span class="sxs-lookup"><span data-stu-id="2a88d-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="2a88d-153">Os objetos de extensão XSLT são adicionados a <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="2a88d-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="2a88d-154">Um nome qualificado e URI de namespace são associados com o objeto de extensão no momento.</span><span class="sxs-lookup"><span data-stu-id="2a88d-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="2a88d-155">Quando um objeto é adicionado, o chamador de <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> deve ser totalmente confiável na política de segurança.</span><span class="sxs-lookup"><span data-stu-id="2a88d-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="2a88d-156">Se o chamador é de confiança parcial, a adição falhará.</span><span class="sxs-lookup"><span data-stu-id="2a88d-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="2a88d-157">Um objeto é adicionado embora com êxito, ele não garante que a execução será com êxito.</span><span class="sxs-lookup"><span data-stu-id="2a88d-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="2a88d-158">Quando o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> é chamado, as permissões são calculadas com a evidência fornecida em tempo de <xref:System.Xml.Xsl.XslTransform.Load%2A> , e esse conjunto de permissões é atribuído ao processo inteiro de transformação.</span><span class="sxs-lookup"><span data-stu-id="2a88d-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="2a88d-159">Se um objeto de extensão tentar iniciar uma ação que requer permissões não encontradas no dataset, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="2a88d-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="2a88d-160">Os tipos de dados retornados de objetos de extensão é um dos quatro tipos de dados básicos XPath número, cadeia de caracteres, conjunto booleano, e o nó.</span><span class="sxs-lookup"><span data-stu-id="2a88d-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="2a88d-161">Para usar o objeto de extensão XSLT, o usuário precisará fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2a88d-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="2a88d-162">Crie <xref:System.Xml.Xsl.XsltArgumentList> e adicione o objeto de extensão usando <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a88d-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="2a88d-163">Chamar o objeto de extensão folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="2a88d-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="2a88d-164">Passar <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="2a88d-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2a88d-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a88d-165">Example</span></span>  
 <span data-ttu-id="2a88d-166">O exemplo a seguir calcula a circunferência de um círculo determinado o raio.</span><span class="sxs-lookup"><span data-stu-id="2a88d-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="2a88d-167">Entrada</span><span class="sxs-lookup"><span data-stu-id="2a88d-167">Input</span></span>  
 <span data-ttu-id="2a88d-168">number.xml</span><span class="sxs-lookup"><span data-stu-id="2a88d-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 <span data-ttu-id="2a88d-169">circle.xsl</span><span class="sxs-lookup"><span data-stu-id="2a88d-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="2a88d-170">Saída</span><span class="sxs-lookup"><span data-stu-id="2a88d-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="2a88d-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a88d-171">See also</span></span>

- [<span data-ttu-id="2a88d-172">A classe XslTransform implementa o processador XSLT</span><span class="sxs-lookup"><span data-stu-id="2a88d-172">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
