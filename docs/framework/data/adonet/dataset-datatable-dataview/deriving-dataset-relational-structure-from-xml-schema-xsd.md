---
title: Derivando a estrutura relacional do DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d15aa02b41b9a34b00298aeb32d2e3998de8feba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786339"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Derivando a estrutura relacional do DataSet do esquema XML (XSD)
Esta seção fornece uma visão geral de como o esquema relacional de um `DataSet` é compilado a partir de um documento de esquema XSD (linguagem de definição de esquema XML). Em geral, para cada `complexType` elemento filho de um elemento de esquema, uma tabela é gerada `DataSet`no. A estrutura da tabela é determinada pela definição do tipo complexo. As `DataSet` tabelas são criadas no para elementos de nível superior no esquema. No entanto, uma tabela é criada somente para um elemento `complexType` de nível superior `complexType` quando o elemento é aninhado dentro de outro `complexType` elemento; nesse `complexType` caso, o elemento aninhado é `DataSet`mapeado para um `DataTable` dentro do.  
  
 Para obter mais informações sobre o XSD, consulte o esquema XML World Wide Web Consortium [(W3C) parte 0: Recomendação](https://www.w3.org/TR/xmlschema-0/)do primer, [parte 1 do esquema XML: Recomendação](https://www.w3.org/TR/xmlschema-1/)de estruturas e o [esquema XML parte 2: recomendação de tipos de dados](https://www.w3.org/TR/xmlschema-2/).  
  
 O exemplo a seguir demonstra um esquema XML `customers` em que é o elemento filho `MyDataSet` do elemento, que é um elemento **DataSet** .  
  
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
> Se o elemento `customers` for de um tipo de dados de esquema XML simples, como **Integer**, nenhuma tabela será gerada. As tabelas são criadas apenas para os elementos de nível superior que são tipos complexos.  
  
 No esquema XML a seguir, o elemento **Schema** tem dois elementos filho `InStateCustomers` e. `OutOfStateCustomers`  
  
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
  
 Os elementos filho `InStateCustomers` e `OutOfStateCustomers` são ambos elementos de tipo complexo (`customerType`). Portanto, o processo de mapeamento gera as duas tabelas idênticas a `DataSet`seguir no.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Descreve os elementos de esquema XML usados para criar restrições de chave estrangeira e exclusivas em um `DataSet`.  
  
 [Gerando relações de conjunto de dados do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Descreve os elementos de esquema XML usados para criar relações entre colunas de tabela `DataSet`em um.  
  
 [Relações e restrições de esquema XML](xml-schema-constraints-and-relationships.md)  
 Descreve como as relações são criadas implicitamente ao usar elementos de esquema XML para criar restrições `DataSet`em um.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como carregar e manter a estrutura relacional e os dados em um `DataSet` como dados XML.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
