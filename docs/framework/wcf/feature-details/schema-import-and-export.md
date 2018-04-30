---
title: Importação e exportação de esquemas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe4ef5b17013bf1a9abf5fd1ca0807fe4d335df4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="schema-import-and-export"></a>Importação e exportação de esquemas
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] inclui um novo mecanismo de serialização, o <xref:System.Runtime.Serialization.DataContractSerializer>. O `DataContractSerializer` converte entre [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XML (em ambas as direções) e objetos. O serializador em si, além de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclui mecanismos de exportação de esquema e importação do esquema associado. *Esquema* é uma descrição legível por máquina formal e precisa a forma do XML que produz o serializador ou que o desserializador pode acessar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a linguagem de definição de esquema do World Wide Web Consortium (W3C) XML (XSD) como sua representação de esquema, que é amplamente interoperável com várias plataformas de terceiros.  
  
 O componente de importação do esquema, <xref:System.Runtime.Serialization.XsdDataContractImporter>, usa um documento de esquema XSD e gera [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (normalmente classes de contrato de dados), de modo que os formulários serializados correspondem ao esquema especificado.  
  
 Por exemplo, o seguinte fragmento de esquema:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 gera o seguinte tipo (ligeiramente simplificado para facilitar a leitura).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Observe que o tipo gerado segue várias práticas recomendadas de contrato de dados (encontrado no [práticas recomendadas: controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
-   O tipo implementa o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
-   Membros de dados são implementados como propriedades públicas que encapsulam os campos particulares.  
  
-   A classe é uma classe parcial e adições podem ser feitas sem modificar o código gerado.  
  
 O <xref:System.Runtime.Serialization.XsdDataContractExporter> permite que você faça o inverso — levam tipos são serializáveis com o `DataContractSerializer` e gerar um documento de esquema XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Não há garantia de fidelidade  
 Não há garantia de que o esquema ou tipos de fazer uma viagem de ida e com total fidelidade. (Um *ida e volta* significa para importar um esquema para criar um conjunto de classes e exportar os resultados para criar um esquema novamente.) O mesmo esquema não pode ser retornado. Reverter o processo não é garantida para preservar a fidelidade também. (Exportar um tipo para gerar a esquema e, em seguida, importar o tipo de volta. É improvável que o mesmo tipo será retornado.)  
  
## <a name="supported-types"></a>Tipos com suporte  
 O modelo de contrato de dados oferece suporte a apenas um subconjunto limitado do esquema WC3. Qualquer esquema que não está de acordo com esse subconjunto fará com que uma exceção durante o processo de importação. Por exemplo, não é possível especificar que um membro de dados de um contrato de dados deve ser serializado como um atributo XML. Assim, os esquemas que exigem o uso de atributos XML não são suportados e causam exceções durante a importação, porque não é possível gerar um contrato de dados com a projeção de XML correto.  
  
 Por exemplo, o seguinte fragmento de esquema não pode ser importado usando as configurações de importação padrão.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Para obter mais informações, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Se um esquema não está de acordo com as regras de contrato de dados, use um mecanismo de serialização diferentes. Por exemplo, o <xref:System.Xml.Serialization.XmlSerializer> usa seu próprio mecanismo de importação de esquema separado. Além disso, há um modo de importação especial em que o intervalo de esquema com suporte é expandido. Para obter mais informações, consulte a seção sobre como gerar <xref:System.Xml.Serialization.IXmlSerializable> tipos no [Importando esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 O `XsdDataContractExporter` oferece suporte a qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que podem ser serializados com o `DataContractSerializer`. Para obter mais informações, consulte [tipos suportados pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Observe que esse esquema gerada usando o `XsdDataContractExporter` dados normalmente válido que o `XsdDataContractImporter` pode usar (a menos que o <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> é usado para personalizar o esquema).  
  
 Para obter mais informações sobre como usar o <xref:System.Runtime.Serialization.XsdDataContractImporter>, consulte [Importando esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Para obter mais informações sobre como usar o <xref:System.Runtime.Serialization.XsdDataContractExporter>, consulte [exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [Importando o esquema para gerar classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [Exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
