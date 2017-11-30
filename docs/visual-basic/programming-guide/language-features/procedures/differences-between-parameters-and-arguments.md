---
title: "Diferenças entre parâmetros e argumentos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="acb73-102">Diferenças entre parâmetros e argumentos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acb73-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="acb73-103">Na maioria dos casos, um procedimento deve ter algumas informações sobre as circunstâncias em que ele foi chamado.</span><span class="sxs-lookup"><span data-stu-id="acb73-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="acb73-104">Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.</span><span class="sxs-lookup"><span data-stu-id="acb73-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="acb73-105">Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="acb73-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="acb73-106">Para comunicar essa informação para o procedimento, o procedimento define um *parâmetro*, e o código de chamada passa um *argumento* para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="acb73-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="acb73-107">Você pode considerar o parâmetro como um espaço de estacionamento e o argumento como um automóvel.</span><span class="sxs-lookup"><span data-stu-id="acb73-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="acb73-108">Assim como automóveis diferentes podem estacionar em um espaço de estacionamento em momentos diferentes, o código de chamada pode passar um argumento diferente para o mesmo parâmetro toda vez que ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="acb73-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="acb73-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="acb73-109">Parameters</span></span>  
 <span data-ttu-id="acb73-110">Um *parâmetro* representa um valor que o procedimento espera passar quando você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="acb73-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="acb73-111">Declaração do procedimento define seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="acb73-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="acb73-112">Quando você define uma `Function` ou `Sub` procedimento, você especificar um *lista de parâmetros* entre parênteses imediatamente após o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="acb73-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="acb73-113">Para cada parâmetro, você especificar um nome, um tipo de dados e um mecanismo de passagem ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="acb73-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="acb73-114">Você também pode indicar que um parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="acb73-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="acb73-115">Isso significa que o código de chamada não precisa passar um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="acb73-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="acb73-116">O nome de cada parâmetro serve como um *variável local* no procedimento.</span><span class="sxs-lookup"><span data-stu-id="acb73-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="acb73-117">Você usar o nome do parâmetro da mesma maneira que você usar qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="acb73-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="acb73-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="acb73-118">Arguments</span></span>  
 <span data-ttu-id="acb73-119">Um *argumento* representa o valor que você passa para um parâmetro de procedimento quando você chamar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="acb73-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="acb73-120">O código de chamada fornece os argumentos quando ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="acb73-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="acb73-121">Quando você chama um `Function` ou `Sub` procedimento, você incluir um *lista de argumentos* entre parênteses imediatamente após o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="acb73-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="acb73-122">Cada argumento corresponde ao parâmetro na mesma posição na lista.</span><span class="sxs-lookup"><span data-stu-id="acb73-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="acb73-123">Em contraste com a definição de parâmetro, os argumentos não têm nomes.</span><span class="sxs-lookup"><span data-stu-id="acb73-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="acb73-124">Cada argumento é uma expressão, que pode conter zero ou mais variáveis, constantes e literais.</span><span class="sxs-lookup"><span data-stu-id="acb73-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="acb73-125">O tipo de dados da expressão avaliada normalmente deve corresponder ao tipo de dados definido para o parâmetro correspondente e, em qualquer caso deve ser conversível para o tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="acb73-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb73-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acb73-126">See Also</span></span>  
 [<span data-ttu-id="acb73-127">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="acb73-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="acb73-128">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="acb73-128">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="acb73-129">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="acb73-129">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="acb73-130">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="acb73-130">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="acb73-131">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="acb73-131">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="acb73-132">Como definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="acb73-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="acb73-133">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="acb73-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="acb73-134">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="acb73-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="acb73-135">Procedimentos Recursivos</span><span class="sxs-lookup"><span data-stu-id="acb73-135">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="acb73-136">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="acb73-136">Procedure Overloading</span></span>](./procedure-overloading.md)
