---
title: Derivando a estrutura relacional do DataSet do esquema XML (XSD)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eb4f6e3a63c901ec69ca5572a6f79d2f0ac4adfc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Derivando a estrutura relacional do DataSet do esquema XML (XSD)
Esta seção fornece uma visão geral de como o esquema relacional de um `DataSet` é compilado a partir de um documento de esquema XSD (linguagem de definição de esquema XML). Em geral, para cada `complexType` elemento filho de um elemento de esquema, uma tabela é gerada no `DataSet`. A estrutura da tabela é determinada pela definição do tipo complexo. Tabelas são criadas no `DataSet` para elementos de nível superior no esquema. No entanto, uma tabela é criada somente para um nível superior `complexType` elemento quando o `complexType` elemento está aninhado em outro `complexType` aninhada de caso de elemento, no qual `complexType` elemento é mapeado para um `DataTable` dentro de `DataSet`.  
  
 Para obter mais informações sobre o XSD, consulte a parte de esquema XML do World Wide Web Consortium (W3C) 0: Primer recomendação, o esquema de XML parte 1: estruturas de recomendação e o esquema XML parte 2: recomendação de tipos de dados, localizado em [http:// www.w3.org/](http://www.w3.org/TR/).  
  
 O exemplo a seguir demonstra um esquema XML onde `customers` é o elemento filho do `MyDataSet` elemento, que é um **DataSet** elemento.  
  
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
>  Se o elemento `customers` é um tipo de dados de esquema XML simples, como **inteiro**, nenhuma tabela é gerada. As tabelas são criadas apenas para os elementos de nível superior que são tipos complexos.  
  
 No esquema XML a seguir, o **esquema** elemento tem dois filhos do elemento, `InStateCustomers` e `OutOfStateCustomers`.  
  
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
  
 Os elementos filho `InStateCustomers` e `OutOfStateCustomers` são ambos elementos de tipo complexo (`customerType`). Portanto, o processo de mapeamento gera duas tabelas a seguir idênticas no `DataSet`.  
  
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
 Descreve como relações são criadas implicitamente ao usar elementos de esquema XML para criar restrições em um `DataSet`.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como carregar e manter a estrutura relacional e os dados em um `DataSet` como dados XML.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
