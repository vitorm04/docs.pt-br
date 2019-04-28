---
title: Exportando esquemas de classes
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
ms.openlocfilehash: dcbccbea279796fdaec1227b7575cf39e47f9e4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856659"
---
# <a name="exporting-schemas-from-classes"></a>Exportando esquemas de classes
Para gerar esquemas XSD (linguagem) de definição de esquema XML de classes que são usadas no modelo de contrato de dados, use o <xref:System.Runtime.Serialization.XsdDataContractExporter> classe. Este tópico descreve o processo de criação de esquemas.  
  
## <a name="the-export-process"></a>O processo de exportação  
 O processo de exportação de esquema começa com um ou mais tipos e produz um <xref:System.Xml.Schema.XmlSchemaSet> que descreve a projeção de XML desses tipos.  
  
 O `XmlSchemaSet` faz parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]do modelo de objeto de esquema (SOM) que representa um conjunto de documentos de esquema XSD. Para criar documentos XSD de um `XmlSchemaSet`, use a coleção de esquemas do <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> propriedade do `XmlSchemaSet` classe. Em seguida, serializar a cada <xref:System.Xml.Schema.XmlSchema> do objeto usando o <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Para exportar os esquemas  
  
1. Criar uma instância da <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. Opcional. Passar um <xref:System.Xml.Schema.XmlSchemaSet> no construtor. Nesse caso, o esquema gerado durante a exportação de esquema é adicionado a este <xref:System.Xml.Schema.XmlSchemaSet> instância em vez de começar com um espaço em branco <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3. Opcional. Chame um do <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> métodos. O método determina se o tipo especificado pode ser exportado. O método tem as mesmas sobrecargas como o `Export` método na próxima etapa.  
  
4. Chame um do <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> métodos. Há três sobrecargas colocar uma <xref:System.Type>, um <xref:System.Collections.Generic.List%601> de `Type` objetos, ou uma <xref:System.Collections.Generic.List%601> de <xref:System.Reflection.Assembly> objetos. No último caso, todos os tipos em todos os assemblies determinados são exportados.  
  
     Diversas chamadas para o `Export` método resulta em vários itens que estão sendo adicionados à mesma `XmlSchemaSet`. Um tipo não é gerado para o `XmlSchemaSet` se ele já existe. Portanto, chamar `Export` várias vezes na mesma `XsdDataContractExporter` é preferível à criação de várias instâncias do `XsdDataContractExporter` classe. Isso evita que os tipos de esquema duplicadas sejam geradas.  
  
    > [!NOTE]
    >  Se houver uma falha durante a exportação, o `XmlSchemaSet` estará em um estado imprevisível.  
  
5. Acesso a <xref:System.Xml.Schema.XmlSchemaSet> por meio de <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> propriedade.  
  
## <a name="export-options"></a>Opções de exportação  
 Você pode definir as <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> propriedade do <xref:System.Runtime.Serialization.XsdDataContractExporter> a uma instância da <xref:System.Runtime.Serialization.ExportOptions> classe para controlar vários aspectos do processo de exportação. Especificamente, você pode definir as seguintes opções:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Esta coleção de `Type` representa os tipos conhecidos para os tipos que está sendo exportados. (Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Esses tipos conhecidos são exportados em cada `Export` chamar Além disso, para os tipos passados para o `Export` método.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. Um <xref:System.Runtime.Serialization.IDataContractSurrogate> pode ser fornecido por meio dessa propriedade que deseja personalizar o processo de exportação. Para obter mais informações, consulte [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Por padrão, não há substituto é usado.  
  
## <a name="helper-methods"></a>Métodos auxiliares  
 Além de sua função principal de exportação de esquema, o `XsdDataContractExporter` fornece vários métodos auxiliares úteis que fornecem informações sobre os tipos. Elas incluem:  
  
- Método <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>. Esse método usa um `Type` e retorna um <xref:System.Xml.XmlQualifiedName> que representa o nome do elemento raiz e o namespace que seria usado se esse tipo foi serializado como o objeto raiz.  
  
- Método <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>. Esse método usa um `Type` e retorna um <xref:System.Xml.XmlQualifiedName> que representa o nome do tipo de esquema XSD que seria usado se esse tipo foi exportado para o esquema. Para <xref:System.Xml.Serialization.IXmlSerializable> tipos representados como tipos anônimos no esquema, esse método retornará `null`.  
  
- Método <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>. Esse método funciona somente com <xref:System.Xml.Serialization.IXmlSerializable> tipos que são representados como tipos anônimos no esquema e retorna `null` para todos os outros tipos. Para tipos anônimos, este método retorna um <xref:System.Xml.Schema.XmlSchemaType> que representa um determinado `Type`.  
  
 Opções de exportação afetam todos esses métodos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Exportação e importação de esquema](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Importando o esquema para gerar classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
