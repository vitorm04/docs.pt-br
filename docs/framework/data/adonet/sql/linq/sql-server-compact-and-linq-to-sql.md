---
title: SQL Server Compact e LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2717a94228dc1be8da0d84179201747d60c896a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="607e3-102">SQL Server Compact e LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="607e3-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="607e3-103">SQL Server Compact é o banco de dados padrão instalado com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="607e3-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="607e3-104">Para obter mais informações, consulte [PAVE sobre usando o SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span><span class="sxs-lookup"><span data-stu-id="607e3-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="607e3-105">Este tópico descreve as principais diferenças no uso, configuração, conjuntos de recursos e escopo de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suporte.</span><span class="sxs-lookup"><span data-stu-id="607e3-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="607e3-106">Características do SQL Server Compact com relação ao LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="607e3-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="607e3-107">Por padrão, o SQL Server Compact é instalado para todos os [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edições e, portanto, está disponível no computador de desenvolvimento para uso com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="607e3-107">By default, SQL Server Compact is installed for all [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="607e3-108">Mas a implantação de um aplicativo que usa o SQL Server Compact e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] difere de um [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="607e3-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span></span> <span data-ttu-id="607e3-109">O SQL Server Compact não faz parte do .NET Framework e, portanto, deve ser empacotado com o aplicativo ou ser baixado separadamente do site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="607e3-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="607e3-110">Observe as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="607e3-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="607e3-111">O SQL Server Compact é empacotado como uma DLL que pode ser usada em arquivos de banco de dados (extensão .sdf) diretamente.</span><span class="sxs-lookup"><span data-stu-id="607e3-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="607e3-112">SQL Server Compact é executado no mesmo processo que o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="607e3-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="607e3-113">A eficiência de comunicação com o SQL Server Compact, portanto, pode ser significativamente maior do que se comunicar com [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="607e3-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="607e3-114">Por outro lado, o SQL Server Compact exigem interoperabilidade entre código gerenciado e com os seus custos atendente.</span><span class="sxs-lookup"><span data-stu-id="607e3-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="607e3-115">O tamanho da DLL do SQL Server Compact é pequeno.</span><span class="sxs-lookup"><span data-stu-id="607e3-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="607e3-116">Esse recurso reduz o tamanho total do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="607e3-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="607e3-117">O tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e a ferramenta de linha de comando SQLMetal dão suporte ao SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="607e3-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="607e3-118">O [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] não dá suporte ao SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="607e3-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="607e3-119">Conjunto de recursos</span><span class="sxs-lookup"><span data-stu-id="607e3-119">Feature Set</span></span>  
 <span data-ttu-id="607e3-120">O conjunto de recursos do SQL Server Compact é muito mais simples do que o conjunto de recursos do [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] das seguintes maneiras que podem afetar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos:</span><span class="sxs-lookup"><span data-stu-id="607e3-120">The SQL Server Compact feature set is much simpler than the feature set of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="607e3-121">O SQL Server Compact não dá suporte a procedimentos armazenados ou exibições.</span><span class="sxs-lookup"><span data-stu-id="607e3-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="607e3-122">O SQL Server Compact dá suporte apenas um subconjunto dos tipos de dados e funções SQL.</span><span class="sxs-lookup"><span data-stu-id="607e3-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="607e3-123">O SQL Server Compact dá suporte apenas a um subconjunto de construções SQL.</span><span class="sxs-lookup"><span data-stu-id="607e3-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="607e3-124">O SQL Server Compact fornece somente um otimizador mínimo.</span><span class="sxs-lookup"><span data-stu-id="607e3-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="607e3-125">É possível que algumas consultas podem atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="607e3-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="607e3-126">O SQL Server Compact não dá suporte a confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="607e3-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607e3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="607e3-127">See Also</span></span>  
 [<span data-ttu-id="607e3-128">Referência</span><span class="sxs-lookup"><span data-stu-id="607e3-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
