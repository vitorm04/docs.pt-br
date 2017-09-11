---
title: "Parâmetros de procedimento e argumentos (Visual Basic) | Documentos do Microsoft"
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
- procedures, argument lists
- values, passing to procedures
- arguments [Visual Basic], passing
- procedures, parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters, Visual Basic procedures
- parameters, lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists
- Visual Basic code, parameter lists
- argument lists
- procedures, parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: 21
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
ms.openlocfilehash: d9df621a933de31e725b2dff54650a50193f0b55
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="66d3d-102">Parâmetros e argumentos de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66d3d-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="66d3d-103">Na maioria dos casos, um procedimento precisa de algumas informações sobre as circunstâncias em que ele foi chamado.</span><span class="sxs-lookup"><span data-stu-id="66d3d-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="66d3d-104">Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.</span><span class="sxs-lookup"><span data-stu-id="66d3d-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="66d3d-105">Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="66d3d-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="66d3d-106">A *parâmetro* representa um valor que o procedimento espera que você forneça quando você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="66d3d-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="66d3d-107">Declaração do procedimento define seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="66d3d-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="66d3d-108">Você pode definir um procedimento com sem parâmetros, um parâmetro ou mais de um.</span><span class="sxs-lookup"><span data-stu-id="66d3d-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="66d3d-109">A parte da definição do procedimento que especifica os parâmetros é chamada de *lista de parâmetros*.</span><span class="sxs-lookup"><span data-stu-id="66d3d-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="66d3d-110">Um *argumento* representa o valor fornecido para um parâmetro de procedimento quando você chamar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="66d3d-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="66d3d-111">O código de chamada fornece os argumentos quando ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="66d3d-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="66d3d-112">A parte da chamada de procedimento que especifica os argumentos é chamada de *lista de argumentos*.</span><span class="sxs-lookup"><span data-stu-id="66d3d-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="66d3d-113">A ilustração a seguir mostra código chamando o procedimento `safeSquareRoot` de dois lugares diferentes.</span><span class="sxs-lookup"><span data-stu-id="66d3d-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="66d3d-114">A primeira chamada passa o valor da variável `x` (4.0) para o parâmetro `number`e o valor de retorno em `root` (2.0) é atribuído à variável `y`.</span><span class="sxs-lookup"><span data-stu-id="66d3d-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="66d3d-115">A segunda chamada passa o valor literal 9.0 para `number`e atribui o valor de retorno (3.0) à variável `z`.</span><span class="sxs-lookup"><span data-stu-id="66d3d-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="66d3d-116">![Diagrama de gráfico de passagem de argumento para o parâmetro](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="66d3d-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="66d3d-117">Passar um argumento para um parâmetro</span><span class="sxs-lookup"><span data-stu-id="66d3d-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="66d3d-118">Para obter mais informações, consulte [as diferenças entre parâmetros e argumentos](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="66d3d-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="66d3d-119">Tipo de dados do parâmetro</span><span class="sxs-lookup"><span data-stu-id="66d3d-119">Parameter Data Type</span></span>  
 <span data-ttu-id="66d3d-120">Definir um tipo de dados para um parâmetro usando o `As` cláusula na sua declaração.</span><span class="sxs-lookup"><span data-stu-id="66d3d-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="66d3d-121">Por exemplo, a seguinte função aceita uma cadeia de caracteres e um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="66d3d-121">For example, the following function accepts a string and an integer.</span></span>  
  
 <span data-ttu-id="66d3d-122">[!code-vb[32 VbVbcnProcedures](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="66d3d-122">[!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]</span></span>  
  
 <span data-ttu-id="66d3d-123">Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off,` de `As` cláusula é opcional, exceto que se qualquer outro parâmetro usa a ele, todos os parâmetros devem usá-lo.</span><span class="sxs-lookup"><span data-stu-id="66d3d-123">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="66d3d-124">Se a verificação de tipo é `On`, o `As` cláusula é necessária para todos os parâmetros de procedimento.</span><span class="sxs-lookup"><span data-stu-id="66d3d-124">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="66d3d-125">Se o código de chamada espera fornecer um argumento com um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para um `String` parâmetro, ele deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="66d3d-125">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="66d3d-126">Forneça apenas os argumentos com tipos de dados que ampliam para o tipo de dados do parâmetro;</span><span class="sxs-lookup"><span data-stu-id="66d3d-126">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="66d3d-127">Defina `Option Strict Off` para permitir conversões de estreitamento implícitas; ou</span><span class="sxs-lookup"><span data-stu-id="66d3d-127">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="66d3d-128">Use uma palavra-chave de conversão para converter explicitamente o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="66d3d-128">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="66d3d-129">Parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="66d3d-129">Type Parameters</span></span>  
 <span data-ttu-id="66d3d-130">A *procedimento genérico* também define um ou mais *parâmetros de tipo* além de seus parâmetros normais.</span><span class="sxs-lookup"><span data-stu-id="66d3d-130">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="66d3d-131">Um procedimento genérico permite que o código de chamada passe diferentes tipos de dados cada vez que ele chama o procedimento, portanto ele pode personalizar os tipos de dados para os requisitos de cada chamada individual.</span><span class="sxs-lookup"><span data-stu-id="66d3d-131">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="66d3d-132">Consulte [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="66d3d-132">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d3d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66d3d-133">See Also</span></span>  
 <span data-ttu-id="66d3d-134">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="66d3d-135"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-135"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="66d3d-136"> [Procedimentos de função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-136"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="66d3d-137"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-137"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="66d3d-138"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-138"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="66d3d-139"> [Como: definir um parâmetro para um procedimento](./how-to-define-a-parameter-for-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-139"> [How to: Define a Parameter for a Procedure](./how-to-define-a-parameter-for-a-procedure.md) </span></span>  
<span data-ttu-id="66d3d-140"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-140"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="66d3d-141"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-141"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="66d3d-142"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="66d3d-142"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="66d3d-143"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="66d3d-143"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)</span></span>
