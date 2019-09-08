---
title: Consultando o banco de dados
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: 3c48879d8e3ae699ef749fc14923358174010aae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782075"
---
# <a name="querying-the-database"></a><span data-ttu-id="aab88-102">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="aab88-102">Querying the Database</span></span>
<span data-ttu-id="aab88-103">Este grupo de tópicos descreve como desenvolver e executar consultas em projetos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aab88-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aab88-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="aab88-104">In This Section</span></span>  
 [<span data-ttu-id="aab88-105">Como: Consultar informações</span><span class="sxs-lookup"><span data-stu-id="aab88-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="aab88-106">Mostra rapidamente como as consultas do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] são basicamente idênticas às consultas do [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aab88-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="aab88-107">Como: Recuperar informações como somente leitura</span><span class="sxs-lookup"><span data-stu-id="aab88-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="aab88-108">Descreve como aumentar o desempenho da consulta quando nenhuma alteração nos dados estiver planejada.</span><span class="sxs-lookup"><span data-stu-id="aab88-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="aab88-109">Como: Controlar a quantidade de dados relacionados recuperados</span><span class="sxs-lookup"><span data-stu-id="aab88-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="aab88-110">Descreve como controlar quais dados relacionados serão recuperados junto com o destino principal.</span><span class="sxs-lookup"><span data-stu-id="aab88-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="aab88-111">Como: Filtrar dados relacionados</span><span class="sxs-lookup"><span data-stu-id="aab88-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="aab88-112">Descreve como recuperar dados relacionados usando uma consulta subconsulta.</span><span class="sxs-lookup"><span data-stu-id="aab88-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="aab88-113">Como: Desativar o carregamento adiado</span><span class="sxs-lookup"><span data-stu-id="aab88-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="aab88-114">Descreve como desativar o carregamento adiado.</span><span class="sxs-lookup"><span data-stu-id="aab88-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="aab88-115">Como: Executar consultas SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="aab88-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="aab88-116">Descreve como enviar consultas usando a linguagem SQL.</span><span class="sxs-lookup"><span data-stu-id="aab88-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="aab88-117">Como: Armazenar e reutilizar consultas</span><span class="sxs-lookup"><span data-stu-id="aab88-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="aab88-118">Descreve como compilar uma consulta uma vez, mas usá-la várias vezes com parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="aab88-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="aab88-119">Como: Manipular chaves compostas em consultas</span><span class="sxs-lookup"><span data-stu-id="aab88-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="aab88-120">Descreve como incluir mais de uma coluna em uma consulta na qual o operador usa apenas um único argumento.</span><span class="sxs-lookup"><span data-stu-id="aab88-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="aab88-121">Como: Recuperar muitos objetos ao mesmo tempo</span><span class="sxs-lookup"><span data-stu-id="aab88-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="aab88-122">Descreve como usar o <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="aab88-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="aab88-123">Como: Filtrar no nível de DataContext</span><span class="sxs-lookup"><span data-stu-id="aab88-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="aab88-124">Descreve outro uso de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="aab88-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="aab88-125">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="aab88-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="aab88-126">Fornece vários exemplos de consultas.</span><span class="sxs-lookup"><span data-stu-id="aab88-126">Provides many examples of queries.</span></span>
