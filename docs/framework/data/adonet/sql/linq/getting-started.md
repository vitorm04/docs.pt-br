---
title: Guia de Introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634684"
---
# <a name="getting-started"></a><span data-ttu-id="b4836-102">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="b4836-102">Getting Started</span></span>
<span data-ttu-id="b4836-103">Usando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você pode usar a tecnologia LINQ para acessar bancos de dados SQL da mesma forma que acessaria uma coleção na memória.</span><span class="sxs-lookup"><span data-stu-id="b4836-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="b4836-104">Por exemplo, o objeto `nw` no código a seguir é criado para representar o banco de dados `Northwind`, a tabela `Customers` é destinada, as linhas são filtradas para `Customers` de `London` e uma cadeia de caracteres de `CompanyName` é selecionada para recuperação.</span><span class="sxs-lookup"><span data-stu-id="b4836-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="b4836-105">Quando o loop é executado, a coleção de valores de `CompanyName` é recuperada.</span><span class="sxs-lookup"><span data-stu-id="b4836-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="b4836-106">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b4836-106">Next Steps</span></span>  
 <span data-ttu-id="b4836-107">Para obter alguns exemplos adicionais, incluindo inserção e atualização, consulte [o que você pode fazer com LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b4836-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="b4836-108">Em seguida, tente alguns tutoriais e explicações passo a passo para ter uma experiência prática de uso do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4836-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="b4836-109">Consulte [aprendendo por passo a passos](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="b4836-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="b4836-110">Por fim, saiba como começar em seu próprio projeto de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lendo [as etapas típicas para usar LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b4836-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4836-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="b4836-111">See also</span></span>

- [<span data-ttu-id="b4836-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b4836-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="b4836-113">Introdução ao LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="b4836-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="b4836-114">Introdução ao LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4836-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="b4836-115">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b4836-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
