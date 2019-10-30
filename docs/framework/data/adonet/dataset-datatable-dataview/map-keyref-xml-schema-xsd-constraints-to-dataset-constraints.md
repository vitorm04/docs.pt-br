---
title: Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 93f766003326fd41357581196015fd58c71d7508
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040378"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="58860-102">Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="58860-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="58860-103">O elemento **keyref** permite que você estabeleça links entre elementos dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="58860-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="58860-104">Isso é semelhante a uma relação de chave estrangeira em um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="58860-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="58860-105">Se um esquema especificar o elemento **keyref** , o elemento será convertido durante o processo de mapeamento de esquema para uma restrição de chave estrangeira correspondente nas colunas nas tabelas do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="58860-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="58860-106">Por padrão, o elemento **keyref** também gera uma relação, com as **Propriedades parentID**, **ChildTable**, **ParentColumn**e **ChildColumn** especificadas na relação.</span><span class="sxs-lookup"><span data-stu-id="58860-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="58860-107">A tabela a seguir descreve os atributos **MSDATA** que você pode especificar no elemento **keyref** .</span><span class="sxs-lookup"><span data-stu-id="58860-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="58860-108">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="58860-108">Attribute name</span></span>|<span data-ttu-id="58860-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="58860-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="58860-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="58860-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="58860-111">Se **ConstraintOnly = "true"** for especificado no elemento **keyref** no esquema, uma restrição será criada, mas nenhuma relação será criada.</span><span class="sxs-lookup"><span data-stu-id="58860-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="58860-112">Se esse atributo não for especificado (ou estiver definido como **false**), a restrição e a relação serão criadas no **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="58860-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="58860-113">**MSDATA: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="58860-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="58860-114">Se o atributo **ConstraintName** for especificado, seu valor será usado como o nome da restrição.</span><span class="sxs-lookup"><span data-stu-id="58860-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="58860-115">Caso contrário, o atributo **Name** do elemento **keyref** no esquema fornecerá o nome da restrição no **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="58860-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="58860-116">**MSDATA: UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="58860-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="58860-117">Se o atributo **UpdateRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **UpdateRule** no **conjunto**de valores.</span><span class="sxs-lookup"><span data-stu-id="58860-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="58860-118">Caso contrário, a propriedade **UpdateRule** será definida como **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="58860-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="58860-119">**MSDATA: DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="58860-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="58860-120">Se o atributo **DeleteRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **DeleteRule** no **conjunto**de valores.</span><span class="sxs-lookup"><span data-stu-id="58860-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="58860-121">Caso contrário, a propriedade **DeleteRule** será definida como **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="58860-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="58860-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="58860-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="58860-123">Se o atributo **AcceptRejectRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **AcceptRejectRule** no **conjunto**de valores.</span><span class="sxs-lookup"><span data-stu-id="58860-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="58860-124">Caso contrário, a propriedade **AcceptRejectRule** será definida como **None**.</span><span class="sxs-lookup"><span data-stu-id="58860-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="58860-125">O exemplo a seguir contém um esquema que especifica as relações de **chave** e **keyref** entre o elemento filho **OrderNumber** do elemento **Order** e o elemento filho **orderno** de **OrderDetail** elementos.</span><span class="sxs-lookup"><span data-stu-id="58860-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="58860-126">No exemplo, o elemento filho **OrderNumber** do elemento **OrderDetail** refere-se ao elemento filho da chave **orderno** do elemento **Order** .</span><span class="sxs-lookup"><span data-stu-id="58860-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="58860-127">O processo de mapeamento de esquema XSD (linguagem de definição de esquema XML) produz o seguinte **conjunto** de um com duas tabelas:</span><span class="sxs-lookup"><span data-stu-id="58860-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="58860-128">Além disso, o **conjunto** de os define as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="58860-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="58860-129">Uma restrição UNIQUE na tabela de **pedidos** .</span><span class="sxs-lookup"><span data-stu-id="58860-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="58860-130">Uma relação entre as tabelas **Order** e **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="58860-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="58860-131">A propriedade **aninhada** está definida como **false** porque os dois elementos não estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="58860-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="58860-132">Uma restrição FOREIGN KEY na tabela **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="58860-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="58860-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58860-133">See also</span></span>

- [<span data-ttu-id="58860-134">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="58860-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="58860-135">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="58860-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- <span data-ttu-id="58860-136">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="58860-136">[ADO.NET Overview](../ado-net-overview.md)</span></span>
