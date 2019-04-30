---
title: Importação e exportação de esquemas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: 9f13f9d95c40b964c5eb416c590a5d603d714bac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991010"
---
# <a name="schema-import-and-export"></a>Importação e exportação de esquemas
Windows Communication Foundation (WCF) inclui um novo mecanismo de serialização, o <xref:System.Runtime.Serialization.DataContractSerializer>. O `DataContractSerializer` converte entre [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objetos e XML (em ambas as direções). Além do serializador em si, o WCF inclui mecanismos de exportação de esquema e importação de esquema associado. *Esquema* é uma descrição formal, precisa e legível por máquina da forma do XML que produz o serializador ou que o desserializador pode acessar. O WCF usa a linguagem de definição de esquema do World Wide Web Consortium (W3C) XML (XSD) como sua representação de esquema, que é amplamente interoperável com várias plataformas de terceiros.  
  
 O componente de importação do esquema <xref:System.Runtime.Serialization.XsdDataContractImporter>, usa um documento de esquema XSD e gera [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (normalmente classes de contrato de dados), de modo que os formulários serializados correspondem ao esquema especificado.  
  
 Por exemplo, o seguinte fragmento de esquema:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 gera o seguinte tipo (um pouco simplificado para melhorar a legibilidade).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Observe que o tipo gerado segue várias práticas recomendadas de contrato de dados (encontrada no [as práticas recomendadas: Controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
- O tipo implementa o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
- Membros de dados são implementados como propriedades públicas que encapsulam os campos particulares.  
  
- A classe é uma classe parcial e adições podem ser feitas sem modificar o código gerado.  
  
 O <xref:System.Runtime.Serialization.XsdDataContractExporter> lhe permite fazer o contrário — levam os tipos que são serializados com o `DataContractSerializer` e gerar um documento de esquema XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Não há garantia de fidelidade  
 Não há garantia de que o esquema ou tipos de fazer uma viagem de ida e com total fidelidade. (Um *ida e volta* significa para importar um esquema para criar um conjunto de classes e exportar os resultados para criar um esquema novamente.) O mesmo esquema não pode ser retornado. Reverter o processo não é garantida para preservar a fidelidade também. (Exporte um tipo para gerar seu esquema e, em seguida, importar o tipo de volta. É improvável que o mesmo tipo será retornado).  
  
## <a name="supported-types"></a>Tipos com suporte  
 O modelo de contrato de dados dá suporte a apenas um subconjunto limitado do esquema WC3. Qualquer esquema que não estão em conformidade com esse subconjunto fará com que uma exceção durante o processo de importação. Por exemplo, não há nenhuma maneira de especificar que um membro de dados de um contrato de dados deve ser serializado como um atributo XML. Assim, os esquemas que exigem o uso de atributos XML não têm suporte e fará com que exceções durante a importação, porque é impossível gerar um contrato de dados com a projeção de XML correto.  
  
 Por exemplo, o seguinte fragmento de esquema não pode ser importado usando as configurações de importação padrão.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Para obter mais informações, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Se um esquema não estiver de acordo com as regras do contrato de dados, use um mecanismo de serialização diferentes. Por exemplo, o <xref:System.Xml.Serialization.XmlSerializer> usa seu próprio mecanismo de importação de esquema separado. Além disso, há um modo de importação especiais em que o intervalo de esquema com suporte é expandido. Para obter mais informações, consulte a seção sobre como gerar <xref:System.Xml.Serialization.IXmlSerializable> digita [Importando esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 O `XsdDataContractExporter` dá suporte a qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que podem ser serializados com o `DataContractSerializer`. Para obter mais informações, consulte [tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Observe esse esquema gerada usando o `XsdDataContractExporter` são normalmente válidos dados que o `XsdDataContractImporter` pode usar (a menos que o <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> é usado para personalizar o esquema).  
  
 Para obter mais informações sobre como usar o <xref:System.Runtime.Serialization.XsdDataContractImporter>, consulte [Importando esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Para obter mais informações sobre como usar o <xref:System.Runtime.Serialization.XsdDataContractExporter>, consulte [exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Importando o esquema para gerar classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
- [Exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
