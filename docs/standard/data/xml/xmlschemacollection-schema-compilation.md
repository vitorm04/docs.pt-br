---
title: "Compilação do esquema de XmlSchemaCollection"
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
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="2e992-102">Compilação do esquema de XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2e992-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="2e992-103">O **XmlSchemaCollection** é um cache ou a biblioteca onde os esquemas de linguagem XSD de definição de XML-Data Reduced (XDR) e o esquema XML podem ser armazenados e validados.</span><span class="sxs-lookup"><span data-stu-id="2e992-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="2e992-104">**XmlSchemaCollection** melhora o desempenho armazenando em cache de esquemas na memória, em vez de acessá-los de um arquivo ou URL.</span><span class="sxs-lookup"><span data-stu-id="2e992-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e992-105">Embora o **XmlSchemaCollection** classe armazena os esquemas XDR e esquemas XML, qualquer método e a propriedade que utiliza ou retorna um **XmlSchema** objeto oferece suporte a esquemas XML apenas.</span><span class="sxs-lookup"><span data-stu-id="2e992-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e992-106">A classe <xref:System.Xml.Schema.XmlSchemaCollection> agora está obsoleta e foi substituída pela classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="2e992-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="2e992-107">Para obter mais informações sobre o <xref:System.Xml.Schema.XmlSchemaSet> , consulte classe [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="2e992-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="2e992-108">Adicionar à coleção esquemas</span><span class="sxs-lookup"><span data-stu-id="2e992-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="2e992-109">Os esquemas são carregados para a coleção usando o **adicionar** método **XmlSchemaCollection**, momento em que o esquema está associado um URI de namespace.</span><span class="sxs-lookup"><span data-stu-id="2e992-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="2e992-110">Para esquemas XML, URI do namespace será normalmente o namespace de destino para o esquema.</span><span class="sxs-lookup"><span data-stu-id="2e992-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="2e992-111">Para esquemas XDR, o URI de namespace é namespace especificado quando o esquema foi adicionado à coleção.</span><span class="sxs-lookup"><span data-stu-id="2e992-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="2e992-112">Verificação para um esquema na coleção</span><span class="sxs-lookup"><span data-stu-id="2e992-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="2e992-113">Você pode verificar se um esquema está na coleção usando o **contém** método.</span><span class="sxs-lookup"><span data-stu-id="2e992-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="2e992-114">O **contém** método aceita um **XmlSchema** objeto (para esquemas XML só) ou uma cadeia de caracteres que representa o URI de namespace associado com o esquema (esquemas XDR e de esquemas XML).</span><span class="sxs-lookup"><span data-stu-id="2e992-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="2e992-115">Recuperar um esquema de coleção</span><span class="sxs-lookup"><span data-stu-id="2e992-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="2e992-116">Você pode recuperar um esquema da coleção usando o **Item** propriedade.</span><span class="sxs-lookup"><span data-stu-id="2e992-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="2e992-117">O **Item** propriedade usa uma cadeia de caracteres que representa o namespace URI associada ao esquema, normalmente é o namespace de destino e retorna um **XmlSchema** objeto.</span><span class="sxs-lookup"><span data-stu-id="2e992-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="2e992-118">O **Item** propriedade se aplica somente aos esquemas XML.</span><span class="sxs-lookup"><span data-stu-id="2e992-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="2e992-119">O valor de retorno é sempre uma referência nula para esquemas XDR porque eles não têm um modelo de objeto disponível.</span><span class="sxs-lookup"><span data-stu-id="2e992-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="2e992-120">Validar documentos XML usando XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2e992-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="2e992-121">Você pode validar um documento de instância XML usando um **XmlSchemaCollection** criando o **XmlSchemaCollection** objeto, adicionando os esquemas na coleção e definindo o **esquemas**  propriedade o **XmlValidatingReader** para atribuir o criado **XmlSchemaCollection** para o **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="2e992-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="2e992-122">Desempenho aprimorado</span><span class="sxs-lookup"><span data-stu-id="2e992-122">Improved Performance</span></span>  
 <span data-ttu-id="2e992-123">É recomendável, se você estiver validando mais de um documento com o mesmo esquema, que você use o **XmlSchemaCollection** porque ele fornece um melhor desempenho fazendo o cache de esquemas na memória.</span><span class="sxs-lookup"><span data-stu-id="2e992-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="2e992-124">O exemplo de código a seguir cria o **XmlSchemaCollection** objeto, adiciona a coleção de esquemas e define o **esquemas** propriedade.</span><span class="sxs-lookup"><span data-stu-id="2e992-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e992-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e992-125">See Also</span></span>  
 [<span data-ttu-id="2e992-126">Validação de XDR com XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2e992-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="2e992-127">Validação de esquema (XSD) XML com XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="2e992-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
