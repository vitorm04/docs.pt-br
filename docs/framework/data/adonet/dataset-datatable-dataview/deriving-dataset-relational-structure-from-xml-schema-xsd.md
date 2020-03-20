---
title: Derivando a estrutura relacional do DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151163"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Derivando a estrutura relacional do DataSet do esquema XML (XSD)
Esta seção fornece uma visão geral de como o esquema relacional de um `DataSet` é compilado a partir de um documento de esquema XSD (linguagem de definição de esquema XML). Em geral, `complexType` para cada elemento filho de um elemento de `DataSet`esquema, uma tabela é gerada no . A estrutura da tabela é determinada pela definição do tipo complexo. As tabelas são `DataSet` criadas no para elementos de nível superior no esquema. No entanto, uma tabela só é `complexType` criada `complexType` para um elemento `complexType` de nível superior quando `complexType` o elemento está `DataTable` aninhado dentro de outro elemento, nesse caso o elemento aninhado é mapeado para um dentro do `DataSet`.  
  
 Para obter mais informações sobre o XSD, consulte o World Wide Web Consortium (W3C) [XML Schema Parte 0: Recomendação de Primer,](https://www.w3.org/TR/xmlschema-0/)o [Esquema XML Parte 1: Recomendação de Estruturas](https://www.w3.org/TR/xmlschema-1/)e o Esquema [XML Parte 2: Recomendação de Tipos de Dados](https://www.w3.org/TR/xmlschema-2/).  
  
 O exemplo a seguir demonstra um `customers` Esquema XML `MyDataSet` onde está o elemento filho do elemento, que é um elemento **DataSet.**  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 No exemplo anterior, o elemento `customers` é um elemento de tipo complexo. Portanto, o definição de tipo complexo é analisada, e o processo de mapeamento cria a tabela a seguir.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 O tipo de dados de cada coluna na tabela é derivado do tipo do Esquema XML do elemento ou atributo correspondente especificado.  
  
> [!NOTE]
> Se o `customers` elemento for de um simples tipo de dados XML Schema, como **inteiro,** nenhuma tabela será gerada. As tabelas são criadas apenas para os elementos de nível superior que são tipos complexos.  
  
 No seguinte Esquema XML, o elemento **Schema** tem `InStateCustomers` `OutOfStateCustomers`dois filhos elementos, e .  
  
```xml  
<xs:schema id="SomeID"
            xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Os elementos filho `InStateCustomers` e `OutOfStateCustomers` são ambos elementos de tipo complexo (`customerType`). Portanto, o processo de mapeamento gera as `DataSet`seguintes duas tabelas idênticas no .  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar `DataSet`restrições de chave únicas e estrangeiras em um .  
  
 [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Descreve os elementos de esquema XML usados para `DataSet`criar relações entre colunas de tabela em um .  
  
 [Relações e restrições de esquema XML](xml-schema-constraints-and-relationships.md)  
 Descreve como as relações são criadas implicitamente ao usar elementos `DataSet`do Esquema XML para criar restrições em um .  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como carregar e persistir a estrutura relacional e os dados em dados `DataSet` XML.  
  
## <a name="see-also"></a>Confira também

- [Visão geral do ADO.NET](../ado-net-overview.md)
