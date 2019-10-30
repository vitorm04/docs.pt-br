---
title: Mapear restrições de esquema XML (XSD) chave para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 670c07dd83e880b79c1ccf0c5af00d253b83f827
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040074"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="fd3ab-102">Mapear restrições de esquema XML (XSD) chave para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="fd3ab-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="fd3ab-103">Em um esquema, você pode especificar uma restrição de chave em um elemento ou atributo usando o elemento de **chave** .</span><span class="sxs-lookup"><span data-stu-id="fd3ab-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="fd3ab-104">O elemento ou atributo no qual uma restrição de chave é especificada deve ter valores exclusivos em qualquer instância de esquema e não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="fd3ab-105">A restrição de chave é semelhante à restrição UNIQUE, exceto que a coluna na qual uma restrição de chave é definida não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="fd3ab-106">A tabela a seguir descreve os atributos **MSDATA** que você pode especificar no elemento **Key** .</span><span class="sxs-lookup"><span data-stu-id="fd3ab-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="fd3ab-107">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="fd3ab-107">Attribute name</span></span>|<span data-ttu-id="fd3ab-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd3ab-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fd3ab-109">**MSDATA: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="fd3ab-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="fd3ab-110">Se esse atributo for especificado, seu valor será usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="fd3ab-111">Caso contrário, o atributo **Name** fornecerá o valor do nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="fd3ab-112">**MSDATA: PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="fd3ab-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="fd3ab-113">Se `PrimaryKey="true"` estiver presente, a propriedade **IsPrimaryKey** de restrição será definida como **true**, tornando-a uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="fd3ab-114">A propriedade de coluna **AllowDBNull** está definida como **false**, pois as chaves primárias não podem ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="fd3ab-115">Na conversão do esquema no qual uma restrição de chave é especificada, o processo de mapeamento cria uma restrição UNIQUE na tabela com a propriedade de coluna **AllowDBNull** definida como **false** para cada coluna na restrição.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="fd3ab-116">A propriedade **IsPrimaryKey** da restrição UNIQUE também é definida como **false** , a menos que você tenha especificado `msdata:PrimaryKey="true"` no elemento **Key** .</span><span class="sxs-lookup"><span data-stu-id="fd3ab-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="fd3ab-117">Isso é idêntico a uma restrição UNIQUE no esquema no qual `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="fd3ab-118">No exemplo de esquema a seguir, o elemento **Key** especifica a restrição de chave no elemento **CustomerID** .</span><span class="sxs-lookup"><span data-stu-id="fd3ab-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="fd3ab-119">O elemento **Key** especifica que os valores do elemento filho **CustomerID** do elemento **Customers** devem ter valores exclusivos e não podem ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="fd3ab-120">Ao traduzir o esquema XSD (linguagem de definição de esquema XML), o processo de mapeamento cria a seguinte tabela:</span><span class="sxs-lookup"><span data-stu-id="fd3ab-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="fd3ab-121">O mapeamento de esquema XML também cria um **UniqueConstraint** na coluna **CustomerID** , conforme mostrado na <xref:System.Data.DataSet>a seguir.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="fd3ab-122">(Para simplificar, apenas as propriedades relevantes são mostradas.)</span><span class="sxs-lookup"><span data-stu-id="fd3ab-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="fd3ab-123">No **conjunto** de um que é gerado, a propriedade **IsPrimaryKey** de **UniqueConstraint** é definida como **true** porque o esquema especifica `msdata:PrimaryKey="true"` no elemento **Key** .</span><span class="sxs-lookup"><span data-stu-id="fd3ab-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="fd3ab-124">O valor da propriedade **ConstraintName** do **UniqueConstraint** no **conjunto** de valores é o valor do atributo **MSDATA: ConstraintName** especificado no elemento **Key** no esquema.</span><span class="sxs-lookup"><span data-stu-id="fd3ab-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3ab-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd3ab-125">See also</span></span>

- [<span data-ttu-id="fd3ab-126">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="fd3ab-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="fd3ab-127">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fd3ab-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="fd3ab-128">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="fd3ab-128">[ADO.NET Overview](../ado-net-overview.md)</span></span>
