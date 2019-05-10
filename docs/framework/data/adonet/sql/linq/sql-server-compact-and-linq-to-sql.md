---
title: SQL Server Compact e LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: a0cb45b31f7134264068297f54013f49b35f669d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651195"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="a680b-102">SQL Server Compact e LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a680b-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="a680b-103">SQL Server Compact é o banco de dados padrão instalado com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a680b-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="a680b-104">Para obter mais informações, consulte [usando o SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="a680b-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="a680b-105">Este tópico descreve as principais diferenças em uso, configuração, conjuntos de recursos e escopo de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dão suporte.</span><span class="sxs-lookup"><span data-stu-id="a680b-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="a680b-106">Características do SQL Server Compact com relação ao LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a680b-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="a680b-107">Por padrão, o SQL Server Compact está instalado para todas as edições do Visual Studio e, portanto, está disponível no computador de desenvolvimento para uso com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a680b-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a680b-108">Mas a implantação de um aplicativo que usa o SQL Server Compact e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] difere daquele para um aplicativo do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a680b-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="a680b-109">O SQL Server Compact não faz parte do .NET Framework e, portanto, deve ser empacotado com o aplicativo ou ser baixado separadamente do site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a680b-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="a680b-110">Observe as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="a680b-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="a680b-111">O SQL Server Compact é empacotado como uma DLL que pode ser usada em arquivos de banco de dados (extensão .sdf) diretamente.</span><span class="sxs-lookup"><span data-stu-id="a680b-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="a680b-112">O SQL Server Compact é executado no mesmo processo que o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="a680b-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="a680b-113">A eficiência de comunicação com o SQL Server Compact, portanto, pode ser significativamente maior do que se comunicando com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a680b-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="a680b-114">Por outro lado, o SQL Server Compact requer a interoperabilidade entre código gerenciado e com os custos de atendimento.</span><span class="sxs-lookup"><span data-stu-id="a680b-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="a680b-115">O tamanho da DLL do SQL Server Compact é pequeno.</span><span class="sxs-lookup"><span data-stu-id="a680b-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="a680b-116">Esse recurso reduz o tamanho total do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a680b-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="a680b-117">O tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e a ferramenta de linha de comando SQLMetal dão suporte ao SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="a680b-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="a680b-118">O [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] não dá suporte ao SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="a680b-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="a680b-119">Conjunto de recursos</span><span class="sxs-lookup"><span data-stu-id="a680b-119">Feature Set</span></span>  
 <span data-ttu-id="a680b-120">O conjunto de recursos do SQL Server Compact é muito mais simples do que o conjunto de recursos do SQL Server das seguintes maneiras que podem afetar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos:</span><span class="sxs-lookup"><span data-stu-id="a680b-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="a680b-121">O SQL Server Compact não dá suporte a procedimentos armazenados ou exibições.</span><span class="sxs-lookup"><span data-stu-id="a680b-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="a680b-122">O SQL Server Compact dá suporte apenas um subconjunto dos tipos de dados e funções SQL.</span><span class="sxs-lookup"><span data-stu-id="a680b-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="a680b-123">O SQL Server Compact dá suporte apenas a um subconjunto de construções SQL.</span><span class="sxs-lookup"><span data-stu-id="a680b-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="a680b-124">O SQL Server Compact fornece somente um otimizador mínimo.</span><span class="sxs-lookup"><span data-stu-id="a680b-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="a680b-125">É possível que algumas consultas atinjam o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a680b-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="a680b-126">O SQL Server Compact não dá suporte a confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="a680b-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a680b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a680b-127">See also</span></span>

- [<span data-ttu-id="a680b-128">Referência</span><span class="sxs-lookup"><span data-stu-id="a680b-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
