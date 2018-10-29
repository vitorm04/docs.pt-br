---
title: Compilação do esquema de XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6ea782020dde83aa7d59be8ec3058a27075ad
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48030662"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="b1774-102">Compilação do esquema de XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="b1774-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="b1774-103">**XmlSchemaCollection** é um cache ou uma biblioteca em que esquemas XDR (XML-Data Reduced) e XSD (XML Schema definition language) podem ser armazenados e validados.</span><span class="sxs-lookup"><span data-stu-id="b1774-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="b1774-104">**XmlSchemaCollection** melhora o desempenho armazenando em cache esquemas na memória em vez de acessá-los de um arquivo ou de uma URL.</span><span class="sxs-lookup"><span data-stu-id="b1774-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1774-105">Embora a classe de **XmlSchemaCollection** armazene esquemas XDR e XML, qualquer método e propriedade que receba ou retorne um objeto **XmlSchema** dá suporte somente a esquemas XML.</span><span class="sxs-lookup"><span data-stu-id="b1774-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1774-106">A classe <xref:System.Xml.Schema.XmlSchemaCollection> agora está obsoleta e foi substituída pela classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="b1774-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="b1774-107">Para saber mais sobre a classe <xref:System.Xml.Schema.XmlSchemaSet>, veja [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="b1774-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="b1774-108">Adicionar à coleção esquemas</span><span class="sxs-lookup"><span data-stu-id="b1774-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="b1774-109">Os esquemas são carregados na coleção usando o método **Add** de **XmlSchemaCollection**, quando o esquema é associado ao URI de um namespace.</span><span class="sxs-lookup"><span data-stu-id="b1774-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="b1774-110">Para esquemas XML, URI do namespace será normalmente o namespace de destino para o esquema.</span><span class="sxs-lookup"><span data-stu-id="b1774-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="b1774-111">Para esquemas XDR, o URI de namespace é namespace especificado quando o esquema foi adicionado à coleção.</span><span class="sxs-lookup"><span data-stu-id="b1774-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="b1774-112">Verificação para um esquema na coleção</span><span class="sxs-lookup"><span data-stu-id="b1774-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="b1774-113">Você pode verificar se um esquema está na coleção usando o método **Contains**.</span><span class="sxs-lookup"><span data-stu-id="b1774-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="b1774-114">O método **Contains** utiliza um objeto **XmlSchema** (somente para esquemas XML) ou uma cadeia de caracteres que representa o URI de namespace associado ao esquema (para esquemas XML e XDR).</span><span class="sxs-lookup"><span data-stu-id="b1774-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="b1774-115">Recuperar um esquema de coleção</span><span class="sxs-lookup"><span data-stu-id="b1774-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="b1774-116">Você pode recuperar um esquema de coleção usando a propriedade **Item**.</span><span class="sxs-lookup"><span data-stu-id="b1774-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="b1774-117">A propriedade **Item** usa uma cadeia de caracteres que representa o URI de namespace associado ao esquema, normalmente o namespace de destino, e retorna um objeto **XmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="b1774-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="b1774-118">A propriedade **Item** se aplica somente a esquemas XML.</span><span class="sxs-lookup"><span data-stu-id="b1774-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="b1774-119">O valor de retorno é sempre uma referência nula para esquemas XDR porque eles não têm um modelo de objeto disponível.</span><span class="sxs-lookup"><span data-stu-id="b1774-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="b1774-120">Validar documentos XML usando XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="b1774-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="b1774-121">Você pode validar um documento de instância de XML usando **XmlSchemaCollection** criando o objeto **XmlSchemaCollection**, adicionando seus esquemas à coleta e definindo a propriedade **Schemas** em **XmlValidatingReader** para atribuir o **XmlSchemaCollection** criado a **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="b1774-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="b1774-122">Desempenho aprimorado</span><span class="sxs-lookup"><span data-stu-id="b1774-122">Improved Performance</span></span>  
 <span data-ttu-id="b1774-123">Se você está validando mais de um documento com o mesmo esquema, é recomendável usar **XmlSchemaCollection**, pois fornece melhor desempenho armazenando em cache esquemas na memória.</span><span class="sxs-lookup"><span data-stu-id="b1774-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="b1774-124">O exemplo de código a seguir cria o objeto **XmlSchemaCollection**, adiciona esquemas à coleta e defina a propriedade **Schemas**.</span><span class="sxs-lookup"><span data-stu-id="b1774-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1774-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1774-125">See also</span></span>

- [<span data-ttu-id="b1774-126">Validação de XDR com XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="b1774-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
- [<span data-ttu-id="b1774-127">Validação de esquema XML (XSD) com XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="b1774-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
