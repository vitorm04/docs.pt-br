---
title: Gerar relações de DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 29c0e9ee96c376c6da392692febccbbae3c6a33f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170216"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Gerar relações de DataSet do esquema XML (XSD)
Em um <xref:System.Data.DataSet>, você forma uma associação entre dois ou mais colunas, criando uma relação pai-filho. Há três maneiras de representar uma **conjunto de dados** relação dentro de um esquema XSD (linguagem) de definição de esquema XML:  
  
-   Especifica tipos complexos aninhados.  
  
-   Use o **msdata:Relationship** anotação.  
  
-   Especifique um **xs: keyref** sem o **msdata:ConstraintOnly** anotação.  
  
## <a name="nested-complex-types"></a>Tipos complexos aninhados  
 Definições de tipo complexo aninhado em um esquema indicam as relações pai-filho dos elementos. O fragmento de esquema XML a seguir mostra que **OrderDetail** é um elemento filho do **ordem** elemento.  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 O processo de mapeamento de esquema XML cria tabelas na **conjunto de dados** que correspondem aos tipos aninhados complexos no esquema. Ele também cria colunas adicionais que são usadas como pai**-** colunas filho para as tabelas geradas. Observe que esses pai**-** colunas filho especificam relações, que não é o mesmo que especificar restrições de chave estrangeira/chave primária.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship anotação  
 O **msdata:Relationship** anotação permite que você especifique explicitamente as relações pai-filho entre os elementos no esquema que não estão aninhados. O exemplo a seguir mostra a estrutura do **relação** elemento.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Os atributos do **msdata:Relationship** anotação identificar os elementos envolvidos na relação pai-filho, bem como o **parentkey** e **childkey** elementos e atributos envolvidos na relação. O processo de mapeamento usa essas informações para gerar tabelas na **conjunto de dados** e criar a relação de chave estrangeira/chave primária entre essas tabelas.  
  
 Por exemplo, o fragmento de esquema a seguir especifica **ordem** e **OrderDetail** elementos no mesmo nível (não aninhado). O esquema especifica um **msdata:Relationship** anotação, que especifica a relação pai-filho entre esses dois elementos. Nesse caso, um relacionamento explícito deve ser especificado usando o **msdata:Relationship** anotação.  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 Usa o processo de mapeamento a **relacionamento** elemento para criar uma relação pai-filho entre os **OrderNumber** coluna no **ordem** tabela e o **OrderNo** coluna o **OrderDetail** na tabela a **DataSet**. O processo de mapeamento especifica apenas a relação; ele não automaticamente especificar quaisquer restrições nos valores nessas colunas, assim como as restrições de chave estrangeira/chave primárias em bancos de dados relacionais.  
  
### <a name="in-this-section"></a>Nesta seção  
 [Mapear relações implícitas entre elementos de esquema aninhados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Descreve as restrições e relações são criadas implicitamente em um **conjunto de dados** quando elementos aninhados são encontrados no esquema XML.  
  
 [Mapear relações especificadas para elementos aninhados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Descreve como definir explicitamente as relações em um **conjunto de dados** para elementos aninhados no esquema XML.  
  
 [Especificar relações entre elementos sem nenhum aninhamento](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Descreve como criar relações em um **conjunto de dados** entre os elementos de esquema XML que não estão aninhados.  
  
### <a name="related-sections"></a>Seções relacionadas  
 [Derivando a estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional ou o esquema de um **conjunto de dados** que é criado a partir do esquema de (XSD) de linguagem de definição de esquema XML.  
  
 [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave estrangeiras e exclusivas em uma **conjunto de dados**.  
  
## <a name="see-also"></a>Consulte também

- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
