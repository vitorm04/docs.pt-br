---
title: Geração SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854358"
---
# <a name="sql-generation"></a><span data-ttu-id="b68d7-102">Geração SQL</span><span class="sxs-lookup"><span data-stu-id="b68d7-102">SQL Generation</span></span>
<span data-ttu-id="b68d7-103">Ao escrever um provedor para o Entity Framework, você deve converter Entity Framework árvores de comando no SQL que um banco de dados específico pode entender, como Transact-SQL para SQL Server ou PL/SQL para Oracle.</span><span class="sxs-lookup"><span data-stu-id="b68d7-103">When you write a provider for the Entity Framework, you must translate Entity Framework command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="b68d7-104">Nesta seção, você aprenderá a desenvolver um componente de geração de SQL (para consultas SELECT) para um provedor de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b68d7-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an Entity Framework provider.</span></span> <span data-ttu-id="b68d7-105">Para obter informações sobre as consultas Insert, Update e Delete, consulte [modification SQL Generation](modification-sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="b68d7-105">For information about insert, update, and delete queries, see [Modification SQL Generation](modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="b68d7-106">Para entender esta seção, você deve estar familiarizado com o Entity Framework e o modelo de provedor ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b68d7-106">To understand this section, you should be familiar with the Entity Framework and the ADO.NET Provider Model.</span></span> <span data-ttu-id="b68d7-107">Você também deve entender árvores e <xref:System.Data.Common.CommandTrees.DbExpression>de comando.</span><span class="sxs-lookup"><span data-stu-id="b68d7-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="b68d7-108">A função do módulo de geração SQL</span><span class="sxs-lookup"><span data-stu-id="b68d7-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="b68d7-109">O módulo de geração de SQL de um provedor de Entity Framework converte uma determinada árvore de comando de consulta em uma única instrução SQL SELECT que tem como alvo um banco de dados compatível com SQL: 1999.</span><span class="sxs-lookup"><span data-stu-id="b68d7-109">The SQL generation module of an Entity Framework provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="b68d7-110">O SQL gerado deve ter como poucas consultas aninhadas possível.</span><span class="sxs-lookup"><span data-stu-id="b68d7-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="b68d7-111">O módulo de geração do SQL não deve simplificar a árvore de comando de consulta de saída.</span><span class="sxs-lookup"><span data-stu-id="b68d7-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="b68d7-112">O Entity Framework fará isso, por exemplo, eliminando junções e recolhendo nós de filtro consecutivos.</span><span class="sxs-lookup"><span data-stu-id="b68d7-112">The Entity Framework will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="b68d7-113">A classe de <xref:System.Data.Common.DbProviderServices> é o ponto de partida para acessar a camada de geração SQL para converter árvores de comando em <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="b68d7-113">The <xref:System.Data.Common.DbProviderServices> class is the starting point for accessing the SQL generation layer to convert command trees into <xref:System.Data.Common.DbCommand>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b68d7-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b68d7-114">In This Section</span></span>  
 [<span data-ttu-id="b68d7-115">A forma das árvores de comando</span><span class="sxs-lookup"><span data-stu-id="b68d7-115">The Shape of the Command Trees</span></span>](the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="b68d7-116">Gerando SQL das árvores de comando – Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b68d7-116">Generating SQL from Command Trees - Best Practices</span></span>](generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="b68d7-117">Geração de SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="b68d7-117">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="b68d7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b68d7-118">See also</span></span>

- [<span data-ttu-id="b68d7-119">Escrevendo um Provedor de Dados do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b68d7-119">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
