---
title: LINQ to SQL de n camadas com o ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5069c518998ca1d93f6e1ce94d76c8d0c7da07bd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="d55ab-102">LINQ to SQL de n camadas com o ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d55ab-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="d55ab-103">Em [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] aplicativos que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você usa o <xref:System.Web.UI.WebControls.LinqDataSource> controle de servidor Web.</span><span class="sxs-lookup"><span data-stu-id="d55ab-103">In [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="d55ab-104">O controle processa a maior parte da lógica de que ele deve ter a consulta em relação a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passar os dados para o navegador, recuperá-la e enviá-lo para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> que atualiza o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d55ab-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="d55ab-105">Você acabou de configurar o controle na marcação e controle gerencia todos os dados transferem entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e o navegador.</span><span class="sxs-lookup"><span data-stu-id="d55ab-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="d55ab-106">Como o controle manipula as interações com a camada de apresentação, e as alças de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a comunicação com a camada de dados, o foco principal em aplicativos multicamadas de [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] estão em escrever sua lógica comercial personalizado.</span><span class="sxs-lookup"><span data-stu-id="d55ab-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="d55ab-107">Para obter mais informações sobre `LINQDataSource`, consulte [NIB: Visão geral do controle de servidor Web LinqDataSource](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="d55ab-107">For more information about `LINQDataSource`, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55ab-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d55ab-108">See Also</span></span>  
 [<span data-ttu-id="d55ab-109">Aplicativos de N camadas e remotos com o LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d55ab-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
