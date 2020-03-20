---
title: Derivando a estrutura relacional do DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151163"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="fc065-102">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fc065-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="fc065-103">Esta seção fornece uma visão geral de como o esquema relacional de um `DataSet` é compilado a partir de um documento de esquema XSD (linguagem de definição de esquema XML).</span><span class="sxs-lookup"><span data-stu-id="fc065-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="fc065-104">Em geral, `complexType` para cada elemento filho de um elemento de `DataSet`esquema, uma tabela é gerada no .</span><span class="sxs-lookup"><span data-stu-id="fc065-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="fc065-105">A estrutura da tabela é determinada pela definição do tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="fc065-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="fc065-106">As tabelas são `DataSet` criadas no para elementos de nível superior no esquema.</span><span class="sxs-lookup"><span data-stu-id="fc065-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="fc065-107">No entanto, uma tabela só é `complexType` criada `complexType` para um elemento `complexType` de nível superior quando `complexType` o elemento está `DataTable` aninhado dentro de outro elemento, nesse caso o elemento aninhado é mapeado para um dentro do `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="fc065-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="fc065-108">Para obter mais informações sobre o XSD, consulte o World Wide Web Consortium (W3C) [XML Schema Parte 0: Recomendação de Primer,](https://www.w3.org/TR/xmlschema-0/)o [Esquema XML Parte 1: Recomendação de Estruturas](https://www.w3.org/TR/xmlschema-1/)e o Esquema [XML Parte 2: Recomendação de Tipos de Dados](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="fc065-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="fc065-109">O exemplo a seguir demonstra um `customers` Esquema XML `MyDataSet` onde está o elemento filho do elemento, que é um elemento **DataSet.**</span><span class="sxs-lookup"><span data-stu-id="fc065-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="fc065-110">No exemplo anterior, o elemento `customers` é um elemento de tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="fc065-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="fc065-111">Portanto, o definição de tipo complexo é analisada, e o processo de mapeamento cria a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="fc065-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="fc065-112">O tipo de dados de cada coluna na tabela é derivado do tipo do Esquema XML do elemento ou atributo correspondente especificado.</span><span class="sxs-lookup"><span data-stu-id="fc065-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc065-113">Se o `customers` elemento for de um simples tipo de dados XML Schema, como **inteiro,** nenhuma tabela será gerada.</span><span class="sxs-lookup"><span data-stu-id="fc065-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="fc065-114">As tabelas são criadas apenas para os elementos de nível superior que são tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="fc065-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="fc065-115">No seguinte Esquema XML, o elemento **Schema** tem `InStateCustomers` `OutOfStateCustomers`dois filhos elementos, e .</span><span class="sxs-lookup"><span data-stu-id="fc065-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="fc065-116">Os elementos filho `InStateCustomers` e `OutOfStateCustomers` são ambos elementos de tipo complexo (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="fc065-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="fc065-117">Portanto, o processo de mapeamento gera as `DataSet`seguintes duas tabelas idênticas no .</span><span class="sxs-lookup"><span data-stu-id="fc065-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="fc065-118">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fc065-118">In This Section</span></span>  
 [<span data-ttu-id="fc065-119">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="fc065-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fc065-120">Descreve os elementos de esquema XML usados para criar `DataSet`restrições de chave únicas e estrangeiras em um .</span><span class="sxs-lookup"><span data-stu-id="fc065-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="fc065-121">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fc065-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="fc065-122">Descreve os elementos de esquema XML usados para `DataSet`criar relações entre colunas de tabela em um .</span><span class="sxs-lookup"><span data-stu-id="fc065-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="fc065-123">Relações e restrições de esquema XML</span><span class="sxs-lookup"><span data-stu-id="fc065-123">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="fc065-124">Descreve como as relações são criadas implicitamente ao usar elementos `DataSet`do Esquema XML para criar restrições em um .</span><span class="sxs-lookup"><span data-stu-id="fc065-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fc065-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="fc065-125">Related Sections</span></span>  
 <span data-ttu-id="fc065-126">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="fc065-126">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="fc065-127">Descreve como carregar e persistir a estrutura relacional e os dados em dados `DataSet` XML.</span><span class="sxs-lookup"><span data-stu-id="fc065-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc065-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc065-128">See also</span></span>

- [<span data-ttu-id="fc065-129">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fc065-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
