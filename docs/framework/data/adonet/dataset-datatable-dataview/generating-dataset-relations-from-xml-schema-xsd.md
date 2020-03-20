---
title: Gerar relações de DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151124"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Gerar relações de DataSet do esquema XML (XSD)
Em <xref:System.Data.DataSet>um , você forma uma associação entre duas ou mais colunas criando uma relação pai-filho. Existem três maneiras de representar uma relação **DataSet** dentro de um esquema de definição de Esquema XML (XSD):  
  
- Especifique tipos complexos aninhados.  
  
- Use a anotação **msdata:Relacionamento.**  
  
- Especifique um **xs:keyref** sem a anotação **msdata:ConstraintOnly.**  
  
## <a name="nested-complex-types"></a>Tipos complexos aninhados  
 Definições complexas de tipo aninhadas em um esquema indicam as relações pai-filho dos elementos. O fragmento de Esquema XML a seguir mostra que **OrderDetail** é um elemento filho do elemento **Ordem.**  
  
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
  
 O processo de mapeamento xml schema cria tabelas no **Conjunto de Dados** que correspondem aos tipos complexos aninhados no esquema. Ele também cria colunas adicionais**-** que são usadas como colunas de filhos-mãe para as tabelas geradas. Observe que**-** essas colunas filho-mãe especificam relacionamentos, o que não é o mesmo que especificar as restrições de chave primária/estrangeira.  
  
## <a name="msdatarelationship-annotation"></a>msdata:Anotação de relacionamento  
 A anotação **msdata:Relacionamento** permite especificar explicitamente as relações pai-filho entre elementos no esquema que não estão aninhados. O exemplo a seguir mostra a estrutura do elemento **Relacionamento.**  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 Os atributos da anotação **msdata:Relacionamento** identificam os elementos envolvidos na relação pai-filho, bem como os elementos e atributos de **chave parental** e **infantil** envolvidos na relação. O processo de mapeamento usa essas informações para gerar tabelas no **DataSet** e para criar a relação chave principal/estrangeira entre essas tabelas.  
  
 Por exemplo, o fragmento de esquema a seguir especifica elementos **de Ordem** e **OrderDetail** no mesmo nível (não aninhado). O esquema especifica uma **anotação msdata:Relacionamento,** que especifica a relação pai-filho entre esses dois elementos. Neste caso, uma relação explícita deve ser especificada usando a anotação **msdata:Relacionamento.**  
  
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
  
 O processo de mapeamento usa o elemento **Relacionamento** para criar uma relação pai-filho entre a coluna **OrderNumber** na tabela **Order** e a coluna **OrderNo** na tabela **OrderDetail** no **Conjunto de dados**. O processo de mapeamento especifica apenas a relação; não especifica automaticamente quaisquer restrições sobre os valores nessas colunas, assim como as restrições de chave primária/estrangeira nas bases de dados relacionais.  
  
### <a name="in-this-section"></a>Nesta seção  
 [Mapear relações implícitas entre elementos de esquema aninhados](map-implicit-relations-between-nested-schema-elements.md)  
 Descreve as restrições e relações que são implicitamente criadas em um **DataSet** quando elementos aninhados são encontrados no Esquema XML.  
  
 [Mapear relações especificadas para elementos aninhados](map-relations-specified-for-nested-elements.md)  
 Descreve como definir explicitamente as relações em um **DataSet** para elementos aninhados no Esquema XML.  
  
 [Especificar relações entre elementos sem nenhum aninhamento](specify-relations-between-elements-with-no-nesting.md)  
 Descreve como criar relações em um **Conjunto de Dados** entre elementos do Esquema XML que não estão aninhados.  
  
### <a name="related-sections"></a>Seções relacionadas  
 [Derivando a estrutura relacional do DataSet do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional, ou esquema, de um conjunto de **dados** que é criado a partir do esquema xml schema (XSD).  
  
 [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave únicas e estrangeiras em um **DataSet**.  
  
## <a name="see-also"></a>Confira também

- [Visão geral do ADO.NET](../ado-net-overview.md)
