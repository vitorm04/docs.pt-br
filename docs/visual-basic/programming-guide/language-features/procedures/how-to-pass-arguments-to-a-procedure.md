---
title: 'Como: Passar argumentos para um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333899"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="d0caa-102">Como: Passar argumentos para um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0caa-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="d0caa-103">Quando você chama um procedimento, você pode seguir o nome do procedimento com uma lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d0caa-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="d0caa-104">Você fornece um argumento correspondente a cada parâmetro necessário que o procedimento define e, opcionalmente, você pode fornecer argumentos para o `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d0caa-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="d0caa-105">Se você não fornecer um `Optional` parâmetro na chamada, você deve incluir uma vírgula para marcar seu lugar na lista de argumentos, se você estiver fornecendo quaisquer argumentos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="d0caa-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="d0caa-106">Se você pretende passar um argumento de tipo de dados diferente do seu parâmetro correspondente, tal como `Byte` à `String`, você pode definir a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) para `Off`.</span><span class="sxs-lookup"><span data-stu-id="d0caa-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="d0caa-107">Se `Option Strict` é `On`, você deve usar conversões ampliadoras ou palavras-chave de conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="d0caa-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="d0caa-108">Para obter mais informações, consulte [ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d0caa-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="d0caa-109">Para obter mais informações, consulte [parâmetros de procedimento e os argumentos](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d0caa-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="d0caa-110">Para passar um ou mais argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="d0caa-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="d0caa-111">Na instrução de chamada, siga o nome do procedimento com parênteses.</span><span class="sxs-lookup"><span data-stu-id="d0caa-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="d0caa-112">Dentro dos parênteses, coloque uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d0caa-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="d0caa-113">Incluir um argumento para cada parâmetro necessário que o procedimento define e separe-os com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d0caa-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="d0caa-114">Verifique se que cada argumento é uma expressão válida que é avaliada como um tipo de dados conversível para o tipo de procedimento define para o parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="d0caa-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="d0caa-115">Se um parâmetro for definido como [opcional](../../../../visual-basic/language-reference/modifiers/optional.md), você pode incluí-lo na lista de argumentos ou omiti-lo.</span><span class="sxs-lookup"><span data-stu-id="d0caa-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="d0caa-116">Se você omiti-lo, o procedimento usa o valor padrão definido para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d0caa-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="d0caa-117">Se você omitir um argumento para um `Optional` parâmetro e houver outro parâmetro depois, na lista de parâmetros, você pode marcar o local do argumento omitido por uma vírgula extra na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d0caa-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="d0caa-118">O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> função.</span><span class="sxs-lookup"><span data-stu-id="d0caa-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="d0caa-119">O exemplo anterior fornece o primeiro argumento obrigatório, que é a cadeia de caracteres de mensagem a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="d0caa-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="d0caa-120">Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d0caa-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="d0caa-121">Como a chamada não fornece um valor `MsgBox` usa o valor padrão, `MsgBoxStyle.OKOnly`, que exibe apenas uma **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="d0caa-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="d0caa-122">A segunda vírgula na lista de argumentos marca o local do segundo argumento omitido, e a última cadeia de caracteres é passada para o terceiro parâmetro opcional de `MsgBox`, que é o texto a ser exibido na barra de título.</span><span class="sxs-lookup"><span data-stu-id="d0caa-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0caa-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0caa-123">See also</span></span>

- [<span data-ttu-id="d0caa-124">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="d0caa-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d0caa-125">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="d0caa-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d0caa-126">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="d0caa-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d0caa-127">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="d0caa-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d0caa-128">Como: definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="d0caa-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="d0caa-129">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="d0caa-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d0caa-130">Procedimentos recursivos</span><span class="sxs-lookup"><span data-stu-id="d0caa-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="d0caa-131">Sobrecarga de procedimento</span><span class="sxs-lookup"><span data-stu-id="d0caa-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="d0caa-132">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="d0caa-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="d0caa-133">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0caa-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
