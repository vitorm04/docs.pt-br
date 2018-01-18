---
title: Consultando o banco de dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e7f2c2a3936fc27e963867a4a4bf4bc210c6b7e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="querying-the-database"></a><span data-ttu-id="bbea3-102">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="bbea3-102">Querying the Database</span></span>
<span data-ttu-id="bbea3-103">Este grupo de tópicos descreve como desenvolver e executar consultas em projetos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbea3-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbea3-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bbea3-104">In This Section</span></span>  
 [<span data-ttu-id="bbea3-105">Como consultar informações</span><span class="sxs-lookup"><span data-stu-id="bbea3-105">How to: Query for Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-query-for-information.md)  
 <span data-ttu-id="bbea3-106">Mostra rapidamente como as consultas do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] são basicamente idênticas às consultas do [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbea3-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="bbea3-107">Como recuperar informações como somente leitura</span><span class="sxs-lookup"><span data-stu-id="bbea3-107">How to: Retrieve Information As Read-Only</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="bbea3-108">Descreve como aumentar o desempenho da consulta quando nenhuma alteração nos dados estiver planejada.</span><span class="sxs-lookup"><span data-stu-id="bbea3-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="bbea3-109">Como controlar quanto dados relacionados são recuperados</span><span class="sxs-lookup"><span data-stu-id="bbea3-109">How to: Control How Much Related Data Is Retrieved</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="bbea3-110">Descreve como controlar quais dados relacionados serão recuperados junto com o destino principal.</span><span class="sxs-lookup"><span data-stu-id="bbea3-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="bbea3-111">Como filtrar dados relacionados</span><span class="sxs-lookup"><span data-stu-id="bbea3-111">How to: Filter Related Data</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-related-data.md)  
 <span data-ttu-id="bbea3-112">Descreve como recuperar dados relacionados usando uma consulta subconsulta.</span><span class="sxs-lookup"><span data-stu-id="bbea3-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="bbea3-113">Como desligar o carregamento adiado</span><span class="sxs-lookup"><span data-stu-id="bbea3-113">How to: Turn Off Deferred Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="bbea3-114">Descreve como desativar o carregamento adiado.</span><span class="sxs-lookup"><span data-stu-id="bbea3-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="bbea3-115">Como executar consultas SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="bbea3-115">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="bbea3-116">Descreve como enviar consultas usando a linguagem SQL.</span><span class="sxs-lookup"><span data-stu-id="bbea3-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="bbea3-117">Como armazenar e reutilizar consultas</span><span class="sxs-lookup"><span data-stu-id="bbea3-117">How to: Store and Reuse Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="bbea3-118">Descreve como compilar uma consulta uma vez, mas usá-la várias vezes com parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="bbea3-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="bbea3-119">Como manipular chaves compostas em consultas</span><span class="sxs-lookup"><span data-stu-id="bbea3-119">How to: Handle Composite Keys in Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="bbea3-120">Descreve como incluir mais de uma coluna em uma consulta na qual o operador usa apenas um único argumento.</span><span class="sxs-lookup"><span data-stu-id="bbea3-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="bbea3-121">Como recuperar vários objetos de uma vez</span><span class="sxs-lookup"><span data-stu-id="bbea3-121">How to: Retrieve Many Objects At Once</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="bbea3-122">Descreve como usar o <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbea3-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="bbea3-123">Como filtrar no nível de DataContext</span><span class="sxs-lookup"><span data-stu-id="bbea3-123">How to: Filter at the DataContext Level</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="bbea3-124">Descreve outro uso de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="bbea3-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="bbea3-125">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="bbea3-125">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="bbea3-126">Fornece vários exemplos de consultas.</span><span class="sxs-lookup"><span data-stu-id="bbea3-126">Provides many examples of queries.</span></span>
