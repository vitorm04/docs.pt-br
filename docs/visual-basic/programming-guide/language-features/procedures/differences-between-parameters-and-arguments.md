---
title: "Diferenças entre parâmetros e argumentos (Visual Basic) | Documentos do Microsoft"
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
- procedures, arguments
- procedures, parameters
- parameters, and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters, definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: 18
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
ms.openlocfilehash: c9226293a1d996f0e3795cced91d492cab2207f7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="7075a-102">Diferenças entre parâmetros e argumentos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7075a-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="7075a-103">Na maioria dos casos, um procedimento deve ter algumas informações sobre as circunstâncias em que ele foi chamado.</span><span class="sxs-lookup"><span data-stu-id="7075a-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="7075a-104">Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.</span><span class="sxs-lookup"><span data-stu-id="7075a-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="7075a-105">Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="7075a-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="7075a-106">Para se comunicar essas informações para o procedimento, o procedimento define uma *parâmetro*, e o código de chamada passa um *argumento* para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7075a-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="7075a-107">Você pode considerar o parâmetro como um espaço de estacionamento e o argumento de um automóvel.</span><span class="sxs-lookup"><span data-stu-id="7075a-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="7075a-108">Assim como automóveis diferentes podem estaciono em um espaço de estacionamento em momentos diferentes, o código de chamada pode passar um argumento diferente para o mesmo parâmetro toda vez que ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="7075a-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="7075a-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7075a-109">Parameters</span></span>  
 <span data-ttu-id="7075a-110">A *parâmetro* representa um valor que o procedimento espera que você passe quando você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="7075a-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="7075a-111">Declaração do procedimento define seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7075a-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="7075a-112">Quando você define uma `Function` ou `Sub` procedimento, você especificar um *lista de parâmetros* entre parênteses imediatamente após o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="7075a-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="7075a-113">Para cada parâmetro, você especificar um nome, um tipo de dados e um mecanismo de passagem ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="7075a-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="7075a-114">Você também pode indicar que um parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="7075a-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="7075a-115">Isso significa que o código de chamada não precisa passar um valor para ela.</span><span class="sxs-lookup"><span data-stu-id="7075a-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="7075a-116">O nome de cada parâmetro serve como um *variável local* no procedimento.</span><span class="sxs-lookup"><span data-stu-id="7075a-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="7075a-117">Você usar o nome do parâmetro da mesma maneira que você usar qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="7075a-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="7075a-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="7075a-118">Arguments</span></span>  
 <span data-ttu-id="7075a-119">Um *argumento* representa o valor que você passa para um parâmetro de procedimento quando você chamar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="7075a-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="7075a-120">O código de chamada fornece os argumentos quando ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="7075a-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="7075a-121">Quando você chama um `Function` ou `Sub` procedimento, você incluir um *lista de argumentos* entre parênteses imediatamente após o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="7075a-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="7075a-122">Cada argumento corresponde ao parâmetro na mesma posição na lista.</span><span class="sxs-lookup"><span data-stu-id="7075a-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="7075a-123">Em contraste com a definição do parâmetro, argumentos não têm nomes.</span><span class="sxs-lookup"><span data-stu-id="7075a-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="7075a-124">Cada argumento é uma expressão, que pode conter zero ou mais variáveis, constantes e literais.</span><span class="sxs-lookup"><span data-stu-id="7075a-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="7075a-125">O tipo de dados da expressão avaliada normalmente deve corresponder ao tipo de dados definido para o parâmetro correspondente e, em qualquer caso deve ser conversível para o tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7075a-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7075a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7075a-126">See Also</span></span>  
 <span data-ttu-id="7075a-127">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-127">[Procedures](./index.md) </span></span>  
<span data-ttu-id="7075a-128"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-128"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="7075a-129"> [Procedimentos de função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-129"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="7075a-130"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-130"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="7075a-131"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-131"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="7075a-132"> [Como: definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-132"> [How to: Define a Parameter for a Procedure](./how-to-define-a-parameter-for-a-procedure.md) </span></span>  
<span data-ttu-id="7075a-133"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-133"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="7075a-134"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-134"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="7075a-135"> [Procedimentos recursivos](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7075a-135"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="7075a-136"> [Sobrecarga de Procedimento](./procedure-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="7075a-136"> [Procedure Overloading](./procedure-overloading.md)</span></span>
