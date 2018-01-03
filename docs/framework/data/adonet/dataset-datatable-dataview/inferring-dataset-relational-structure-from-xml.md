---
title: Inferindo estrutura relacional do conjunto de dados do XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3c58dbd35c2c203450960118b58da49518098ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Inferindo estrutura relacional do conjunto de dados do XML
A estrutura relacional, ou o esquema, de um <xref:System.Data.DataSet> é composto de tabelas, colunas, restrições e relações. Ao carregar um <xref:System.Data.DataSet> do XML, o esquema pode ser predefinido ou pode ser criado, explicitamente ou por meio de inferência do XML que está sendo carregado. Para obter mais informações sobre como carregar o esquema e o conteúdo de um <xref:System.Data.DataSet> do XML, consulte [carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) e [carregar informações de esquema de conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Se o esquema de um <xref:System.Data.DataSet> está sendo criada do XML, o método preferencial é especificar explicitamente o esquema usando a esquema XML definição linguagem (XSD) (conforme descrito em [derivando estrutura relacional do DataSet do esquema XML (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) ou o XML-Data Reduced (XDR). Se nenhum esquema XSD ou XDR está disponível em XML, o esquema do <xref:System.Data.DataSet> pode ser inferido da estrutura dos elementos e atributos XML.  
  
 Esta seção descreve as regras para <xref:System.Data.DataSet> inferência de esquema mostrando elementos XML e atributos e sua estrutura e resultante inferido <xref:System.Data.DataSet> esquema.  
  
 Nem todos os atributos presentes em um documento XML devem ser incluídos no processo de inferência de tipos. Atributos qualificados por Namespace podem incluir metadados que são importantes para o documento XML, mas não para o <xref:System.Data.DataSet> esquema. Usando <xref:System.Data.DataSet.InferXmlSchema%2A>, você pode especificar namespaces sejam ignorados durante o processo de inferência de tipos. Para obter mais informações, consulte [carregar informações de esquema de conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Resumo do processo de inferência de esquema de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Fornece um resumo de alto nível das regras para inferir o esquema de um <xref:System.Data.DataSet> do XML.  
  
 [Inferindo tabelas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 Descreve os elementos XML que são inferidos como tabelas em um <xref:System.Data.DataSet>.  
  
 [Inferindo colunas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 Descreve os elementos e atributos XML que são inferidos como colunas de tabela.  
  
 [Inferindo relações](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 Descreve o <xref:System.Data.DataRelation> e <xref:System.Data.ForeignKeyConstraint> objetos criados por aninhado, inferido tabelas.  
  
 [Inferindo o texto do elemento](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Descreve as colunas que são criadas para texto em elementos XML e explica quando o texto em elementos XML será ignorado.  
  
 [Limitações de inferência](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 Discute as limitações de inferência de esquema.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como o <xref:System.Data.DataSet> objeto interage com os dados XML.  
  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional, ou o esquema, de um <xref:System.Data.DataSet> que é criado a partir do esquema de linguagem XSD de definição de esquema XML.  
  
 [ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 Descreve o ADO.NET arquitetura e componentes e como usá-las para acessar fontes de dados existentes e gerenciar dados de aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
