---
title: Inferir a estrutura relacional do DataSet do esquema XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 9b1932807058777a532457c99efc49f3ddfdf4ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204807"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Inferir a estrutura relacional do DataSet do esquema XML
A estrutura relacional, ou esquema, de um <xref:System.Data.DataSet> é composta de tabelas, colunas, restrições e relações. Ao carregar um <xref:System.Data.DataSet> do XML, o esquema pode ser predefinido ou pode ser criado, explicitamente ou por meio de inferência, a partir do XML que está sendo carregado. Para obter mais informações sobre como carregar o esquema e o <xref:System.Data.DataSet> conteúdo de um XML, consulte [carregamento de um conjunto de dados de XML](loading-a-dataset-from-xml.md) e [carregamento de informações de esquema de DataSet de XML](loading-dataset-schema-information-from-xml.md).  
  
 Se o esquema de um <xref:System.Data.DataSet> estiver sendo criado a partir de XML, o método preferencial será especificar explicitamente o esquema usando o XSD (linguagem de definição de esquema XML) (conforme descrito em derivando a [estrutura relacional do conjunto de dados do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) ou o XML-dados reduzidos (XDR). Se nenhum esquema XML ou esquema XDR estiver disponível no XML, o esquema do <xref:System.Data.DataSet> poderá ser inferido da estrutura dos elementos e atributos XML.  
  
 Esta seção descreve as regras para <xref:System.Data.DataSet> a inferência de esquema mostrando elementos XML e atributos e sua estrutura e o esquema deduzido <xref:System.Data.DataSet> resultante.  
  
 Nem todos os atributos presentes em um documento XML devem ser incluídos no processo de inferência. Atributos qualificados para namespace podem incluir metadados que são importantes para o documento XML, mas não para <xref:System.Data.DataSet> o esquema. Usando <xref:System.Data.DataSet.InferXmlSchema%2A>o, você pode especificar namespaces a serem ignorados durante o processo de inferência. Para obter mais informações, consulte [carregando informações de esquema de conjunto de dados do XML](loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Resumo do processo de inferência de esquema de conjunto de dados](summary-of-the-dataset-schema-inference-process.md)  
 Fornece um resumo de alto nível das regras para inferir o esquema de um <xref:System.Data.DataSet> XML.  
  
 [Inferindo tabelas](inferring-tables.md)  
 Descreve os elementos XML que são inferidos como tabelas em <xref:System.Data.DataSet>um.  
  
 [Inferindo colunas](inferring-columns.md)  
 Descreve os elementos XML e atributos que são inferidos como colunas de tabela.  
  
 [Inferindo relações](inferring-relationships.md)  
 Descreve os <xref:System.Data.DataRelation> objetos <xref:System.Data.ForeignKeyConstraint> e criados para tabelas aninhadas e inferidas.  
  
 [Inferindo o texto do elemento](inferring-element-text.md)  
 Descreve as colunas que são criadas para texto em elementos XML e explica quando o texto em elementos XML é ignorado.  
  
 [Limitações de inferência](inference-limitations.md)  
 Discute as limitações da inferência de esquema.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como o <xref:System.Data.DataSet> objeto interage com dados XML.  
  
 [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Descreve a estrutura relacional, ou esquema, de um <xref:System.Data.DataSet> que é criado a partir do esquema XSD (XML Schema Definition Language).  
  
 [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)  
 Descreve a arquitetura e os componentes do ADO.NET e como usá-los para acessar as fontes de dados existentes e gerenciar os dados do aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
