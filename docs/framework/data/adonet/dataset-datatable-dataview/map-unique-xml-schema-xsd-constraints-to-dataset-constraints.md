---
title: Mapear de restrições de esquema XML (XSD) exclusivas para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 231f23ccf47f60b902fdd5c66b63fe1a750445f9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203420"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="2d799-102">Mapear de restrições de esquema XML (XSD) exclusivas para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="2d799-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="2d799-103">Em um esquema XSD (linguagem de definição de esquema XML), o elemento **exclusivo** especifica a restrição de exclusividade em um elemento ou atributo.</span><span class="sxs-lookup"><span data-stu-id="2d799-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="2d799-104">No processo de tradução de um esquema XML em um esquema relacional, a restrição UNIQUE especificada em um elemento ou atributo no esquema XML é mapeada para uma restrição UNIQUE no <xref:System.Data.DataTable> no correspondente <xref:System.Data.DataSet> que é gerado.</span><span class="sxs-lookup"><span data-stu-id="2d799-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="2d799-105">A tabela a seguir descreve os atributos **MSDATA** que você pode especificar no elemento **Unique** .</span><span class="sxs-lookup"><span data-stu-id="2d799-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="2d799-106">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="2d799-106">Attribute name</span></span>|<span data-ttu-id="2d799-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d799-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2d799-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="2d799-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="2d799-109">Se esse atributo for especificado, seu valor será usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="2d799-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="2d799-110">Caso contrário, o atributo **Name** fornecerá o valor do nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="2d799-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="2d799-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="2d799-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="2d799-112">Se `PrimaryKey="true"` estiver presente no elemento **Unique** , uma restrição UNIQUE será criada com a propriedade **IsPrimaryKey** definida como **true**.</span><span class="sxs-lookup"><span data-stu-id="2d799-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="2d799-113">O exemplo a seguir mostra um esquema XML que usa o elemento **exclusivo** para especificar uma restrição de exclusividade.</span><span class="sxs-lookup"><span data-stu-id="2d799-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="2d799-114">O elemento **exclusivo** no esquema especifica que para todos os elementos **Customers** em uma instância de documento, o valor do elemento filho **CustomerID** deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="2d799-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="2d799-115">Ao criar o **conjunto**de um, o processo de mapeamento lê esse esquema e gera a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d799-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="2d799-116">O processo de mapeamento também cria uma restrição UNIQUE na coluna **CustomerID** , conforme mostrado no **conjunto**de acordo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d799-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="2d799-117">(Para simplificar, apenas as propriedades relevantes são mostradas.)</span><span class="sxs-lookup"><span data-stu-id="2d799-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="2d799-118">No **conjunto** de um que é gerado, a propriedade IsPrimaryKey é definida como **false** para a restrição UNIQUE.</span><span class="sxs-lookup"><span data-stu-id="2d799-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="2d799-119">A propriedade **Unique** na coluna indica que os valores de coluna **CustomerID** devem ser exclusivos (mas podem ser uma referência nula, conforme especificado pela propriedade **AllowDBNull** da coluna).</span><span class="sxs-lookup"><span data-stu-id="2d799-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="2d799-120">Se você modificar o esquema e definir o valor de atributo opcional **MSDATA: PrimaryKey** como **true**, a restrição UNIQUE será criada na tabela.</span><span class="sxs-lookup"><span data-stu-id="2d799-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="2d799-121">A propriedade de coluna **AllowDBNull** é definida **como false**e a Propriedade IsPrimaryKey da restrição definida como **true**, tornando a coluna **CustomerID** uma coluna de chave primária.</span><span class="sxs-lookup"><span data-stu-id="2d799-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="2d799-122">Você pode especificar uma restrição UNIQUE em uma combinação de elementos ou atributos no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="2d799-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="2d799-123">O exemplo a seguir demonstra como especificar que uma combinação de **CustomerID** e valores **CompanyName** deve ser exclusiva para todos os **clientes** em qualquer instância, adicionando outro elemento **xs: Field** no esquema.</span><span class="sxs-lookup"><span data-stu-id="2d799-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="2d799-124">Essa é a restrição que é criada no **conjunto**de resultados resultante.</span><span class="sxs-lookup"><span data-stu-id="2d799-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d799-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d799-125">See also</span></span>

- [<span data-ttu-id="2d799-126">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="2d799-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="2d799-127">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2d799-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="2d799-128">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2d799-128">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
