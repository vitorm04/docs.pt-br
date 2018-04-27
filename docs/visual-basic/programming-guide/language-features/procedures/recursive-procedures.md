---
title: Procedimentos recursivos (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 471746f4412b61c9782e8019aa8a9ec6221afb04
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="36cd9-102">Procedimentos recursivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36cd9-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="36cd9-103">Um *recursiva* procedimento é aquele que chama a mesmo.</span><span class="sxs-lookup"><span data-stu-id="36cd9-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="36cd9-104">Em geral, isso não é a maneira mais eficiente para gravar o código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36cd9-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="36cd9-105">O procedimento a seguir usa a recursão para calcular o fatorial do argumento original.</span><span class="sxs-lookup"><span data-stu-id="36cd9-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="36cd9-106">Considerações sobre com procedimentos recursivos</span><span class="sxs-lookup"><span data-stu-id="36cd9-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="36cd9-107">**Das condições de limitação**.</span><span class="sxs-lookup"><span data-stu-id="36cd9-107">**Limiting Conditions**.</span></span> <span data-ttu-id="36cd9-108">Você deve criar um procedimento recursiva para testar a pelo menos uma condição que pode encerrar a recursão, e você também deve tratar o caso em que nenhuma dessas condições é atendida dentro de um número razoável de chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="36cd9-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="36cd9-109">Pelo menos uma condição que possa ser atendida sem falhar, o procedimento é executado um alto risco de execução em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="36cd9-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="36cd9-110">**Uso de Memória**.</span><span class="sxs-lookup"><span data-stu-id="36cd9-110">**Memory Usage**.</span></span> <span data-ttu-id="36cd9-111">Seu aplicativo tem uma quantidade limitada de espaço para variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="36cd9-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="36cd9-112">Cada vez que um procedimento chama a mesmo, ele usa mais do que o espaço para cópias adicionais de suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="36cd9-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="36cd9-113">Se esse processo continua indefinidamente, eventualmente faz com que um <xref:System.StackOverflowException> erro.</span><span class="sxs-lookup"><span data-stu-id="36cd9-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="36cd9-114">**Eficiência**.</span><span class="sxs-lookup"><span data-stu-id="36cd9-114">**Efficiency**.</span></span> <span data-ttu-id="36cd9-115">Quase sempre, você pode substituir um loop de recursão.</span><span class="sxs-lookup"><span data-stu-id="36cd9-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="36cd9-116">Um loop não tem a sobrecarga de argumentos de passagem, inicializar o armazenamento adicional e retornar valores.</span><span class="sxs-lookup"><span data-stu-id="36cd9-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="36cd9-117">O desempenho pode ser muito melhor sem chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="36cd9-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="36cd9-118">**Recursão mútua**.</span><span class="sxs-lookup"><span data-stu-id="36cd9-118">**Mutual Recursion**.</span></span> <span data-ttu-id="36cd9-119">Você pode observar muito baixo desempenho ou até mesmo um loop infinito, se dois procedimentos chamam uma à outra.</span><span class="sxs-lookup"><span data-stu-id="36cd9-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="36cd9-120">Esse design apresenta os mesmos problemas como um procedimento único recursiva, mas pode ser difícil de detectar e depurar.</span><span class="sxs-lookup"><span data-stu-id="36cd9-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="36cd9-121">**Chamando com parênteses**.</span><span class="sxs-lookup"><span data-stu-id="36cd9-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="36cd9-122">Quando uma `Function` procedimento chama recursivamente a mesmo, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="36cd9-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="36cd9-123">Caso contrário, o nome da função é executado como que representa o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="36cd9-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="36cd9-124">**Teste**.</span><span class="sxs-lookup"><span data-stu-id="36cd9-124">**Testing**.</span></span> <span data-ttu-id="36cd9-125">Se você gravar um procedimento recursiva, você deve testá-lo com muito cuidado para garantir que ele atenda sempre alguma condição de limitação.</span><span class="sxs-lookup"><span data-stu-id="36cd9-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="36cd9-126">Você também deve garantir que você não pode ficar sem memória devido a ter muitas chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="36cd9-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cd9-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36cd9-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="36cd9-128">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="36cd9-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="36cd9-129">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="36cd9-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="36cd9-130">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="36cd9-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="36cd9-131">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="36cd9-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="36cd9-132">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="36cd9-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="36cd9-133">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="36cd9-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="36cd9-134">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="36cd9-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="36cd9-135">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="36cd9-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="36cd9-136">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="36cd9-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="36cd9-137">Solução de problemas de exceções: System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="36cd9-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
