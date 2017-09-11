---
title: Procedimentos recursivos (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5e4838bb14125dcfd27798acf0c196f351ba5b90
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="a3ef8-102">Procedimentos recursivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3ef8-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="a3ef8-103">A *recursiva* procedimento é aquela que chama a mesmo.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="a3ef8-104">Em geral, isso não é a maneira mais eficiente para gravar [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
 <span data-ttu-id="a3ef8-105">O procedimento a seguir usa a recursão para calcular o fatorial do argumento original.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 <span data-ttu-id="a3ef8-106">[!code-vb[VbVbcnProcedures&#51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3ef8-106">[!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span></span>  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="a3ef8-107">Considerações sobre com procedimentos recursivos</span><span class="sxs-lookup"><span data-stu-id="a3ef8-107">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="a3ef8-108">**Limitando condições**.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-108">**Limiting Conditions**.</span></span> <span data-ttu-id="a3ef8-109">Você deve criar um procedimento de recursiva para testar a pelo menos uma condição que pode finalizar a recursão e você também deverá manipular o caso em que nenhuma dessas condições for atendida dentro de um número razoável de chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="a3ef8-110">Pelo menos uma condição que pode ser atendida sem falhas, o procedimento é executado um alto risco de execução em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="a3ef8-111">**Uso de memória**.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-111">**Memory Usage**.</span></span> <span data-ttu-id="a3ef8-112">Seu aplicativo tem uma quantidade limitada de espaço para variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="a3ef8-113">Cada vez que um procedimento chama a próprio, ele usa mais do que o espaço para cópias adicionais de suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="a3ef8-114">Se esse processo continua indefinidamente, eventualmente causar um <xref:System.StackOverflowException>erro.</xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="a3ef8-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="a3ef8-115">**Eficiência**.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-115">**Efficiency**.</span></span> <span data-ttu-id="a3ef8-116">Você pode substituir quase sempre um loop de recursão.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="a3ef8-117">Um loop não tem a sobrecarga de passagem de argumentos, inicializando o armazenamento adicional e retornar valores.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="a3ef8-118">O desempenho pode ser muito melhor sem chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-118">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="a3ef8-119">**Recursão mútua**.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-119">**Mutual Recursion**.</span></span> <span data-ttu-id="a3ef8-120">Você pode observar um desempenho muito ruim, ou até mesmo um loop infinito, se dois procedimentos chamam uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="a3ef8-121">Esse design apresenta os mesmos problemas como um procedimento único recursiva, mas pode ser difícil de detectar e depurar.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="a3ef8-122">**Chamando com parênteses**.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="a3ef8-123">Quando uma `Function` procedimento chama a mesmo recursivamente, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="a3ef8-124">Caso contrário, o nome de função é usado como o que representa o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="a3ef8-125">**Teste**.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-125">**Testing**.</span></span> <span data-ttu-id="a3ef8-126">Se você escrever um procedimento recursiva, você deve testá-lo com muito cuidado para certificar-se de que ele atende sempre alguma condição de limitação.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="a3ef8-127">Você também deve garantir que você não pode ficar sem memória devido a ter muitas chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="a3ef8-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ef8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3ef8-128">See Also</span></span>  
 <span data-ttu-id="a3ef8-129"><xref:System.StackOverflowException></xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="a3ef8-129"><xref:System.StackOverflowException></span></span>   
<span data-ttu-id="a3ef8-130"> [Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-130"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="a3ef8-131"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-131"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="a3ef8-132"> [Procedimentos de função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-132"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="a3ef8-133"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-133"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="a3ef8-134"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-134"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="a3ef8-135"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a3ef8-136"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="a3ef8-137"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="a3ef8-138"> [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="a3ef8-138"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="a3ef8-139"> [Solução de problemas de exceções: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span><span class="sxs-lookup"><span data-stu-id="a3ef8-139"> [Troubleshooting Exceptions: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span></span>
