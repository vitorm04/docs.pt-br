---
title: Restrições de esquema XML (XSD) às restrições de conjunto de dados de chave de mapa
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: ad39fd75a3f8872ed2c24a65481209e3c772a638
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757860"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="ddfac-102">Restrições de esquema XML (XSD) às restrições de conjunto de dados de chave de mapa</span><span class="sxs-lookup"><span data-stu-id="ddfac-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="ddfac-103">Em um esquema, você pode especificar uma restrição de chave em um elemento ou atributo usando o **chave** elemento.</span><span class="sxs-lookup"><span data-stu-id="ddfac-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="ddfac-104">O elemento ou atributo no qual uma restrição de chave for especificada deve ter valores exclusivos em qualquer instância do esquema e não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ddfac-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="ddfac-105">A restrição de chave é semelhante a restrição unique, exceto que a coluna na qual é definida uma restrição de chave não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ddfac-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="ddfac-106">A tabela a seguir descreve o **msdata** atributos que você pode especificar o **chave** elemento.</span><span class="sxs-lookup"><span data-stu-id="ddfac-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="ddfac-107">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="ddfac-107">Attribute name</span></span>|<span data-ttu-id="ddfac-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddfac-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ddfac-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="ddfac-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="ddfac-110">Se esse atributo for especificado, seu valor é usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="ddfac-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="ddfac-111">Caso contrário, o **nome** atributo fornece o valor do nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="ddfac-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="ddfac-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="ddfac-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="ddfac-113">Se `PrimaryKey="true"` estiver presente, o **IsPrimaryKey** restrição está definida como **true**, tornando uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="ddfac-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="ddfac-114">O **AllowDBNull** coluna está definida como **false**, porque as chaves primárias não podem ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ddfac-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="ddfac-115">Na conversão do esquema no qual uma restrição de chave for especificada, o processo de mapeamento cria uma restrição exclusiva na tabela com o **AllowDBNull** propriedade column definida como **false** para cada coluna a restrição.</span><span class="sxs-lookup"><span data-stu-id="ddfac-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="ddfac-116">O **IsPrimaryKey** propriedade da restrição unique também é definida como **false** , a menos que você especificou `msdata:PrimaryKey="true"` no **chave** elemento.</span><span class="sxs-lookup"><span data-stu-id="ddfac-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="ddfac-117">Isso é idêntico de uma restrição exclusiva no esquema no qual `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="ddfac-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="ddfac-118">No exemplo de esquema a seguir, o **chave** elemento Especifica a restrição de chave no **CustomerID** elemento.</span><span class="sxs-lookup"><span data-stu-id="ddfac-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="ddfac-119">O **chave** elemento Especifica que os valores da **CustomerID** elemento filho do **clientes** elemento deve ter valores exclusivos e não pode ter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ddfac-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="ddfac-120">Converter o esquema de linguagem XSD de definição de esquema XML, o processo de mapeamento cria a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="ddfac-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="ddfac-121">O mapeamento de esquema XML também cria um **UniqueConstraint** no **CustomerID** coluna, conforme mostrado no exemplo a seguir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ddfac-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ddfac-122">(Para manter a simplicidade, somente as propriedades relevantes são mostradas.)</span><span class="sxs-lookup"><span data-stu-id="ddfac-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
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
  
 <span data-ttu-id="ddfac-123">No **conjunto de dados** que é gerado, o **IsPrimaryKey** propriedade o **UniqueConstraint** é definido como **true** porque o esquema Especifica `msdata:PrimaryKey="true"` no **chave** elemento.</span><span class="sxs-lookup"><span data-stu-id="ddfac-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="ddfac-124">O valor da **ConstraintName** propriedade do **UniqueConstraint** no **conjunto de dados** é o valor da **msdata:ConstraintName** o atributo especificado no **chave** elemento no esquema.</span><span class="sxs-lookup"><span data-stu-id="ddfac-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfac-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddfac-125">See Also</span></span>  
 [<span data-ttu-id="ddfac-126">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="ddfac-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="ddfac-127">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ddfac-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="ddfac-128">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ddfac-128">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
