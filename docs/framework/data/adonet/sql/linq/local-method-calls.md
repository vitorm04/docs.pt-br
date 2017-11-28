---
title: "Chamadas de método locais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32d4726924140029ebe94676f23ba5c495891e8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="local-method-calls"></a><span data-ttu-id="2d534-102">Chamadas de método locais</span><span class="sxs-lookup"><span data-stu-id="2d534-102">Local Method Calls</span></span>
<span data-ttu-id="2d534-103">Um chamada de método local é uma chamada que é executada dentro do modelo do objeto.</span><span class="sxs-lookup"><span data-stu-id="2d534-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="2d534-104">Um chamada de método remoto é uma chamada que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte no SQL e passa para o mecanismo de banco de dados para execução.</span><span class="sxs-lookup"><span data-stu-id="2d534-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="2d534-105">Chamadas de método locais são necessários quando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é possível converter a chamada para SQL.</span><span class="sxs-lookup"><span data-stu-id="2d534-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="2d534-106">Caso contrário, um <xref:System.InvalidOperationException> será gerado.</span><span class="sxs-lookup"><span data-stu-id="2d534-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="2d534-107">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="2d534-107">Example 1</span></span>  
 <span data-ttu-id="2d534-108">No exemplo a seguir, uma classe `Order` é mapeada para a tabela Orders no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="2d534-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="2d534-109">Um método de instância local foi adicionado à classe.</span><span class="sxs-lookup"><span data-stu-id="2d534-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="2d534-110">Em Query 1, o construtor da classe `Order` é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="2d534-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="2d534-111">Na consulta, 2, se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tentou converter `LocalInstanceMethod()`em SQL, a tentativa falhará e um <xref:System.InvalidOperationException> exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="2d534-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="2d534-112">Mas como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte para chamadas de método locais consulta2 não lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="2d534-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2d534-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d534-113">See Also</span></span>  
 [<span data-ttu-id="2d534-114">Informações de plano de fundo</span><span class="sxs-lookup"><span data-stu-id="2d534-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
