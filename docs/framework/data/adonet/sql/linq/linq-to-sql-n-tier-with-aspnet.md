---
title: LINQ to SQL de n camadas com o ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 435f24a0f105a24bbec91a7e70dc5aaaa25e5649
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL de n camadas com o ASP.NET
Em [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplicativos que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você usa o <xref:System.Web.UI.WebControls.LinqDataSource> controle de servidor Web. O controle processa a maior parte da lógica de que ele deve ter a consulta em relação a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passar os dados para o navegador, recuperá-la e enviá-lo para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> que atualiza o banco de dados. Você acabou de configurar o controle na marcação e controle gerencia todos os dados transferem entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e o navegador. Como o controle manipula as interações com a camada de apresentação, e as alças de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a comunicação com a camada de dados, o foco principal em aplicativos multicamadas de [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] estão em escrever sua lógica comercial personalizado.  
  
 Para obter mais informações sobre `LINQDataSource`, consulte [NIB: Visão geral do controle de servidor Web LinqDataSource](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos de N camadas e remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
