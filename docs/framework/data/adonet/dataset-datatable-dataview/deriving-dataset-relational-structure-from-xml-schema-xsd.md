---
title: Derivando a estrutura relacional do DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 8d11fdbcb973eb3e4b7487eb6aacb28374c4c654
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717927"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Derivando a estrutura relacional do DataSet do esquema XML (XSD)
Esta seção fornece uma visão geral de como o esquema relacional de um `DataSet` é compilado a partir de um documento de esquema XSD (linguagem de definição de esquema XML). Em geral, para cada `complexType` elemento filho de um elemento de esquema, em que uma tabela é gerada a `DataSet`. A estrutura da tabela é determinada pela definição do tipo complexo. Tabelas são criadas no `DataSet` para elementos de nível superior no esquema. No entanto, uma tabela só é criada para um nível superior `complexType` elemento quando o `complexType` elemento está aninhado em outro `complexType` elemento, nesse caso, aninhada `complexType` elemento é mapeado para um `DataTable` dentro a `DataSet`.  
  
 Para obter mais informações sobre o XSD, consulte o World Wide Web Consortium (W3C) [esquema XML parte 0: Recomendação elementar](https://www.w3.org/TR/xmlschema-0/), o [esquema XML parte 1: Recomendação de estruturas](https://www.w3.org/TR/xmlschema-1/)e o [XML Schema Part 2: Recomendação de tipos de dados](https://www.w3.org/TR/xmlschema-2/).  
  
 O exemplo a seguir demonstra um esquema XML no qual `customers` é o elemento filho do `MyDataSet` elemento, que é um **conjunto de dados** elemento.  
  
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
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 O tipo de dados de cada coluna na tabela é derivado do tipo do Esquema XML do elemento ou atributo correspondente especificado.  
  
> [!NOTE]
>  Se o elemento `customers` é um tipo de dados de esquema XML simples, como **inteiro**, nenhuma tabela será gerada. As tabelas são criadas apenas para os elementos de nível superior que são tipos complexos.  
  
 No esquema XML a seguir, o **esquema** elemento tem dois elementos filho, `InStateCustomers` e `OutOfStateCustomers`.  
  
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
  
 Os elementos filho `InStateCustomers` e `OutOfStateCustomers` são ambos elementos de tipo complexo (`customerType`). Portanto, o processo de mapeamento gera as seguintes duas tabelas idênticas no `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave estrangeiras e exclusivas em um `DataSet`.  
  
 [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Descreve os elementos de esquema XML usados para criar relações entre colunas da tabela em um `DataSet`.  
  
 [Relações e restrições de esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 Descreve como as relações são criadas implicitamente ao usar elementos de esquema XML para criar restrições em um `DataSet`.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como carregar e manter a estrutura relacional e os dados em um `DataSet` como dados XML.  
  
## <a name="see-also"></a>Consulte também
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
