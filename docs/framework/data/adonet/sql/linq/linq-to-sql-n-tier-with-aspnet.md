---
title: LINQ to SQL de n camadas com o ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793026"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL de n camadas com o ASP.NET
Em aplicativos ASP.NET que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]o, você usa <xref:System.Web.UI.WebControls.LinqDataSource> o controle de servidor Web. O controle manipula a maior parte da lógica que deve ser consultada [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passa os dados para o navegador, recupera-os e envia-os para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> que, em seguida, o atualiza. Você apenas configura o controle na marcação, e o controle manipula toda a transferência de dados entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o e o navegador. Como o controle manipula as interações com a camada de apresentação [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e manipula a comunicação com a camada de dados, seu foco principal em aplicativos multicamadas ASP.net é escrever sua lógica de negócios personalizada.  
  
 Para obter mais informações `LINQDataSource`sobre o, consulte [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).  
  
## <a name="see-also"></a>Consulte também

- [Aplicativos de N camadas e remotos com o LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
