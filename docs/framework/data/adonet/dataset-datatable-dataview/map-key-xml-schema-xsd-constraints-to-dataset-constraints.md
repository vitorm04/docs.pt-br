---
title: Mapear restrições de esquema XML (XSD) chave para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150929"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="67dbf-102">Mapear restrições de esquema XML (XSD) chave para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="67dbf-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="67dbf-103">Em um esquema, você pode especificar uma restrição de chave em um elemento ou atributo usando o **elemento-chave.**</span><span class="sxs-lookup"><span data-stu-id="67dbf-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="67dbf-104">O elemento ou atributo no qual uma restrição de chave é especificada deve ter valores únicos em qualquer instância de esquema e não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="67dbf-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="67dbf-105">A restrição de chave é semelhante à restrição única, exceto que a coluna na qual uma restrição de chave é definida não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="67dbf-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="67dbf-106">A tabela a seguir descreve os **atributos msdata** que você pode especificar no **elemento-chave.**</span><span class="sxs-lookup"><span data-stu-id="67dbf-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="67dbf-107">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="67dbf-107">Attribute name</span></span>|<span data-ttu-id="67dbf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="67dbf-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="67dbf-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="67dbf-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="67dbf-110">Se este atributo for especificado, seu valor será usado como nome de restrição.</span><span class="sxs-lookup"><span data-stu-id="67dbf-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="67dbf-111">Caso contrário, o atributo **nome** fornece o valor do nome de restrição.</span><span class="sxs-lookup"><span data-stu-id="67dbf-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="67dbf-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="67dbf-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="67dbf-113">Se `PrimaryKey="true"` estiver presente, a propriedade de restrição **IsPrimaryKey** é definida como **true,** tornando-a uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="67dbf-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="67dbf-114">A propriedade Da coluna **AllowDBNull** é definida como **falsa,** porque as chaves primárias não podem ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="67dbf-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="67dbf-115">Ao converter esquema no qual uma restrição de chave é especificada, o processo de mapeamento cria uma restrição única na tabela com a propriedade da coluna **AllowDBNull** definida como **falsa** para cada coluna na restrição.</span><span class="sxs-lookup"><span data-stu-id="67dbf-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="67dbf-116">A propriedade **IsPrimaryKey** da restrição exclusiva também é definida `msdata:PrimaryKey="true"` como **falsa,** a menos que você tenha especificado no **elemento-chave.**</span><span class="sxs-lookup"><span data-stu-id="67dbf-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="67dbf-117">Isto é idêntico a uma restrição única `PrimaryKey="true"`no esquema em que .</span><span class="sxs-lookup"><span data-stu-id="67dbf-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="67dbf-118">No exemplo do esquema a seguir, o **elemento-chave** especifica a restrição de chave no elemento **CustomerID.**</span><span class="sxs-lookup"><span data-stu-id="67dbf-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="67dbf-119">O **elemento-chave** especifica que os valores do elemento filho **CustomerID** do elemento **Clientes** devem ter valores únicos e não podem ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="67dbf-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="67dbf-120">Ao traduzir o esquema de definição de Esquema XML (XSD), o processo de mapeamento cria a seguinte tabela:</span><span class="sxs-lookup"><span data-stu-id="67dbf-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="67dbf-121">O mapeamento xml schema também cria uma **Restrição Única** na coluna <xref:System.Data.DataSet> **CustomerID,** como mostrado no seguinte .</span><span class="sxs-lookup"><span data-stu-id="67dbf-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="67dbf-122">(Para simplificar, apenas propriedades relevantes são mostradas.)</span><span class="sxs-lookup"><span data-stu-id="67dbf-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="67dbf-123">No **Conjunto de Dados** gerado, a propriedade **IsPrimaryKey** da **UniqueConstraint** é definida `msdata:PrimaryKey="true"` como **true** porque o esquema especifica no **elemento-chave.**</span><span class="sxs-lookup"><span data-stu-id="67dbf-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="67dbf-124">O valor da propriedade **ConstraintName** da **UniqueConstraint** no **DataSet** é o valor do atributo **msdata:ConstraintName** especificado no **elemento-chave** no esquema.</span><span class="sxs-lookup"><span data-stu-id="67dbf-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67dbf-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="67dbf-125">See also</span></span>

- [<span data-ttu-id="67dbf-126">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="67dbf-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="67dbf-127">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="67dbf-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="67dbf-128">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="67dbf-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
