---
title: "Mapear relações definidas para elementos aninhados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9866b556f2ba09cef7616fea4a2a6d8135e6b8e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapear relações definidas para elementos aninhados
Um esquema pode incluir um **msdata:Relationship** anotação para especificar explicitamente o mapeamento entre quaisquer dois elementos no esquema. Os dois elementos especificados na **msdata:Relationship** podem ser aninhados no esquema, mas não precisa ser. O processo de mapeamento usa **msdata:Relationship** no esquema para gerar a primária/chave relação de chave estrangeira entre as duas colunas.  
  
 O exemplo a seguir mostra um esquema XML no qual o **OrderDetail** é um elemento filho do **ordem**. O **msdata:Relationship** identifica essa relação pai-filho e especifica que o **OrderNumber** coluna resultante **ordem** tabela está relacionada com o **OrderNo** coluna resultante **OrderDetail** tabela.  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 O processo de mapeamento de esquema XML cria o seguinte o <xref:System.Data.DataSet>:  
  
-   Um **ordem** e um **OrderDetail** tabela.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   Uma relação entre o **ordem** e **OrderDetail** tabelas. O **aninhadas** para essa relação é definida como **True** porque o **ordem** e **OrderDetail** elementos estão aninhados no esquema .  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 O processo de mapeamento não cria quaisquer restrições.  
  
## <a name="see-also"></a>Consulte também  
 [Gerar relações de conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
