---
title: Diferenças entre parâmetros e argumentos
ms.date: 07/20/2015
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
ms.openlocfilehash: 0ad9104f347205cebc6e078aac246a413c0d9b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057839"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="3291d-102">Diferenças entre parâmetros e argumentos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3291d-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="3291d-103">Na maioria dos casos, um procedimento deve ter algumas informações sobre as circunstâncias em que ele foi chamado.</span><span class="sxs-lookup"><span data-stu-id="3291d-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="3291d-104">Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.</span><span class="sxs-lookup"><span data-stu-id="3291d-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="3291d-105">Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento ao chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="3291d-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="3291d-106">Para comunicar essas informações ao procedimento, o procedimento define um *parâmetro*e o código de chamada passa um *argumento* para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3291d-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="3291d-107">Você pode considerar o parâmetro como um espaço de estacionamento e o argumento como um automóvel.</span><span class="sxs-lookup"><span data-stu-id="3291d-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="3291d-108">Assim como os automóveis diferentes podem estacionar em um espaço de estacionamento em momentos diferentes, o código de chamada pode passar um argumento diferente para o mesmo parâmetro toda vez que ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="3291d-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="3291d-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3291d-109">Parameters</span></span>  

 <span data-ttu-id="3291d-110">Um *parâmetro* representa um valor que o procedimento espera que você passe ao chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="3291d-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="3291d-111">A declaração do procedimento define seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3291d-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="3291d-112">Ao definir um `Function` procedimento ou `Sub` , você especifica uma *lista de parâmetros* entre parênteses imediatamente após o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="3291d-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="3291d-113">Para cada parâmetro, você especifica um nome, um tipo de dados e um mecanismo de passagem ([ByVal](../../../language-reference/modifiers/byval.md) ou [ByRef](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="3291d-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="3291d-114">Você também pode indicar que um parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="3291d-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="3291d-115">Isso significa que o código de chamada não precisa passar um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="3291d-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="3291d-116">O nome de cada parâmetro serve como uma *variável local* no procedimento.</span><span class="sxs-lookup"><span data-stu-id="3291d-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="3291d-117">Você usa o nome do parâmetro da mesma maneira que usa qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="3291d-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="3291d-118">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3291d-118">Arguments</span></span>  

 <span data-ttu-id="3291d-119">Um *argumento* representa o valor que você passa para um parâmetro de procedimento quando chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="3291d-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="3291d-120">O código de chamada fornece os argumentos ao chamar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="3291d-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="3291d-121">Ao chamar um `Function` procedimento ou `Sub` , você inclui uma *lista de argumentos* entre parênteses imediatamente após o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="3291d-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="3291d-122">Cada argumento corresponde ao parâmetro na mesma posição na lista.</span><span class="sxs-lookup"><span data-stu-id="3291d-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="3291d-123">Ao contrário da definição de parâmetro, os argumentos não têm nomes.</span><span class="sxs-lookup"><span data-stu-id="3291d-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="3291d-124">Cada argumento é uma expressão, que pode conter zero ou mais variáveis, constantes e literais.</span><span class="sxs-lookup"><span data-stu-id="3291d-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="3291d-125">O tipo de dados da expressão avaliada normalmente deve corresponder ao tipo de dados definido para o parâmetro correspondente e, em qualquer caso, ele deve ser conversível para o tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3291d-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3291d-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="3291d-126">See also</span></span>

- [<span data-ttu-id="3291d-127">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="3291d-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3291d-128">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="3291d-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="3291d-129">Procedimentos de função</span><span class="sxs-lookup"><span data-stu-id="3291d-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="3291d-130">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="3291d-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3291d-131">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="3291d-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="3291d-132">Como definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="3291d-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="3291d-133">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="3291d-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="3291d-134">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="3291d-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="3291d-135">Procedimentos recursivos</span><span class="sxs-lookup"><span data-stu-id="3291d-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="3291d-136">Sobrecarga de procedimento</span><span class="sxs-lookup"><span data-stu-id="3291d-136">Procedure Overloading</span></span>](./procedure-overloading.md)
