---
title: Valores de coluna de XML do SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: cd55e2263d4b71fe62910ac918e331ebe37833eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177274"
---
# <a name="sql-xml-column-values"></a>Valores de coluna de XML do SQL

O SQL Server dá suporte ao tipo de dados `xml`, e os desenvolvedores podem recuperar conjuntos de resultados, incluindo esse tipo usando o comportamento padrão da classe <xref:System.Data.SqlClient.SqlCommand>. Uma coluna `xml` pode ser recuperada da mesma forma que qualquer coluna é recuperada (em um <xref:System.Data.SqlClient.SqlDataReader>, por exemplo), mas se você quiser trabalhar com o conteúdo da coluna como XML, deverá usar um <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemplo  

 O aplicativo de console a seguir seleciona duas linhas, cada uma contendo uma coluna `xml`, da tabela **Sales.Store** no banco de dados **AdventureWorks** para uma instância do <xref:System.Data.SqlClient.SqlDataReader>. Para cada linha, o valor da coluna `xml` é lido usando o método <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>. O valor é armazenado em <xref:System.Xml.XmlReader>. Observe que você deverá usar <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> em vez do método <xref:System.Data.IDataRecord.GetValue%2A> se desejar definir o conteúdo para uma variável <xref:System.Data.SqlTypes.SqlXml>; <xref:System.Data.IDataRecord.GetValue%2A> retorna o valor da coluna `xml` como uma cadeia de caracteres.  
  
> [!NOTE]
> O banco de dados **AdventureWorks** de exemplo não é instalado por padrão quando você instala o SQL Server. Você pode instalá-lo executando a Instalação do SQL Server.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Data.SqlTypes.SqlXml>
- [Dados XML no SQL Server](xml-data-in-sql-server.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
