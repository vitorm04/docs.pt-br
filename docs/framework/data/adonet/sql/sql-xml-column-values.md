---
title: Valores de coluna de XML do SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 03b09d3a53c725bb0e84ba6b5d98944267bc564c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780794"
---
# <a name="sql-xml-column-values"></a>Valores de coluna de XML do SQL
O SQL Server dá `xml` suporte ao tipo de dados, e os desenvolvedores podem recuperar conjuntos de resultados, incluindo esse <xref:System.Data.SqlClient.SqlCommand> tipo usando o comportamento padrão da classe. Uma `xml` coluna pode ser recuperada da mesma forma que qualquer coluna é recuperada (em um <xref:System.Data.SqlClient.SqlDataReader>, por exemplo), mas se você quiser trabalhar com o conteúdo da coluna como XML, deverá <xref:System.Xml.XmlReader>usar um.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir seleciona duas linhas, cada `xml` uma contendo uma coluna, da tabela **Sales. Store** no banco de <xref:System.Data.SqlClient.SqlDataReader> dados **AdventureWorks** para uma instância. Para cada linha, o valor da `xml` coluna é lido usando o <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> método de <xref:System.Data.SqlClient.SqlDataReader>. O valor é armazenado em um <xref:System.Xml.XmlReader>. Observe que você deve usar <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> em vez do <xref:System.Data.IDataRecord.GetValue%2A> método se quiser definir o conteúdo como uma <xref:System.Data.SqlTypes.SqlXml> variável; Retorna o valor `xml` da coluna como uma cadeia de caracteres. <xref:System.Data.IDataRecord.GetValue%2A>  
  
> [!NOTE]
> O banco de dados de exemplo **AdventureWorks** não é instalado por padrão quando você instala o SQL Server. Você pode instalá-lo executando SQL Server configuração.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.SqlTypes.SqlXml>
- [Dados XML no SQL Server](xml-data-in-sql-server.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
