---
title: SQL Server Compact e LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: bdd1237a8eac1c278e7704f3fbf0ae8b1deeff42
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541357"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="c6e63-102">SQL Server Compact e LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c6e63-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="c6e63-103">SQL Server Compact é o banco de dados padrão instalado com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6e63-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="c6e63-104">Para obter mais informações, consulte [usando SQL Server Compact (Visual Studio)](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="c6e63-104">For more information, see [Using SQL Server Compact (Visual Studio)](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="c6e63-105">Este tópico descreve as principais diferenças de uso, configuração, conjuntos de recursos e escopo de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suporte.</span><span class="sxs-lookup"><span data-stu-id="c6e63-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="c6e63-106">Características do SQL Server Compact com relação ao LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c6e63-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="c6e63-107">Por padrão, o SQL Server Compact é instalado para todas as edições do Visual Studio e, portanto, está disponível no computador de desenvolvimento para uso com o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6e63-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="c6e63-108">Mas a implantação de um aplicativo que usa SQL Server Compact e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] difere disso para um aplicativo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c6e63-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="c6e63-109">O SQL Server Compact não faz parte do .NET Framework e, portanto, deve ser empacotado com o aplicativo ou ser baixado separadamente do site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6e63-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="c6e63-110">Observe as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="c6e63-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="c6e63-111">O SQL Server Compact é empacotado como uma DLL que pode ser usada em arquivos de banco de dados (extensão .sdf) diretamente.</span><span class="sxs-lookup"><span data-stu-id="c6e63-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="c6e63-112">O SQL Server Compact é executado no mesmo processo que o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="c6e63-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="c6e63-113">A eficiência da comunicação com o SQL Server Compact pode, portanto, ser significativamente maior do que a comunicação com SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c6e63-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="c6e63-114">Por outro lado, o SQL Server Compact requer a interoperabilidade entre códigos gerenciados e não gerenciados com os custos de atendimento.</span><span class="sxs-lookup"><span data-stu-id="c6e63-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="c6e63-115">O tamanho da DLL do SQL Server Compact é pequeno.</span><span class="sxs-lookup"><span data-stu-id="c6e63-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="c6e63-116">Esse recurso reduz o tamanho total do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6e63-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="c6e63-117">O runtime do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e a ferramenta de linha de comando SQLMetal dão suporte ao SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="c6e63-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="c6e63-118">O Object Relational Designer não oferece suporte a SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="c6e63-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="c6e63-119">Conjunto de recursos</span><span class="sxs-lookup"><span data-stu-id="c6e63-119">Feature Set</span></span>  
 <span data-ttu-id="c6e63-120">O conjunto de recursos SQL Server Compact é muito mais simples do que o conjunto de recursos de SQL Server das seguintes maneiras que podem afetar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] os aplicativos:</span><span class="sxs-lookup"><span data-stu-id="c6e63-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="c6e63-121">O SQL Server Compact não dá suporte a procedimentos armazenados ou exibições.</span><span class="sxs-lookup"><span data-stu-id="c6e63-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="c6e63-122">O SQL Server Compact dá suporte apenas um subconjunto dos tipos de dados e funções SQL.</span><span class="sxs-lookup"><span data-stu-id="c6e63-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="c6e63-123">O SQL Server Compact dá suporte apenas a um subconjunto de construções SQL.</span><span class="sxs-lookup"><span data-stu-id="c6e63-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="c6e63-124">O SQL Server Compact fornece somente um otimizador mínimo.</span><span class="sxs-lookup"><span data-stu-id="c6e63-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="c6e63-125">É possível que algumas consultas atinjam o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c6e63-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="c6e63-126">O SQL Server Compact não dá suporte a confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="c6e63-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e63-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="c6e63-127">See also</span></span>

- [<span data-ttu-id="c6e63-128">Referência</span><span class="sxs-lookup"><span data-stu-id="c6e63-128">Reference</span></span>](reference.md)
