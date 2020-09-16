---
title: LINQ to SQL de n camadas com o ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1af7f0d78f16e25c1ae7bf563c6abfb3b77f6183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559220"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL de n camadas com o ASP.NET
Em aplicativos ASP.NET que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o, você usa o <xref:System.Web.UI.WebControls.LinqDataSource> controle de servidor Web. O controle manipula a maior parte da lógica que deve ser consultada [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , passa os dados para o navegador, recupera-os e envia-os para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> que, em seguida, o atualiza. Você apenas configura o controle na marcação, e o controle manipula toda a transferência de dados entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o e o navegador. Como o controle manipula as interações com a camada de apresentação e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] manipula a comunicação com a camada de dados, seu foco principal em aplicativos multicamadas ASP.net é escrever sua lógica de negócios personalizada.  
  
 Para obter mais informações sobre o `LINQDataSource` , consulte [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Confira também

- [Aplicativos de n camadas e remoto com LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
