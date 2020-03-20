---
title: Mapear de restrições de esquema XML (XSD) exclusivas para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150838"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="f93d8-102">Mapear de restrições de esquema XML (XSD) exclusivas para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="f93d8-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="f93d8-103">Em um esquema de definição de Esquema XML (XSD), o elemento **único** especifica a restrição de exclusividade em um elemento ou atributo.</span><span class="sxs-lookup"><span data-stu-id="f93d8-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="f93d8-104">No processo de tradução de um Esquema XML em um esquema relacional, a restrição única especificada em um elemento ou atributo <xref:System.Data.DataTable> no <xref:System.Data.DataSet> Esquema XML é mapeada para uma restrição única no correspondente gerado.</span><span class="sxs-lookup"><span data-stu-id="f93d8-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="f93d8-105">A tabela a seguir descreve os **atributos msdata** que você pode especificar no elemento **único.**</span><span class="sxs-lookup"><span data-stu-id="f93d8-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="f93d8-106">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="f93d8-106">Attribute name</span></span>|<span data-ttu-id="f93d8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f93d8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f93d8-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="f93d8-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="f93d8-109">Se este atributo for especificado, seu valor será usado como nome de restrição.</span><span class="sxs-lookup"><span data-stu-id="f93d8-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="f93d8-110">Caso contrário, o atributo **nome** fornece o valor do nome de restrição.</span><span class="sxs-lookup"><span data-stu-id="f93d8-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="f93d8-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="f93d8-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="f93d8-112">Se `PrimaryKey="true"` estiver presente no elemento **único,** uma restrição única será criada com a propriedade **IsPrimaryKey** definida como **true**.</span><span class="sxs-lookup"><span data-stu-id="f93d8-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="f93d8-113">O exemplo a seguir mostra um Esquema XML que usa o elemento **exclusivo** para especificar uma restrição de exclusividade.</span><span class="sxs-lookup"><span data-stu-id="f93d8-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="f93d8-114">O elemento **único** no esquema especifica que, para todos os elementos **clientes** em uma instância de documento, o valor do elemento filho **CustomerID** deve ser único.</span><span class="sxs-lookup"><span data-stu-id="f93d8-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="f93d8-115">Na construção do **DataSet,** o processo de mapeamento lê este esquema e gera a seguinte tabela:</span><span class="sxs-lookup"><span data-stu-id="f93d8-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="f93d8-116">O processo de mapeamento também cria uma restrição única na coluna **CustomerID,** como mostrado no **Conjunto de Dados**a seguir .</span><span class="sxs-lookup"><span data-stu-id="f93d8-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="f93d8-117">(Para simplificar, apenas propriedades relevantes são mostradas.)</span><span class="sxs-lookup"><span data-stu-id="f93d8-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
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
  
 <span data-ttu-id="f93d8-118">No **Conjunto de dados** gerado, a propriedade **IsPrimaryKey** é definida como **False** para a restrição única.</span><span class="sxs-lookup"><span data-stu-id="f93d8-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="f93d8-119">A propriedade **única** na coluna indica que os valores da coluna **CustomerID** devem ser únicos (mas podem ser uma referência nula, conforme especificado pela propriedade **AllowDBNull** da coluna).</span><span class="sxs-lookup"><span data-stu-id="f93d8-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="f93d8-120">Se você modificar o esquema e definir o valor de atributo **msdata:PrimaryKey** para **True,** a restrição única será criada na tabela.</span><span class="sxs-lookup"><span data-stu-id="f93d8-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="f93d8-121">A propriedade da coluna **AllowDBNull** está definida como **False**, e a propriedade **IsPrimaryKey** da restrição definida como **True,** tornando assim a coluna **CustomerID** uma coluna de chave primária.</span><span class="sxs-lookup"><span data-stu-id="f93d8-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="f93d8-122">Você pode especificar uma restrição única em uma combinação de elementos ou atributos no Esquema XML.</span><span class="sxs-lookup"><span data-stu-id="f93d8-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="f93d8-123">O exemplo a seguir demonstra como especificar que uma combinação de valores **De CustomerID** e **CompanyName** deve ser única para todos **os Clientes** em qualquer instância, adicionando outro elemento **xs:campo** no esquema.</span><span class="sxs-lookup"><span data-stu-id="f93d8-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="f93d8-124">Esta é a restrição criada no **Conjunto de Dados**resultante .</span><span class="sxs-lookup"><span data-stu-id="f93d8-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="f93d8-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="f93d8-125">See also</span></span>

- [<span data-ttu-id="f93d8-126">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="f93d8-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="f93d8-127">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f93d8-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="f93d8-128">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f93d8-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
