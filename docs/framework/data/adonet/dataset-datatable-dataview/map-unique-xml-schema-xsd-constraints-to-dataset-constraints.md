---
title: Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 6c1c4607704e092cc1c12108a455bf3076415882
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485671"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="a6663-102">Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="a6663-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="a6663-103">Em um esquema XSD (linguagem) de definição de esquema XML, o **exclusivo** elemento Especifica a restrição de exclusividade em um elemento ou atributo.</span><span class="sxs-lookup"><span data-stu-id="a6663-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="a6663-104">No processo de conversão de um esquema XML em um esquema relacional, a restrição unique especificada em um elemento ou atributo no esquema XML é mapeada para uma restrição exclusiva na <xref:System.Data.DataTable> nas correspondentes <xref:System.Data.DataSet> que é gerado.</span><span class="sxs-lookup"><span data-stu-id="a6663-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="a6663-105">A tabela a seguir descreve o **msdata** atributos que você pode especificar o **exclusivo** elemento.</span><span class="sxs-lookup"><span data-stu-id="a6663-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="a6663-106">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="a6663-106">Attribute name</span></span>|<span data-ttu-id="a6663-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6663-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a6663-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="a6663-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="a6663-109">Se esse atributo for especificado, seu valor é usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="a6663-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="a6663-110">Caso contrário, o **nome** atributo fornece o valor do nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="a6663-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="a6663-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="a6663-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="a6663-112">Se `PrimaryKey="true"` está presente na **exclusivo** elemento, uma restrição exclusiva é criada com o **IsPrimaryKey** propriedade definida como **true**.</span><span class="sxs-lookup"><span data-stu-id="a6663-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="a6663-113">O exemplo a seguir mostra um esquema XML que usa o **exclusivo** elemento para especificar uma restrição de exclusividade.</span><span class="sxs-lookup"><span data-stu-id="a6663-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="a6663-114">O **exclusivos** elemento no esquema Especifica que, para todos os **clientes** elementos em um documento de instância, o valor da **CustomerID** elemento filho deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="a6663-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="a6663-115">Na construção do **conjunto de dados**, o processo de mapeamento lê esse esquema e gera a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="a6663-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="a6663-116">O processo de mapeamento também cria uma restrição exclusiva na **CustomerID** coluna, conforme mostrado no seguinte **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="a6663-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="a6663-117">(Para simplificar, somente as propriedades relevantes são exibidas.)</span><span class="sxs-lookup"><span data-stu-id="a6663-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="a6663-118">No **DataSet** que é gerado, o **IsPrimaryKey** estiver definida como **False** para a restrição exclusiva.</span><span class="sxs-lookup"><span data-stu-id="a6663-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="a6663-119">O **exclusivos** propriedade na coluna indica que o **CustomerID** valores de coluna devem ser exclusivos (mas podem ser uma referência nula, conforme especificado pelo **AllowDBNull** propriedade da coluna).</span><span class="sxs-lookup"><span data-stu-id="a6663-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="a6663-120">Se você modificar o esquema e defina o cabeçalho opcional **msdata:PrimaryKey** valor ao atributo **verdadeiro**, a restrição exclusiva será criada na tabela.</span><span class="sxs-lookup"><span data-stu-id="a6663-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="a6663-121">O **AllowDBNull** coluna estiver definida como **falso**e o **IsPrimaryKey** propriedade da restrição definida como **True**, tornando assim o **CustomerID** coluna uma coluna de chave primária.</span><span class="sxs-lookup"><span data-stu-id="a6663-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="a6663-122">Você pode especificar uma restrição exclusiva em uma combinação de elementos ou atributos no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="a6663-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="a6663-123">O exemplo a seguir demonstra como especificar que uma combinação de **CustomerID** e **CompanyName** valores devem ser exclusivos para todos os **clientes** em qualquer instância por Adicionar outra **xs:field** elemento no esquema.</span><span class="sxs-lookup"><span data-stu-id="a6663-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="a6663-124">Essa é a restrição que é criada no resultante **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="a6663-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6663-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6663-125">See Also</span></span>  
 [<span data-ttu-id="a6663-126">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="a6663-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="a6663-127">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a6663-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="a6663-128">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a6663-128">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
