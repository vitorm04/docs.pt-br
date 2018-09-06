---
title: LINQ to SQL de n camadas com o ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 0ea202f7259034614eed6968397e270807626172
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799717"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL de n camadas com o ASP.NET
Na [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplicativos que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você usa o <xref:System.Web.UI.WebControls.LinqDataSource> controle de servidor Web. O controle manipula a maioria da lógica que deve ter para consultar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passar os dados para o navegador, recuperá-la e enviá-lo para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> que atualiza o banco de dados. Você configura apenas o controle na marcação e o controle manipula qualquer transferência de dados entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e o navegador. Como o controle manipula as interações com a camada de apresentação, e as alças de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a comunicação com a camada de dados, o foco principal em aplicativos multicamadas de [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] estão em escrever sua lógica comercial personalizado.  
  
 Para obter mais informações sobre `LINQDataSource`, consulte [NIB: Visão geral do controle de servidor Web LinqDataSource](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos de N camadas e remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
