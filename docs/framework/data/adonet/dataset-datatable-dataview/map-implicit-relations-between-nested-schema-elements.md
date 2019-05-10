---
title: Mapear relações implícitas entre elementos de esquema aninhados
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 6fcb0b9bb7c947359c2334d3d116f5317f84af83
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586813"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="cdf35-102">Mapear relações implícitas entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="cdf35-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="cdf35-103">Um esquema XSD (linguagem) de definição de esquema XML pode ter tipos complexos aninhados dentro uma da outra.</span><span class="sxs-lookup"><span data-stu-id="cdf35-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="cdf35-104">Nesse caso, o processo de mapeamento se aplica o mapeamento padrão e cria o seguinte no <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="cdf35-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="cdf35-105">Uma tabela para cada um dos tipos complexos (pai e filho).</span><span class="sxs-lookup"><span data-stu-id="cdf35-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="cdf35-106">Não se existir nenhuma restrição exclusiva no pai, a coluna de chave primária adicional um acordo com a definição de tabela denominada *TableName*ID onde *TableName* é o nome da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="cdf35-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="cdf35-107">Uma restrição de chave primária na tabela pai que identifica a coluna adicional, como a chave primária (definindo o **IsPrimaryKey** propriedade **verdadeiro**).</span><span class="sxs-lookup"><span data-stu-id="cdf35-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="cdf35-108">A restrição é denominada restrição\# onde \# é 1, 2, 3 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="cdf35-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="cdf35-109">Por exemplo, o nome padrão para a primeira restrição é Constraint1.</span><span class="sxs-lookup"><span data-stu-id="cdf35-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="cdf35-110">Uma restrição de chave estrangeira na tabela filho que identifica a coluna adicional, como a chave estrangeira referindo-se para a chave primária da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="cdf35-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="cdf35-111">A restrição é nomeada *ParentTable_ChildTable* onde *ParentTable* é o nome da tabela pai e *ChildTable* é o nome da tabela filho.</span><span class="sxs-lookup"><span data-stu-id="cdf35-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="cdf35-112">Uma relação de dados entre as tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="cdf35-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="cdf35-113">O exemplo a seguir mostra um esquema no qual **OrderDetail** é um elemento filho do **ordem**.</span><span class="sxs-lookup"><span data-stu-id="cdf35-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="cdf35-114">O processo de mapeamento de esquema XML cria o seguinte a **conjunto de dados**:</span><span class="sxs-lookup"><span data-stu-id="cdf35-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="cdf35-115">Uma **ordem** e uma **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="cdf35-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="cdf35-116">Uma restrição exclusiva na **ordem** tabela.</span><span class="sxs-lookup"><span data-stu-id="cdf35-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="cdf35-117">Observe que o **IsPrimaryKey** estiver definida como **verdadeiro**.</span><span class="sxs-lookup"><span data-stu-id="cdf35-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="cdf35-118">Uma restrição de chave estrangeira na **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="cdf35-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- <span data-ttu-id="cdf35-119">Uma relação entre o **ordem** e **OrderDetail** tabelas.</span><span class="sxs-lookup"><span data-stu-id="cdf35-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="cdf35-120">O **Nested** propriedade para essa relação é definida como **verdadeiro** porque o **ordem** e **OrderDetail** elementos são aninhados no esquema .</span><span class="sxs-lookup"><span data-stu-id="cdf35-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cdf35-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdf35-121">See also</span></span>

- [<span data-ttu-id="cdf35-122">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="cdf35-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="cdf35-123">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="cdf35-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- <span data-ttu-id="cdf35-124">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="cdf35-124">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
