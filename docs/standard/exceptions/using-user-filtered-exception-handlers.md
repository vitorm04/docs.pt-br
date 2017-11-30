---
title: "Usando manipuladores de exceções filtrados pelo usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a71a722063448fb0d568f4bfb4f71d4e01c57454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="e9668-102">Usando manipuladores de exceções filtrados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e9668-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="e9668-103">Atualmente, o Visual Basic suporta exceções filtradas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e9668-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="e9668-104">Os manipuladores de exceção filtrados por usuário capturam e tratam exceções com base nos requisitos que você define para a exceção.</span><span class="sxs-lookup"><span data-stu-id="e9668-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="e9668-105">Esses manipuladores utiliza o **Catch** instrução com o **quando** palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e9668-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="e9668-106">Essa técnica é útil quando um objeto de exceção em particular corresponde a vários erros.</span><span class="sxs-lookup"><span data-stu-id="e9668-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="e9668-107">Nesse caso, o objeto normalmente tem uma propriedade que contém o código de erro específico associado ao erro.</span><span class="sxs-lookup"><span data-stu-id="e9668-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="e9668-108">Você pode usar a propriedade do código de erro na expressão para selecionar apenas o erro específico que você deseja manipular no que **Catch** cláusula.</span><span class="sxs-lookup"><span data-stu-id="e9668-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="e9668-109">O exemplo de Visual Basic a seguir ilustra o **Catch/quando** instrução.</span><span class="sxs-lookup"><span data-stu-id="e9668-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="e9668-110">A expressão da cláusula de filtro de usuário não é restrita de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="e9668-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="e9668-111">Se ocorrer uma exceção durante a execução da expressão de filtro de usuário, essa exceção será descartada e a expressão de filtro é considerada a ser avaliada como false.</span><span class="sxs-lookup"><span data-stu-id="e9668-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="e9668-112">Nesse caso, o common language runtime continua a pesquisa para um manipulador para a exceção atual.</span><span class="sxs-lookup"><span data-stu-id="e9668-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="e9668-113">Combinando a exceção específica e as cláusulas de filtro de usuário</span><span class="sxs-lookup"><span data-stu-id="e9668-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="e9668-114">Uma instrução catch pode conter a exceção específica e as cláusulas de filtro de usuário.</span><span class="sxs-lookup"><span data-stu-id="e9668-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="e9668-115">O tempo de execução testa a exceção específica pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="e9668-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="e9668-116">Se a exceção específica for bem-sucedida, o tempo de execução executa o filtro de usuário.</span><span class="sxs-lookup"><span data-stu-id="e9668-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="e9668-117">O filtro genérico pode conter uma referência à variável declarada no filtro de classe.</span><span class="sxs-lookup"><span data-stu-id="e9668-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="e9668-118">Observe que a ordem das duas cláusulas de filtros não pode ser revertida.</span><span class="sxs-lookup"><span data-stu-id="e9668-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="e9668-119">O seguinte exemplo do Visual Basic mostra a exceção específica `ClassLoadException` no **Catch** instrução, bem como a cláusula de filtro de usuário usando o **quando** palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e9668-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="e9668-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9668-120">See Also</span></span>
[<span data-ttu-id="e9668-121">Exceções</span><span class="sxs-lookup"><span data-stu-id="e9668-121">Exceptions</span></span>](index.md)
