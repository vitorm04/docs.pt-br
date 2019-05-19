---
title: LINQ to SQL de n camadas com o ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 85ead36d1d927084c11dca1bd73a192b16e4ab7b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880761"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL de n camadas com o ASP.NET
Em aplicativos ASP.NET que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você usa o <xref:System.Web.UI.WebControls.LinqDataSource> controle de servidor Web. O controle manipula a maioria da lógica que deve ter para consultar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passar os dados para o navegador, recuperá-la e enviá-lo para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> que atualiza o banco de dados. Você configura apenas o controle na marcação e o controle manipula qualquer transferência de dados entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e o navegador. Como o controle manipula as interações com a camada de apresentação e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] manipula a comunicação com a camada de dados, o foco principal em aplicativos de várias camados do ASP.NET é sobre como escrever sua lógica de negócios personalizada.  
  
 Para obter mais informações sobre `LINQDataSource`, consulte [visão geral do controle de servidor Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Consulte também

- [Aplicativos de N camadas e remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
