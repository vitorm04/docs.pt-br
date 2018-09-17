---
title: Lendo e gravando esquemas XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 241ff40448c3dca2846f9e420dc7df41427dc79d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45592225"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="289fd-102">Lendo e gravando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="289fd-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="289fd-103">A API do SOM (Schema Object Model) pode ser usada para ler e gravar esquemas XSD de arquivos ou de outras origens e criar esquemas XML na memória usando as classes no namespace <xref:System.Xml.Schema?displayProperty=nameWithType> que mapeiam para as estruturas definidas na Recomendação de esquema XML do W3C (World Wide Web Consortium).</span><span class="sxs-lookup"><span data-stu-id="289fd-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="289fd-104">Lendo e gravando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="289fd-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="289fd-105">A classe <xref:System.Xml.Schema.XmlSchema> fornece os métodos <xref:System.Xml.Schema.XmlSchema.Read%2A> e <xref:System.Xml.Schema.XmlSchema.Write%2A> para ler e gravar esquemas XML.</span><span class="sxs-lookup"><span data-stu-id="289fd-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="289fd-106">O método <xref:System.Xml.Schema.XmlSchema.Read%2A> retorna um objeto <xref:System.Xml.Schema.XmlSchema> que representa o esquema XML e utiliza um <xref:System.Xml.Schema.ValidationEventHandler> opcional como um parâmetro para tratar avisos e erros de validação de esquema encontrados ao ler um esquema XML.</span><span class="sxs-lookup"><span data-stu-id="289fd-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="289fd-107">O método <xref:System.Xml.Schema.XmlSchema.Write%2A> grava esquemas XML nos objetos <xref:System.IO.Stream>, <xref:System.IO.TextWriter> e <xref:System.Xml.XmlWriter> e pode utilizar um objeto opcional <xref:System.Xml.XmlNamespaceManager> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="289fd-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="289fd-108">Um <xref:System.Xml.XmlNamespaceManager> é usado para tratar namespaces encontrados em um esquema XML.</span><span class="sxs-lookup"><span data-stu-id="289fd-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="289fd-109">Para saber mais sobre a classe <xref:System.Xml.XmlNamespaceManager>, confira [Gerenciando namespaces em um documento XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="289fd-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="289fd-110">O exemplo de código a seguir ilustra esquemas XML de leitura e gravação de um arquivo e para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="289fd-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="289fd-111">O exemplo de código utiliza o arquivo `example.xsd`, lê-o em um objeto <xref:System.Xml.Schema.XmlSchema> usando o método `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> e, em seguida, grava o arquivo no console e em um novo arquivo `new.xsd`.</span><span class="sxs-lookup"><span data-stu-id="289fd-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="289fd-112">O exemplo de código também fornece <xref:System.Xml.Schema.ValidationEventHandler> como um parâmetro para o método `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> para tratar todos os avisos ou erros de validação de esquema encontrados ao ler o esquema XML.</span><span class="sxs-lookup"><span data-stu-id="289fd-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="289fd-113">Se o <xref:System.Xml.Schema.ValidationEventHandler> não for especificado (`null`), nenhum aviso ou erro será relatado.</span><span class="sxs-lookup"><span data-stu-id="289fd-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="289fd-114">O exemplo utiliza o arquivo `example.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="289fd-114">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="289fd-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="289fd-115">See also</span></span>

- [<span data-ttu-id="289fd-116">Visão geral de modelo de objeto de esquema XML</span><span class="sxs-lookup"><span data-stu-id="289fd-116">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [<span data-ttu-id="289fd-117">Compilando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="289fd-117">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
- [<span data-ttu-id="289fd-118">Percorrer esquemas XML</span><span class="sxs-lookup"><span data-stu-id="289fd-118">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [<span data-ttu-id="289fd-119">Edição de esquemas XML</span><span class="sxs-lookup"><span data-stu-id="289fd-119">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [<span data-ttu-id="289fd-120">Incluindo ou importando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="289fd-120">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [<span data-ttu-id="289fd-121">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="289fd-121">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [<span data-ttu-id="289fd-122">Infoset de compilação pós-esquema</span><span class="sxs-lookup"><span data-stu-id="289fd-122">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
- <span data-ttu-id="289fd-123">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md) (Gerenciando namespaces em um documento XML)</span><span class="sxs-lookup"><span data-stu-id="289fd-123">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span></span>
