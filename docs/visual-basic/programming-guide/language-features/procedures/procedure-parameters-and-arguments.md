---
title: Parâmetros e argumentos de procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 80065cabcacdcf44b04fef7bacb978ca9c8077ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825450"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="c7dfd-102">Parâmetros e argumentos de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7dfd-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="c7dfd-103">Na maioria dos casos, um procedimento precisa de algumas informações sobre as circunstâncias em que ele tiver sido chamado.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="c7dfd-104">Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="c7dfd-105">Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento quando você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="c7dfd-106">Um *parâmetro* representa um valor que o procedimento espera que você forneça quando você chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="c7dfd-107">Declaração do procedimento define seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="c7dfd-108">Você pode definir um procedimento sem parâmetros, um parâmetro ou mais de um.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="c7dfd-109">A parte da definição do procedimento que especifica os parâmetros é chamada de *lista de parâmetros*.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="c7dfd-110">Uma *argumento* representa o valor fornecido para um parâmetro de procedimento quando você chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="c7dfd-111">O código de chamada fornece os argumentos quando ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="c7dfd-112">A parte da chamada de procedimento que especifica os argumentos é chamada a *lista de argumentos*.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="c7dfd-113">A ilustração a seguir mostra o código chamando o procedimento `safeSquareRoot` de dois locais diferentes.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="c7dfd-114">A primeira chamada passa o valor da variável `x` (4.0) para o parâmetro `number`e o valor de retorno `root` (2.0) é atribuído à variável `y`.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="c7dfd-115">A segunda chamada passa o valor literal 9.0 para `number`e atribui o valor de retorno (3.0) à variável `z`.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagrama que mostra a passar um argumento para um parâmetro](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="c7dfd-117">Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c7dfd-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="c7dfd-118">Tipo de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="c7dfd-118">Parameter Data Type</span></span>  
 <span data-ttu-id="c7dfd-119">Você define um tipo de dados para um parâmetro usando o `As` cláusula na sua declaração.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="c7dfd-120">Por exemplo, a seguinte função aceita uma cadeia de caracteres e um inteiro.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="c7dfd-121">Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off,` o `As` cláusula é opcional, exceto que, se qualquer outro parâmetro usa a ele, todos os parâmetros devem usá-lo.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="c7dfd-122">Se a verificação de tipo está `On`, o `As` cláusula é necessária para todos os parâmetros de procedimento.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="c7dfd-123">Se o código de chamada espera que fornecer um argumento com um tipo de dados diferente do seu parâmetro correspondente, tal como `Byte` para um `String` parâmetro, ele deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c7dfd-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="c7dfd-124">Forneça apenas os argumentos com tipos de dados ampliam com o tipo de dados de parâmetro;</span><span class="sxs-lookup"><span data-stu-id="c7dfd-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="c7dfd-125">Definir `Option Strict Off` para permitir conversões de estreitamento implícitas; ou</span><span class="sxs-lookup"><span data-stu-id="c7dfd-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="c7dfd-126">Use uma palavra-chave de conversão para converter explicitamente o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="c7dfd-127">Parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="c7dfd-127">Type Parameters</span></span>  
 <span data-ttu-id="c7dfd-128">Um *procedimento genérico* também define um ou mais *parâmetros de tipo* , além de seus parâmetros normais.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="c7dfd-129">Um procedimento genérico permite que o código de chamada passar diferentes tipos de dados cada vez que ele chama o procedimento, portanto, ele pode personalizar os tipos de dados para os requisitos de cada chamada individual.</span><span class="sxs-lookup"><span data-stu-id="c7dfd-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="c7dfd-130">Ver [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c7dfd-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7dfd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7dfd-131">See also</span></span>

- [<span data-ttu-id="c7dfd-132">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c7dfd-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c7dfd-133">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="c7dfd-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="c7dfd-134">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="c7dfd-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="c7dfd-135">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="c7dfd-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="c7dfd-136">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="c7dfd-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c7dfd-137">Como: Definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="c7dfd-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="c7dfd-138">Como: Passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="c7dfd-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="c7dfd-139">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="c7dfd-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c7dfd-140">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="c7dfd-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="c7dfd-141">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7dfd-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
