---
title: Mapear keyref restrições de esquema XML (XSD) para restrições de conjunto de dados
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: a3a5033292db2b47e7a9811e36c0a4af016951fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758549"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="4690d-102">Mapear keyref restrições de esquema XML (XSD) para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="4690d-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="4690d-103">O **keyref** elemento permite estabelecer links entre elementos dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="4690d-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="4690d-104">Isso é semelhante a uma relação de chave estrangeira no banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="4690d-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="4690d-105">Se um esquema Especifica a **keyref** elemento, o elemento foi convertido durante o processo de mapeamento de esquema para uma restrição de chave estrangeira correspondente nas colunas nas tabelas do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4690d-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4690d-106">Por padrão, o **keyref** elemento também gera uma relação com o **ParentTable**, **ChildTable**, **ParentColumn**e  **ChildColumn** propriedades especificadas na relação.</span><span class="sxs-lookup"><span data-stu-id="4690d-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="4690d-107">A tabela a seguir descreve o **msdata** atributos que você pode especificar o **keyref** elemento.</span><span class="sxs-lookup"><span data-stu-id="4690d-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="4690d-108">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="4690d-108">Attribute name</span></span>|<span data-ttu-id="4690d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4690d-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4690d-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="4690d-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="4690d-111">Se **ConstraintOnly = "true"** é especificado no **keyref** elemento no esquema, uma restrição é criada, mas nenhuma relação é criada.</span><span class="sxs-lookup"><span data-stu-id="4690d-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="4690d-112">Se esse atributo não for especificado (ou seja definido como **False**), a restrição e a relação são criados no **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4690d-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="4690d-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="4690d-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="4690d-114">Se o **ConstraintName** atributo for especificado, seu valor é usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="4690d-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="4690d-115">Caso contrário, o **nome** atributo do **keyref** elemento no esquema fornece o nome da restrição no **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4690d-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="4690d-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="4690d-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="4690d-117">Se o **UpdateRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído ao **UpdateRule** propriedade restrição no  **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4690d-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="4690d-118">Caso contrário, o **UpdateRule** está definida como **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="4690d-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="4690d-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="4690d-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="4690d-120">Se o **DeleteRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído ao **DeleteRule** propriedade restrição no  **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4690d-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="4690d-121">Caso contrário, o **DeleteRule** está definida como **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="4690d-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="4690d-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="4690d-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="4690d-123">Se o **AcceptRejectRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído ao **AcceptRejectRule** propriedade restrição no  **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4690d-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="4690d-124">Caso contrário, o **AcceptRejectRule** está definida como **nenhum**.</span><span class="sxs-lookup"><span data-stu-id="4690d-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="4690d-125">O exemplo a seguir contém um esquema que especifica o **chave** e **keyref** relações entre o **OrderNumber** elemento filho do **ordem**  elemento e o **OrderNo** elemento filho do **OrderDetail** elemento.</span><span class="sxs-lookup"><span data-stu-id="4690d-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="4690d-126">No exemplo, o **OrderNumber** elemento filho do **OrderDetail** elemento refere-se ao **OrderNo** elemento chave filho do **ordem**elemento.</span><span class="sxs-lookup"><span data-stu-id="4690d-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="4690d-127">O processo de mapeamento XML Schema definition language (XSD) esquema produz os seguintes **DataSet** com duas tabelas:</span><span class="sxs-lookup"><span data-stu-id="4690d-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="4690d-128">Além disso, o **DataSet** define as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="4690d-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="4690d-129">Uma restrição exclusiva no **ordem** tabela.</span><span class="sxs-lookup"><span data-stu-id="4690d-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="4690d-130">Uma relação entre o **ordem** e **OrderDetail** tabelas.</span><span class="sxs-lookup"><span data-stu-id="4690d-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="4690d-131">O **aninhadas** está definida como **False** porque os dois elementos não estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="4690d-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   <span data-ttu-id="4690d-132">Uma restrição de chave estrangeira no **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="4690d-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4690d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4690d-133">See Also</span></span>  
 [<span data-ttu-id="4690d-134">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="4690d-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="4690d-135">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="4690d-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="4690d-136">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4690d-136">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
