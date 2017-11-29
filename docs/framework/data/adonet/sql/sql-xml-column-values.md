---
title: Valores de coluna de XML do SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c974749ee84bf64d1912ed71ea0817227b1ea514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sql-xml-column-values"></a>Valores de coluna de XML do SQL
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]oferece suporte a `xml` tipo de dados, e os desenvolvedores podem recuperar conjuntos de resultados desse tipo usando o comportamento padrão da <xref:System.Data.SqlClient.SqlCommand> classe. Um `xml` coluna pode ser recuperada como qualquer coluna é recuperada (em um <xref:System.Data.SqlClient.SqlDataReader>, por exemplo), mas se você quiser trabalhar com o conteúdo da coluna como XML, você deve usar um <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemplo  
 O aplicativo de console a seguir seleciona duas linhas, cada uma contendo uma `xml` coluna, do **Sales** tabela o **AdventureWorks** de banco de dados para um <xref:System.Data.SqlClient.SqlDataReader> instância. Para cada linha, o valor da `xml` coluna é leitura usando o <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> método <xref:System.Data.SqlClient.SqlDataReader>. O valor é armazenado em um <xref:System.Xml.XmlReader>. Observe que você deve usar <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> em vez de <xref:System.Data.IDataRecord.GetValue%2A> método se você deseja definir o conteúdo um <xref:System.Data.SqlTypes.SqlXml> variável; <xref:System.Data.IDataRecord.GetValue%2A> retorna o valor da `xml` coluna como uma cadeia de caracteres.  
  
> [!NOTE]
>  O **AdventureWorks** banco de dados de exemplo não é instalado por padrão quando você instala o [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Você pode instalá-lo executando [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instalação.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.SqlTypes.SqlXml>  
 [Dados XML no SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
