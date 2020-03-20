---
title: Mapear relações implícitas entre elementos de esquema aninhados
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150957"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="220e7-102">Mapear relações implícitas entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="220e7-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="220e7-103">Um esquema de definição de Esquema XML (XSD) pode ter tipos complexos aninhados dentro um do outro.</span><span class="sxs-lookup"><span data-stu-id="220e7-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="220e7-104">Neste caso, o processo de mapeamento aplica o <xref:System.Data.DataSet>mapeamento padrão e cria o seguinte no :</span><span class="sxs-lookup"><span data-stu-id="220e7-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="220e7-105">Uma tabela para cada um dos tipos complexos (pai e filho).</span><span class="sxs-lookup"><span data-stu-id="220e7-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="220e7-106">Se não houver nenhuma restrição única no pai, uma coluna de chave principal adicional por definição de tabela chamada *TableName*_Id onde *TableName* é o nome da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="220e7-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="220e7-107">Uma restrição de chave primária na tabela pai identificando a coluna adicional como a chave principal (definindo a propriedade **IsPrimaryKey** para **True**).</span><span class="sxs-lookup"><span data-stu-id="220e7-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="220e7-108">A restrição é\# \# chamada Restrição onde é 1, 2, 3, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="220e7-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="220e7-109">Por exemplo, o nome padrão da primeira restrição é Restrição1.</span><span class="sxs-lookup"><span data-stu-id="220e7-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="220e7-110">Uma restrição de chave estrangeira na tabela infantil identificando a coluna adicional como a chave estrangeira referente à chave primária da tabela-mãe.</span><span class="sxs-lookup"><span data-stu-id="220e7-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="220e7-111">A restrição é nomeada *ParentTable_ChildTable* onde *ParentTable* é o nome da tabela dos pais e *ChildTable* é o nome da tabela filho.</span><span class="sxs-lookup"><span data-stu-id="220e7-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="220e7-112">Uma relação de dados entre as tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="220e7-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="220e7-113">O exemplo a seguir mostra um esquema onde **orderdetail** é um elemento filho da **Ordem**.</span><span class="sxs-lookup"><span data-stu-id="220e7-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="220e7-114">O processo de mapeamento do Esquema XML cria o seguinte no **DataSet**:</span><span class="sxs-lookup"><span data-stu-id="220e7-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="220e7-115">Uma **ordem** e uma tabela **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="220e7-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="220e7-116">Uma restrição única na mesa **da Ordem.**</span><span class="sxs-lookup"><span data-stu-id="220e7-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="220e7-117">Observe que a propriedade **IsPrimaryKey** está definida **como True**.</span><span class="sxs-lookup"><span data-stu-id="220e7-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="220e7-118">Uma restrição de chave estrangeira na tabela **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="220e7-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="220e7-119">Uma relação entre as tabelas **Ordem** e **OrdemDetalhe.**</span><span class="sxs-lookup"><span data-stu-id="220e7-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="220e7-120">A **propriedade Aninhado** para esta relação é definida como **True** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="220e7-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="220e7-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="220e7-121">See also</span></span>

- [<span data-ttu-id="220e7-122">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="220e7-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="220e7-123">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="220e7-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="220e7-124">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="220e7-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
