---
title: Parâmetros e argumentos de procedimento
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
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352578"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="25392-102">Parâmetros e argumentos de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25392-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="25392-103">Na maioria dos casos, um procedimento precisa de algumas informações sobre as circunstâncias em que ele foi chamado.</span><span class="sxs-lookup"><span data-stu-id="25392-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="25392-104">Um procedimento que executa tarefas repetidas ou compartilhadas usa informações diferentes para cada chamada.</span><span class="sxs-lookup"><span data-stu-id="25392-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="25392-105">Essas informações consistem em variáveis, constantes e expressões que você passa para o procedimento ao chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="25392-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="25392-106">Um *parâmetro* representa um valor que o procedimento espera que você forneça ao chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="25392-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="25392-107">A declaração do procedimento define seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="25392-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="25392-108">Você pode definir um procedimento sem parâmetros, um parâmetro ou mais de um.</span><span class="sxs-lookup"><span data-stu-id="25392-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="25392-109">A parte da definição do procedimento que especifica os parâmetros é chamada de *lista de parâmetros*.</span><span class="sxs-lookup"><span data-stu-id="25392-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="25392-110">Um *argumento* representa o valor que você fornece a um parâmetro de procedimento ao chamar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="25392-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="25392-111">O código de chamada fornece os argumentos ao chamar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="25392-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="25392-112">A parte da chamada de procedimento que especifica os argumentos é chamada de *lista de argumentos*.</span><span class="sxs-lookup"><span data-stu-id="25392-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="25392-113">A ilustração a seguir mostra o código que chama o procedimento `safeSquareRoot` de dois locais diferentes.</span><span class="sxs-lookup"><span data-stu-id="25392-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="25392-114">A primeira chamada passa o valor da variável `x` (4,0) para o parâmetro `number`e o valor de retorno em `root` (2,0) é atribuído à variável `y`.</span><span class="sxs-lookup"><span data-stu-id="25392-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="25392-115">A segunda chamada passa o valor literal 9,0 para `number`e atribui o valor de retorno (3,0) à variável `z`.</span><span class="sxs-lookup"><span data-stu-id="25392-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagrama que mostra a passagem de um argumento para um parâmetro](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="25392-117">Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="25392-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="25392-118">Tipo de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="25392-118">Parameter Data Type</span></span>  
 <span data-ttu-id="25392-119">Você define um tipo de dados para um parâmetro usando a cláusula `As` em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="25392-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="25392-120">Por exemplo, a função a seguir aceita uma cadeia de caracteres e um inteiro.</span><span class="sxs-lookup"><span data-stu-id="25392-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="25392-121">Se a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) for `Off,` a cláusula `As` for opcional, exceto que, se qualquer parâmetro usar, todos os parâmetros deverão usá-lo.</span><span class="sxs-lookup"><span data-stu-id="25392-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="25392-122">Se a verificação de tipo for `On`, a cláusula `As` será necessária para todos os parâmetros de procedimento.</span><span class="sxs-lookup"><span data-stu-id="25392-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="25392-123">Se o código de chamada espera fornecer um argumento com um tipo de dados diferente daquele de seu parâmetro correspondente, como `Byte` para um parâmetro `String`, ele deve executar um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="25392-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="25392-124">Forneça somente argumentos com tipos de dados que ampliam para o tipo de dados de parâmetro;</span><span class="sxs-lookup"><span data-stu-id="25392-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="25392-125">Defina `Option Strict Off` para permitir conversões de estreitamento implícitas; or</span><span class="sxs-lookup"><span data-stu-id="25392-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="25392-126">Use uma palavra-chave de conversão para converter explicitamente o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="25392-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="25392-127">Parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="25392-127">Type Parameters</span></span>  
 <span data-ttu-id="25392-128">Um *procedimento genérico* também define um ou mais *parâmetros de tipo* , além de seus parâmetros normais.</span><span class="sxs-lookup"><span data-stu-id="25392-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="25392-129">Um procedimento genérico permite que o código de chamada passe tipos de dados diferentes cada vez que chama o procedimento, para que possa personalizar os tipos de dados para os requisitos de cada chamada individual.</span><span class="sxs-lookup"><span data-stu-id="25392-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="25392-130">Consulte [procedimentos genéricos em Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="25392-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25392-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25392-131">See also</span></span>

- [<span data-ttu-id="25392-132">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="25392-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="25392-133">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="25392-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="25392-134">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="25392-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="25392-135">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="25392-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="25392-136">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="25392-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="25392-137">Como definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="25392-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="25392-138">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="25392-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="25392-139">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="25392-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="25392-140">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="25392-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="25392-141">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25392-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
