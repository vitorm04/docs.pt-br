---
title: Gerar relações de conjunto de dados de esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: fdf22c311ef7b4267f4a4da8566e4ea59504b103
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Gerar relações de conjunto de dados de esquema XML (XSD)
Em um <xref:System.Data.DataSet>, formam uma associação entre duas ou mais colunas, criando uma relação pai-filho. Há três maneiras para representar um **DataSet** relação dentro de um esquema de linguagem XSD de definição de esquema XML:  
  
-   Especifica tipos complexos aninhados.  
  
-   Use o **msdata:Relationship** anotação.  
  
-   Especifique um **xs:keyref** sem o **msdata:ConstraintOnly** anotação.  
  
## <a name="nested-complex-types"></a>Tipos complexos aninhados  
 Definições de tipo complexa aninhada em um esquema indicam as relações pai-filho dos elementos. O fragmento de esquema XML a seguir mostra que **OrderDetail** é um elemento filho do **ordem** elemento.  
  
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
  
 O processo de mapeamento de esquema XML cria tabelas de **conjunto de dados** que correspondem aos tipos aninhados complexos no esquema. Ele também cria colunas adicionais que são usadas como pai**-** colunas-filho para as tabelas geradas. Observe que essas pai**-** colunas filho especificam relações, que não é o mesmo que especificar restrições de chave estrangeira/de chave primária.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship anotação  
 O **msdata:Relationship** anotação permite que você especifique explicitamente as relações pai-filho entre elementos do esquema que não estão aninhadas. O exemplo a seguir mostra a estrutura do **relação** elemento.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Os atributos do **msdata:Relationship** anotação identificar os elementos envolvidos na relação pai-filho, bem como o **parentkey** e **childkey** elementos e atributos envolvidos na relação. O processo de mapeamento usa essas informações para gerar tabelas de **DataSet** e criar a relação chave primária/estrangeira chave entre essas tabelas.  
  
 Por exemplo, o fragmento de esquema a seguir especifica **ordem** e **OrderDetail** elementos no mesmo nível (não aninhados). O esquema especifica um **msdata:Relationship** anotação, que especifica a relação pai-filho entre esses dois elementos. Nesse caso, uma relação explicit deve ser especificada usando o **msdata:Relationship** anotação.  
  
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
  
 Usa o processo de mapeamento de **relação** elemento para criar uma relação pai-filho entre o **OrderNumber** coluna o **ordem** tabela e o **OrderNo** coluna o **OrderDetail** tabela o **conjunto de dados**. O processo de mapeamento especifica apenas a relação; ele não especificar automaticamente quaisquer restrições nos valores nessas colunas, assim como as restrições de chave key/foreign primárias em bancos de dados relacionais.  
  
### <a name="in-this-section"></a>Nesta seção  
 [Mapear relações implícita entre elementos de esquema aninhados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Descreve as restrições e relações são criadas implicitamente em um **DataSet** quando elementos aninhados são encontrados no esquema XML.  
  
 [Mapear relações definidas para elementos aninhados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Descreve como definir explicitamente as relações em um **DataSet** para elementos aninhados no esquema XML.  
  
 [Especificar as relações entre os elementos sem nenhum aninhamento](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Descreve como criar relações em um **DataSet** entre elementos de esquema XML que não estão aninhados.  
  
### <a name="related-sections"></a>Seções relacionadas  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional, ou o esquema, de um **conjunto de dados** que é criado a partir do esquema de linguagem XSD de definição de esquema XML.  
  
 [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave estrangeiras e exclusivas em uma **conjunto de dados**.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
