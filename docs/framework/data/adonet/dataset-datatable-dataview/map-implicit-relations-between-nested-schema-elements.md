---
title: Mapear relações implícitas entre elementos de esquema aninhados
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 25fc2c427727273038f7b4267376d6ba6446b811
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040383"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="e1e93-102">Mapear relações implícitas entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="e1e93-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="e1e93-103">Um esquema XSD (linguagem de definição de esquema XML) pode ter tipos complexos aninhados dentro um do outro.</span><span class="sxs-lookup"><span data-stu-id="e1e93-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="e1e93-104">Nesse caso, o processo de mapeamento aplica o mapeamento padrão e cria o seguinte no <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="e1e93-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="e1e93-105">Uma tabela para cada um dos tipos complexos (pai e filho).</span><span class="sxs-lookup"><span data-stu-id="e1e93-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="e1e93-106">Se não existir nenhuma restrição exclusiva no pai, uma coluna de chave primária adicional por definição de tabela denominada *TableName*_Id, em que *TableName* é o nome da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="e1e93-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="e1e93-107">Uma restrição PRIMARY KEY na tabela pai que identifica a coluna adicional como a chave primária (definindo a propriedade **IsPrimaryKey** como **true**).</span><span class="sxs-lookup"><span data-stu-id="e1e93-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="e1e93-108">A restrição é chamada de restrição\# em que \# é 1, 2, 3 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e1e93-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="e1e93-109">Por exemplo, o nome padrão para a primeira restrição é Constraint1.</span><span class="sxs-lookup"><span data-stu-id="e1e93-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="e1e93-110">Uma restrição FOREIGN KEY na tabela filho que identifica a coluna adicional como a chave estrangeira que faz referência à chave primária da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="e1e93-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="e1e93-111">A restrição é denominada *ParentTable_ChildTable* , em que *ParentTable* é o nome da tabela pai e *ChildTable* é o nome da tabela filho.</span><span class="sxs-lookup"><span data-stu-id="e1e93-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="e1e93-112">Uma relação de dados entre as tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="e1e93-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="e1e93-113">O exemplo a seguir mostra um esquema em que **OrderDetail** é um elemento filho de **Order**.</span><span class="sxs-lookup"><span data-stu-id="e1e93-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="e1e93-114">O processo de mapeamento de esquema XML cria o seguinte no **conjunto de conjuntos**:</span><span class="sxs-lookup"><span data-stu-id="e1e93-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="e1e93-115">Uma **ordem** e uma tabela **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="e1e93-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="e1e93-116">Uma restrição UNIQUE na tabela de **pedidos** .</span><span class="sxs-lookup"><span data-stu-id="e1e93-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="e1e93-117">Observe que a propriedade **IsPrimaryKey** está definida como **true**.</span><span class="sxs-lookup"><span data-stu-id="e1e93-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="e1e93-118">Uma restrição FOREIGN KEY na tabela **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="e1e93-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- <span data-ttu-id="e1e93-119">Uma relação entre as tabelas **Order** e **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="e1e93-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="e1e93-120">A propriedade **aninhada** para essa relação é definida como **true** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="e1e93-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1e93-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1e93-121">See also</span></span>

- [<span data-ttu-id="e1e93-122">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="e1e93-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="e1e93-123">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="e1e93-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- <span data-ttu-id="e1e93-124">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e1e93-124">[ADO.NET Overview](../ado-net-overview.md)</span></span>
