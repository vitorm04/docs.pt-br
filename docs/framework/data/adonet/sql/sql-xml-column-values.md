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
# <a name="sql-xml-column-values"></a><span data-ttu-id="18078-102">Valores de coluna de XML do SQL</span><span class="sxs-lookup"><span data-stu-id="18078-102">SQL XML Column Values</span></span>

<span data-ttu-id="18078-103">O SQL Server dá suporte ao tipo de dados `xml`, e os desenvolvedores podem recuperar conjuntos de resultados, incluindo esse tipo usando o comportamento padrão da classe <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="18078-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="18078-104">Uma coluna `xml` pode ser recuperada da mesma forma que qualquer coluna é recuperada (em um <xref:System.Data.SqlClient.SqlDataReader>, por exemplo), mas se você quiser trabalhar com o conteúdo da coluna como XML, deverá usar um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="18078-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18078-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18078-105">Example</span></span>  

 <span data-ttu-id="18078-106">O aplicativo de console a seguir seleciona duas linhas, cada uma contendo uma coluna `xml`, da tabela **Sales.Store** no banco de dados **AdventureWorks** para uma instância do <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="18078-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="18078-107">Para cada linha, o valor da coluna `xml` é lido usando o método <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="18078-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="18078-108">O valor é armazenado em <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="18078-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="18078-109">Observe que você deverá usar <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> em vez do método <xref:System.Data.IDataRecord.GetValue%2A> se desejar definir o conteúdo para uma variável <xref:System.Data.SqlTypes.SqlXml>; <xref:System.Data.IDataRecord.GetValue%2A> retorna o valor da coluna `xml` como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="18078-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18078-110">O banco de dados **AdventureWorks** de exemplo não é instalado por padrão quando você instala o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="18078-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="18078-111">Você pode instalá-lo executando a Instalação do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="18078-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18078-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="18078-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="18078-113">Dados XML no SQL Server</span><span class="sxs-lookup"><span data-stu-id="18078-113">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="18078-114">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="18078-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
