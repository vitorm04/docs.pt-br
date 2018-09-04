---
title: Guia de Introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 17b014a5a56a2c60359f6fb0b60df29feb97f2a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529405"
---
# <a name="getting-started"></a><span data-ttu-id="49553-102">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="49553-102">Getting Started</span></span>
<span data-ttu-id="49553-103">Usando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você pode usar o [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] tecnologia para acessar o SQL bancos de dados exatamente como você acessaria uma coleção em memória.</span><span class="sxs-lookup"><span data-stu-id="49553-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="49553-104">Por exemplo, o objeto `nw` no código a seguir é criado para representar o banco de dados `Northwind`, a tabela `Customers` é destinada, as linhas são filtradas para `Customers` de `London` e uma cadeia de caracteres de `CompanyName` é selecionada para recuperação.</span><span class="sxs-lookup"><span data-stu-id="49553-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="49553-105">Quando o loop é executado, a coleção de valores de `CompanyName` é recuperada.</span><span class="sxs-lookup"><span data-stu-id="49553-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="49553-106">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="49553-106">Next Steps</span></span>  
 <span data-ttu-id="49553-107">Para obter alguns exemplos adicionais, incluindo a inserção e atualização, consulte [o que você pode fazer com LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="49553-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="49553-108">Em seguida, tente alguns tutoriais e explicações passo a passo para ter uma experiência prática de uso do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49553-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="49553-109">Ver [aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="49553-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="49553-110">Finalmente, Aprenda como começar a usar em seus próprios [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto lendo [etapas típicas para usar o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="49553-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49553-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49553-111">See Also</span></span>  
 [<span data-ttu-id="49553-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="49553-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="49553-113">Introdução ao LINQ</span><span class="sxs-lookup"><span data-stu-id="49553-113">Introduction to LINQ</span></span>](https://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [<span data-ttu-id="49553-114">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="49553-114">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
