---
title: Procedimentos recursivos
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 646d4e29ed7a0b6367d4b35a7f8641bcf659e616
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352549"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="cede0-102">Procedimentos recursivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cede0-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="cede0-103">Um procedimento *recursivo* é aquele que chama a si mesmo.</span><span class="sxs-lookup"><span data-stu-id="cede0-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="cede0-104">Em geral, essa não é a maneira mais eficiente de escrever Visual Basic código.</span><span class="sxs-lookup"><span data-stu-id="cede0-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="cede0-105">O procedimento a seguir usa a recursão para calcular o fatorial de seu argumento original.</span><span class="sxs-lookup"><span data-stu-id="cede0-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="cede0-106">Considerações com procedimentos recursivos</span><span class="sxs-lookup"><span data-stu-id="cede0-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="cede0-107">**Limitando condições**.</span><span class="sxs-lookup"><span data-stu-id="cede0-107">**Limiting Conditions**.</span></span> <span data-ttu-id="cede0-108">Você deve criar um procedimento Recursivo para testar pelo menos uma condição que pode encerrar a recursão e também deve lidar com o caso em que nenhuma condição é satisfeita dentro de um número razoável de chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="cede0-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="cede0-109">Sem pelo menos uma condição que possa ser atendida sem falha, o procedimento executa um alto risco de execução em um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="cede0-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="cede0-110">**Uso de Memória**.</span><span class="sxs-lookup"><span data-stu-id="cede0-110">**Memory Usage**.</span></span> <span data-ttu-id="cede0-111">Seu aplicativo tem uma quantidade limitada de espaço para variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="cede0-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="cede0-112">Cada vez que um procedimento chama a si mesmo, ele usa mais desse espaço para cópias adicionais de suas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="cede0-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="cede0-113">Se esse processo continuar indefinidamente, eventualmente causará um erro de <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="cede0-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="cede0-114">**Eficiência**.</span><span class="sxs-lookup"><span data-stu-id="cede0-114">**Efficiency**.</span></span> <span data-ttu-id="cede0-115">Quase sempre é possível substituir um loop pela recursão.</span><span class="sxs-lookup"><span data-stu-id="cede0-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="cede0-116">Um loop não tem a sobrecarga de passar argumentos, inicializar armazenamento adicional e retornar valores.</span><span class="sxs-lookup"><span data-stu-id="cede0-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="cede0-117">Seu desempenho pode ser muito melhor sem chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="cede0-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="cede0-118">**Recursão mútua**.</span><span class="sxs-lookup"><span data-stu-id="cede0-118">**Mutual Recursion**.</span></span> <span data-ttu-id="cede0-119">Você pode observar um desempenho muito ruim, ou até mesmo um loop infinito, se dois procedimentos chamarem uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="cede0-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="cede0-120">Esse tipo de design apresenta os mesmos problemas que um único procedimento Recursivo, mas pode ser mais difícil de detectar e depurar.</span><span class="sxs-lookup"><span data-stu-id="cede0-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="cede0-121">**Chamada com parênteses**.</span><span class="sxs-lookup"><span data-stu-id="cede0-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="cede0-122">Quando um procedimento de `Function` chama-se recursivamente, você deve seguir o nome do procedimento com parênteses, mesmo que não haja nenhuma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="cede0-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="cede0-123">Caso contrário, o nome da função será obtido como representando o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="cede0-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="cede0-124">**Testando**.</span><span class="sxs-lookup"><span data-stu-id="cede0-124">**Testing**.</span></span> <span data-ttu-id="cede0-125">Se você escrever um procedimento Recursivo, deverá testá-lo com muito cuidado para garantir que ele sempre atenda a alguma condição de limitação.</span><span class="sxs-lookup"><span data-stu-id="cede0-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="cede0-126">Você também deve garantir que não seja possível ficar sem memória devido a ter muitas chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="cede0-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="cede0-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cede0-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="cede0-128">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="cede0-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="cede0-129">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="cede0-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="cede0-130">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="cede0-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="cede0-131">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="cede0-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="cede0-132">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="cede0-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="cede0-133">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="cede0-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cede0-134">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="cede0-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="cede0-135">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="cede0-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="cede0-136">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="cede0-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
