---
title: Chamadas de método locais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 25aded1aa961e182e8d2d472fca4c5a84b501af1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166164"
---
# <a name="local-method-calls"></a><span data-ttu-id="3c6ea-102">Chamadas de método locais</span><span class="sxs-lookup"><span data-stu-id="3c6ea-102">Local Method Calls</span></span>

<span data-ttu-id="3c6ea-103">Um chamada de método local é uma chamada que é executada dentro do modelo do objeto.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="3c6ea-104">Um chamada de método remoto é uma chamada que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte no SQL e passa para o mecanismo de banco de dados para execução.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="3c6ea-105">As chamadas de método local são necessárias quando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o não pode converter a chamada em SQL.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="3c6ea-106">Caso contrário, um <xref:System.InvalidOperationException> será gerado.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="3c6ea-107">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="3c6ea-107">Example 1</span></span>  

 <span data-ttu-id="3c6ea-108">No exemplo a seguir, uma classe `Order` é mapeada para a tabela Orders no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="3c6ea-109">Um método de instância local foi adicionado à classe.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="3c6ea-110">Em Query 1, o construtor da classe `Order` é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="3c6ea-111">Na consulta 2, se você [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tentou traduzir `LocalInstanceMethod()` no SQL, a tentativa falharia e uma <xref:System.InvalidOperationException> exceção seria gerada.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="3c6ea-112">Mas como o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece suporte para chamadas de método local, o Query2 não lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3c6ea-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3c6ea-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="3c6ea-113">See also</span></span>

- [<span data-ttu-id="3c6ea-114">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="3c6ea-114">Background Information</span></span>](background-information.md)
