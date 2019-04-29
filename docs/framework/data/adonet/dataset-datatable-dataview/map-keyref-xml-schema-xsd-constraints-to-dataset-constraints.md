---
title: Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: dcb295aef6d93222e682ef7f720c83963036e795
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607482"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="55ba3-102">Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="55ba3-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="55ba3-103">O **keyref** elemento permite estabelecer links entre elementos dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="55ba3-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="55ba3-104">Isso é semelhante a uma relação de chave estrangeira no banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="55ba3-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="55ba3-105">Se um esquema Especifica a **keyref** elemento, o elemento é convertido durante o processo de mapeamento de esquema para uma restrição de chave estrangeira correspondente nas colunas nas tabelas da <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="55ba3-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="55ba3-106">Por padrão, o **keyref** elemento também gera uma relação com o **ParentTable**, **ChildTable**, **ParentColumn**e  **ChildColumn** propriedades especificadas na relação.</span><span class="sxs-lookup"><span data-stu-id="55ba3-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="55ba3-107">A tabela a seguir descreve o **msdata** atributos que você pode especificar o **keyref** elemento.</span><span class="sxs-lookup"><span data-stu-id="55ba3-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="55ba3-108">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="55ba3-108">Attribute name</span></span>|<span data-ttu-id="55ba3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="55ba3-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="55ba3-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="55ba3-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="55ba3-111">Se **ConstraintOnly = "true"** for especificado na **keyref** elemento no esquema, uma restrição é criada, mas nenhuma relação é criada.</span><span class="sxs-lookup"><span data-stu-id="55ba3-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="55ba3-112">Se esse atributo não for especificado (ou é definido como **falsos**), a restrição e a relação são criados na **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="55ba3-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="55ba3-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="55ba3-114">Se o **ConstraintName** atributo for especificado, seu valor é usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="55ba3-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="55ba3-115">Caso contrário, o **nome** atributo da **keyref** elemento no esquema fornece o nome da restrição no **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="55ba3-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="55ba3-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="55ba3-117">Se o **UpdateRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído para o **UpdateRule** propriedade restrição no  **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="55ba3-118">Caso contrário, o **UpdateRule** estiver definida como **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="55ba3-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="55ba3-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="55ba3-120">Se o **DeleteRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído para o **DeleteRule** propriedade restrição no  **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="55ba3-121">Caso contrário, o **DeleteRule** estiver definida como **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="55ba3-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="55ba3-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="55ba3-123">Se o **AcceptRejectRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído para o **AcceptRejectRule** propriedade restrição no  **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="55ba3-124">Caso contrário, o **AcceptRejectRule** estiver definida como **None**.</span><span class="sxs-lookup"><span data-stu-id="55ba3-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="55ba3-125">O exemplo a seguir contém um esquema que especifica o **chave** e **keyref** relações entre as **OrderNumber** elemento filho do **ordem**  elemento e o **OrderNo** elemento filho do **OrderDetail** elemento.</span><span class="sxs-lookup"><span data-stu-id="55ba3-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="55ba3-126">No exemplo, o **OrderNumber** elemento filho do **OrderDetail** elemento refere-se ao **OrderNo** elemento chave filho do **ordem**elemento.</span><span class="sxs-lookup"><span data-stu-id="55ba3-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="55ba3-127">O processo de mapeamento de esquema de linguagem XSD do esquema XML definição produz a seguinte **conjunto de dados** com duas tabelas:</span><span class="sxs-lookup"><span data-stu-id="55ba3-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="55ba3-128">Além disso, o **conjunto de dados** define as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="55ba3-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="55ba3-129">Uma restrição exclusiva na **ordem** tabela.</span><span class="sxs-lookup"><span data-stu-id="55ba3-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="55ba3-130">Uma relação entre o **ordem** e **OrderDetail** tabelas.</span><span class="sxs-lookup"><span data-stu-id="55ba3-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="55ba3-131">O **Nested** estiver definida como **falso** porque os dois elementos não estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="55ba3-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
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
  
- <span data-ttu-id="55ba3-132">Uma restrição de chave estrangeira na **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="55ba3-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="55ba3-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55ba3-133">See also</span></span>

- [<span data-ttu-id="55ba3-134">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="55ba3-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="55ba3-135">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="55ba3-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="55ba3-136">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="55ba3-136">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
