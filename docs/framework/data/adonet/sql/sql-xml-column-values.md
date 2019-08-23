---
title: Valores de coluna de XML do SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 29e9ac5b95b62ef2a4467bf41484c3740d550abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964957"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="25af3-102">Valores de coluna de XML do SQL</span><span class="sxs-lookup"><span data-stu-id="25af3-102">SQL XML Column Values</span></span>
<span data-ttu-id="25af3-103">O SQL Server dá `xml` suporte ao tipo de dados, e os desenvolvedores podem recuperar conjuntos de resultados, incluindo esse <xref:System.Data.SqlClient.SqlCommand> tipo usando o comportamento padrão da classe.</span><span class="sxs-lookup"><span data-stu-id="25af3-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="25af3-104">Uma `xml` coluna pode ser recuperada da mesma forma que qualquer coluna é recuperada (em um <xref:System.Data.SqlClient.SqlDataReader>, por exemplo), mas se você quiser trabalhar com o conteúdo da coluna como XML, deverá <xref:System.Xml.XmlReader>usar um.</span><span class="sxs-lookup"><span data-stu-id="25af3-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25af3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25af3-105">Example</span></span>  
 <span data-ttu-id="25af3-106">O aplicativo de console a seguir seleciona duas linhas, cada `xml` uma contendo uma coluna, da tabela **Sales. Store** no banco de <xref:System.Data.SqlClient.SqlDataReader> dados **AdventureWorks** para uma instância.</span><span class="sxs-lookup"><span data-stu-id="25af3-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="25af3-107">Para cada linha, o valor da `xml` coluna é lido usando o <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> método de <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="25af3-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="25af3-108">O valor é armazenado em um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="25af3-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="25af3-109">Observe que você deve usar <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> em vez do <xref:System.Data.IDataRecord.GetValue%2A> método se quiser definir o conteúdo como uma <xref:System.Data.SqlTypes.SqlXml> variável; Retorna o valor `xml` da coluna como uma cadeia de caracteres. <xref:System.Data.IDataRecord.GetValue%2A></span><span class="sxs-lookup"><span data-stu-id="25af3-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25af3-110">O banco de dados de exemplo **AdventureWorks** não é instalado por padrão quando você instala o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="25af3-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="25af3-111">Você pode instalá-lo executando SQL Server configuração.</span><span class="sxs-lookup"><span data-stu-id="25af3-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="25af3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25af3-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="25af3-113">Dados XML no SQL Server</span><span class="sxs-lookup"><span data-stu-id="25af3-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- <span data-ttu-id="25af3-114">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="25af3-114">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
