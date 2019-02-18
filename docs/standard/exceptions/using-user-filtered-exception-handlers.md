---
title: Usando manipuladores de exceções filtrados pelo usuário
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 228bae8db833abfa3c8c906d57e2177cde644548
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304603"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="c3e6f-102">Usando manipuladores de exceções filtrados pelo usuário</span><span class="sxs-lookup"><span data-stu-id="c3e6f-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="c3e6f-103">Atualmente, o Visual Basic dá suporte a exceções filtradas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="c3e6f-104">Os manipuladores de exceção filtrados por usuário capturam e tratam exceções com base nos requisitos que você define para a exceção.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="c3e6f-105">Esses manipuladores usam a instrução **Catch** com a palavra-chave **When**.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="c3e6f-106">Essa técnica é útil quando um objeto de exceção em particular corresponde a vários erros.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="c3e6f-107">Nesse caso, o objeto normalmente tem uma propriedade que contém o código de erro específico associado ao erro.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="c3e6f-108">Você pode usar a propriedade do código de erro na expressão para selecionar apenas o erro específico que você deseja manipular na cláusula **Catch**.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="c3e6f-109">O exemplo do Visual Basic a seguir ilustra a instrução **Catch/When**.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="c3e6f-110">A expressão da cláusula filtrada pelo usuário não é restrita de nenhuma forma.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="c3e6f-111">Se ocorrer uma exceção durante a execução da expressão filtrada pelo usuário, essa exceção será descartada e será considerado que a expressão do filtro foi avaliada como falsa.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="c3e6f-112">Nesse caso, o Common Language Runtime continua a pesquisar um manipulador para a exceção atual.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="c3e6f-113">Combinar a exceção específica e as cláusulas filtradas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="c3e6f-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="c3e6f-114">Uma instrução catch pode contar a exceção específica e as cláusulas filtradas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="c3e6f-115">O tempo de execução testa primeiro a exceção específica.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="c3e6f-116">Se a exceção específica for bem-sucedida, o tempo de execução executará o filtro do usuário.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="c3e6f-117">O filtro genérico pode conter uma referência à variável declarada no filtro da classe.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="c3e6f-118">Observe que a ordem das duas cláusulas do filtro não pode ser invertida.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="c3e6f-119">O seguinte exemplo do Visual Basic mostra a exceção específica `ClassLoadException` na instrução **Catch**, além da cláusula filtrada pelo usuário usando a palavra-chave **When**.</span><span class="sxs-lookup"><span data-stu-id="c3e6f-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="c3e6f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3e6f-120">See also</span></span>

- [<span data-ttu-id="c3e6f-121">Exceções</span><span class="sxs-lookup"><span data-stu-id="c3e6f-121">Exceptions</span></span>](index.md)
