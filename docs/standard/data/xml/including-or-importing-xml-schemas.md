---
title: Incluindo ou importando um esquema XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d3b336b0ac4ca4fd02950a572404a117d4c193f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="including-or-importing-xml-schemas"></a>Incluindo ou importando um esquema XML
Um esquema XML pode conter os elementos `<xs:import />`, `<xs:include />` e `<xs:redefine />`. Esses elementos de esquema referem-se a outros esquemas XML que podem ser usados para complementar a estrutura do esquema que os inclui ou importa. As classes <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> e <xref:System.Xml.Schema.XmlSchemaRedefine> são mapeadas para esses elementos na API do modelo de objeto (SOM) de esquema.  
  
## <a name="including-or-importing-an-xml-schema"></a>Incluindo ou importando um esquema XML  
 O exemplo de código a seguir complementa o esquema de cliente criado no [compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tópico com o esquema de endereço. Complementar o esquema de cliente com o esquema de endereço torna disponíveis os tipos de endereço no esquema do cliente.  
  
 É possível incorporar o esquema de endereços empregando os elementos `<xs:include />` ou `<xs:import />` para usar os componentes do esquema de endereços como está, ou empregando um elemento `<xs:redefine />` para modificar qualquer um de seus componentes conforme as necessidades do esquema de cliente. Desde que o esquema de endereço tenha um `targetNamespace` diferente daquele do esquema de cliente, o elemento `<xs:import />` e, consequentemente, a semântica de importação serão usados.  
  
 O exemplo de código inclui o esquema de endereço nas seguintes etapas.  
  
1.  Adiciona o esquema de cliente e o esquema de endereço a um novo objeto de <xref:System.Xml.Schema.XmlSchemaSet> e os compila. Todos os avisos e erros de validação de esquema apresentados durante a leitura ou a compilação dos esquemas são tratados pelo delegado <xref:System.Xml.Schema.ValidationEventHandler>.  
  
2.  Recupera os objetos compilados de <xref:System.Xml.Schema.XmlSchema> para os esquemas de cliente e de endereço de <xref:System.Xml.Schema.XmlSchemaSet> ao fazer a iteração na propriedade <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>. As propriedades de PSCI (Post-Schema-Compilation-Infoset) ficarão acessíveis desde que os esquemas sejam compilados.  
  
3.  Cria um objeto de <xref:System.Xml.Schema.XmlSchemaImport>, define a propriedade <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> da importação para o namespace do esquema de endereço, define a propriedade <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> da importação para o objeto de <xref:System.Xml.Schema.XmlSchema> do esquema de endereço e adiciona a importação à propriedade <xref:System.Xml.Schema.XmlSchema.Includes%2A> do esquema de cliente.  
  
4.  Reutiliza e compila o objeto modificado de <xref:System.Xml.Schema.XmlSchema> do esquema de cliente usando os métodos <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> e <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> da classe <xref:System.Xml.Schema.XmlSchemaSet> e o grava no console.  
  
5.  Por fim, grava recursivamente no console todos os esquemas importados para o esquema de cliente usando a propriedade <xref:System.Xml.Schema.XmlSchema.Includes%2A> do esquema de cliente. A propriedade <xref:System.Xml.Schema.XmlSchema.Includes%2A> fornece acesso a qualquer include (incluir), import (importar) ou redefine (redefinir) adicionados a um esquema.  
  
 Veja abaixo o exemplo de código completo e os esquemas de endereço e de cliente gravados no console.  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 Para obter mais informações sobre o `<xs:import />`, `<xs:include />`, e `<xs:redefine />` elementos e o <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> e <xref:System.Xml.Schema.XmlSchemaRedefine> classes, consulte o [W3C XML Schema](http://go.microsoft.com/fwlink/?LinkId=45242) e <xref:System.Xml.Schema?displayProperty=nameWithType> documentação de referência de classe de namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de modelo de objeto de esquema XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Lendo e gravando esquemas XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Percorrer esquemas XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Edição de esquemas XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
