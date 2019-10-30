---
title: Relações e restrições de esquema XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 47b1a3e81cfbc4eb58531b1633dd29becbe497a2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040039"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="632d8-102">Relações e restrições de esquema XML</span><span class="sxs-lookup"><span data-stu-id="632d8-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="632d8-103">Em um esquema XSD (linguagem de definição de esquema XML), você pode especificar restrições (restrições UNIQUE, Key e keyref) e relações (usando a anotação **MSDATA: relationship** ).</span><span class="sxs-lookup"><span data-stu-id="632d8-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="632d8-104">Este tópico explica como as restrições e as relações especificadas em um esquema XML são interpretadas para gerar o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="632d8-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="632d8-105">Em geral, em um esquema XML, você especifica a anotação **MSDATA: relationship** se você quiser gerar somente relações no **conjunto**de uma.</span><span class="sxs-lookup"><span data-stu-id="632d8-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="632d8-106">Para obter mais informações, consulte [gerando relações de conjunto de dados do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="632d8-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="632d8-107">Você especifica restrições (Unique, Key e keyref) se desejar gerar restrições no **conjunto**de testes.</span><span class="sxs-lookup"><span data-stu-id="632d8-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="632d8-108">Observe que as restrições Key e keyref também são usadas para gerar relações, conforme explicado posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="632d8-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="632d8-109">Gerando uma relação de restrições de chave e keyref</span><span class="sxs-lookup"><span data-stu-id="632d8-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="632d8-110">Em vez de especificar a anotação **MSDATA: relationship** , você pode especificar as restrições de Key e keyref, que são usadas durante o processo de mapeamento de esquema XML para gerar não apenas as restrições, mas também a relação no **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="632d8-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="632d8-111">No entanto, se você especificar `msdata:ConstraintOnly="true"` no elemento **keyref** , o **conjunto** de testes incluirá apenas as restrições e não incluirá a relação.</span><span class="sxs-lookup"><span data-stu-id="632d8-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="632d8-112">O exemplo a seguir mostra um esquema XML que inclui elementos **Order** e **OrderDetail** , que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="632d8-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="632d8-113">O esquema também especifica as restrições de chave e keyref.</span><span class="sxs-lookup"><span data-stu-id="632d8-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="632d8-114">O **conjunto** de os que é gerado durante o processo de mapeamento de esquema XML inclui as tabelas **Order** e **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="632d8-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="632d8-115">Além disso, o **conjunto** de testes inclui relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="632d8-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="632d8-116">O exemplo a seguir mostra essas relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="632d8-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="632d8-117">Observe que o esquema não especifica a anotação **MSDATA: relationship** ; em vez disso, as restrições Key e keyref são usadas para gerar a relação.</span><span class="sxs-lookup"><span data-stu-id="632d8-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
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
  
 <span data-ttu-id="632d8-118">No exemplo de esquema anterior, os elementos **Order** e **OrderDetail** não são aninhados.</span><span class="sxs-lookup"><span data-stu-id="632d8-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="632d8-119">No exemplo de esquema a seguir, esses elementos são aninhados.</span><span class="sxs-lookup"><span data-stu-id="632d8-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="632d8-120">No entanto, nenhuma **MSDATA:** a anotação de relação foi especificada; Portanto, uma relação implícita é assumida.</span><span class="sxs-lookup"><span data-stu-id="632d8-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="632d8-121">Para obter mais informações, consulte [mapear relações implícitas entre elementos de esquema aninhados](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="632d8-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="632d8-122">O esquema também especifica as restrições de chave e keyref.</span><span class="sxs-lookup"><span data-stu-id="632d8-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="632d8-123">O **conjunto** de resultados resultante do processo de mapeamento de esquema XML inclui duas tabelas:</span><span class="sxs-lookup"><span data-stu-id="632d8-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="632d8-124">O **conjunto** de e também inclui as duas relações (uma com base na anotação **MSDATA: relationship** e a outra com base nas restrições Key e keyref) e várias restrições.</span><span class="sxs-lookup"><span data-stu-id="632d8-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="632d8-125">O exemplo a seguir mostra as relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="632d8-125">The following example shows the relations and constraints.</span></span>  
  
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
  
 <span data-ttu-id="632d8-126">Se uma restrição keyref que faz referência a uma tabela aninhada contiver a anotação **MSDATA: Isnestd = "true"** , o **conjunto** de um criará uma única relação aninhada com base na restrição keyref e a restrição UNIQUE/KEY relacionada.</span><span class="sxs-lookup"><span data-stu-id="632d8-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="632d8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="632d8-127">See also</span></span>

- [<span data-ttu-id="632d8-128">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="632d8-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- <span data-ttu-id="632d8-129">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="632d8-129">[ADO.NET Overview](../ado-net-overview.md)</span></span>
