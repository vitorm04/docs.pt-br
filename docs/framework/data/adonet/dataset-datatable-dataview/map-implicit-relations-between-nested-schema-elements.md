---
title: "Mapear relações implícita entre elementos de esquema aninhada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0ad26637ec8cd3e9ea555a20810805cf6eb1444e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="17e90-102">Mapear relações implícita entre elementos de esquema aninhada</span><span class="sxs-lookup"><span data-stu-id="17e90-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="17e90-103">Um esquema de linguagem XSD de definição de esquema XML pode ter tipos complexos aninhados dentro de uma outra.</span><span class="sxs-lookup"><span data-stu-id="17e90-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="17e90-104">Nesse caso, o processo de mapeamento aplica-se o mapeamento padrão e cria o seguinte o <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="17e90-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="17e90-105">Uma tabela para cada um dos tipos complexos (pai e filho).</span><span class="sxs-lookup"><span data-stu-id="17e90-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="17e90-106">Não se existir nenhuma restrição exclusiva no pai, a coluna de chave primária adicional um por definição da tabela denominada *TableName*ID onde *TableName* é o nome da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="17e90-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="17e90-107">Uma restrição de chave primária na tabela pai que identifica a coluna adicional, como a chave primária (definindo o **IsPrimaryKey** propriedade **True**).</span><span class="sxs-lookup"><span data-stu-id="17e90-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="17e90-108">A restrição é nomeada restrição *#*  onde  *#*  é 1, 2, 3 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="17e90-108">The constraint is named Constraint*#* where *#* is 1, 2, 3, and so on.</span></span> <span data-ttu-id="17e90-109">Por exemplo, o nome padrão para a primeira restrição é Constraint1.</span><span class="sxs-lookup"><span data-stu-id="17e90-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="17e90-110">Uma restrição de chave estrangeira na tabela filho que identifica a coluna adicional de chave estrangeira que faz referência à chave primária da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="17e90-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="17e90-111">A restrição é nomeada *ParentTable_ChildTable* onde *ParentTable* é o nome da tabela pai e *ChildTable* é o nome da tabela filho.</span><span class="sxs-lookup"><span data-stu-id="17e90-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="17e90-112">Uma relação de dados entre as tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="17e90-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="17e90-113">O exemplo a seguir mostra um esquema onde **OrderDetail** é um elemento filho do **ordem**.</span><span class="sxs-lookup"><span data-stu-id="17e90-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="17e90-114">O processo de mapeamento de esquema XML cria o seguinte o **DataSet**:</span><span class="sxs-lookup"><span data-stu-id="17e90-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="17e90-115">Um **ordem** e um **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="17e90-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="17e90-116">Uma restrição exclusiva no **ordem** tabela.</span><span class="sxs-lookup"><span data-stu-id="17e90-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="17e90-117">Observe que o **IsPrimaryKey** está definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="17e90-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="17e90-118">Uma restrição de chave estrangeira no **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="17e90-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="17e90-119">Uma relação entre o **ordem** e **OrderDetail** tabelas.</span><span class="sxs-lookup"><span data-stu-id="17e90-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="17e90-120">O **aninhadas** para essa relação é definida como **True** porque o **ordem** e **OrderDetail** elementos estão aninhados no esquema .</span><span class="sxs-lookup"><span data-stu-id="17e90-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17e90-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17e90-121">See Also</span></span>  
 [<span data-ttu-id="17e90-122">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="17e90-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="17e90-123">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="17e90-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="17e90-124">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="17e90-124">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
