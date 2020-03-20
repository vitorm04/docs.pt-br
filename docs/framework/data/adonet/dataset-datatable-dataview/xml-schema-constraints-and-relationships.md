---
title: Relações e restrições de esquema XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150708"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="7882c-102">Relações e restrições de esquema XML</span><span class="sxs-lookup"><span data-stu-id="7882c-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="7882c-103">Em um esquema de definição de Esquema XML (XSD), você pode especificar restrições (restrições únicas, chave e keyref) e relacionamentos (usando a anotação **msdata:Relacionamento).**</span><span class="sxs-lookup"><span data-stu-id="7882c-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="7882c-104">Este tópico explica como as restrições e relacionamentos especificados em um <xref:System.Data.DataSet>Esquema XML são interpretados para gerar o .</span><span class="sxs-lookup"><span data-stu-id="7882c-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7882c-105">Em geral, em um Esquema XML, você especifica a anotação **msdata:Relacionamento** se quiser gerar apenas relacionamentos no **Conjunto de Dados**.</span><span class="sxs-lookup"><span data-stu-id="7882c-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="7882c-106">Para obter mais informações, consulte [Gerando relações de conjunto de dados a partir de XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7882c-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="7882c-107">Você especifica restrições (exclusivo, chave e keyref) se quiser gerar restrições no **Conjunto de Dados**.</span><span class="sxs-lookup"><span data-stu-id="7882c-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="7882c-108">Observe que as restrições de chave e keyref também são usadas para gerar relacionamentos, como explicado posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7882c-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="7882c-109">Gerando um Relacionamento a partir de restrições de chave e keyref</span><span class="sxs-lookup"><span data-stu-id="7882c-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="7882c-110">Em vez de especificar a anotação **msdata:Relacionamento,** você pode especificar as restrições de teclas e keyref, que são usadas durante o processo de mapeamento do Esquema XML para gerar não apenas as restrições, mas também a relação no **Conjunto de Dados**.</span><span class="sxs-lookup"><span data-stu-id="7882c-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="7882c-111">No entanto, `msdata:ConstraintOnly="true"` se você especificar no elemento **keyref,** o **DataSet** incluirá apenas as restrições e não incluirá o relacionamento.</span><span class="sxs-lookup"><span data-stu-id="7882c-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="7882c-112">O exemplo a seguir mostra um esquema XML que inclui elementos **de Ordem** e **OrderDetail,** que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="7882c-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="7882c-113">O esquema também especifica as restrições de chave e keyref.</span><span class="sxs-lookup"><span data-stu-id="7882c-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="7882c-114">O **Conjunto de Dados** gerado durante o processo de mapeamento do Esquema XML inclui as tabelas **Order** and **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="7882c-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="7882c-115">Além disso, o **DataSet** inclui relacionamentos e restrições.</span><span class="sxs-lookup"><span data-stu-id="7882c-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="7882c-116">O exemplo a seguir mostra essas relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="7882c-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="7882c-117">Observe que o esquema não especifica a anotação **msdata:Relacionamento;** em vez disso, as restrições de chave e keyref são usadas para gerar a relação.</span><span class="sxs-lookup"><span data-stu-id="7882c-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="7882c-118">No exemplo do esquema anterior, os elementos **Order** **e OrderDetail** não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="7882c-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="7882c-119">No exemplo do esquema a seguir, esses elementos são aninhados.</span><span class="sxs-lookup"><span data-stu-id="7882c-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="7882c-120">No entanto, nenhuma **anotação msdata:Relacionamento** é especificada; portanto, uma relação implícita é assumida.</span><span class="sxs-lookup"><span data-stu-id="7882c-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="7882c-121">Para obter mais informações, consulte [Mapear relações implícitas entre elementos de esquema aninhados](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="7882c-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="7882c-122">O esquema também especifica as restrições de chave e keyref.</span><span class="sxs-lookup"><span data-stu-id="7882c-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
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
  
 <span data-ttu-id="7882c-123">O **Conjunto de Dados** resultante do processo de mapeamento do Esquema XML inclui duas tabelas:</span><span class="sxs-lookup"><span data-stu-id="7882c-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="7882c-124">O **DataSet** também inclui os dois relacionamentos (um baseado no **msdata:anotação de relacionamento** e outro com base nas restrições de chave e keyref) e várias restrições.</span><span class="sxs-lookup"><span data-stu-id="7882c-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="7882c-125">O exemplo a seguir mostra as relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="7882c-125">The following example shows the relations and constraints.</span></span>  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="7882c-126">Se uma restrição keyref referente a uma tabela aninhada contiver a anotação **msdata:IsNested="true",** o **DataSet** criará uma única relação aninhada baseada na restrição keyref e na restrição única/chave relacionada.</span><span class="sxs-lookup"><span data-stu-id="7882c-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7882c-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7882c-127">See also</span></span>

- [<span data-ttu-id="7882c-128">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7882c-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="7882c-129">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7882c-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
