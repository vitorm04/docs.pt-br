---
title: Como passar argumentos para um procedimento
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
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387771"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="eb535-102">Como passar argumentos para um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb535-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="eb535-103">Ao chamar um procedimento, você segue o nome do procedimento com uma lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="eb535-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="eb535-104">Você fornece um argumento correspondente a cada parâmetro necessário que o procedimento define e, opcionalmente, pode fornecer argumentos para os `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="eb535-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="eb535-105">Se você não fornecer um `Optional` parâmetro na chamada, deverá incluir uma vírgula para marcar seu lugar na lista de argumentos, se você estiver fornecendo argumentos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="eb535-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="eb535-106">Se você pretende passar um argumento de um tipo de dados diferente daquele de seu parâmetro correspondente, como `Byte` para `String` , você pode definir a opção de verificação de tipo ([instrução Option Strict](../../../language-reference/statements/option-strict-statement.md)) para `Off` .</span><span class="sxs-lookup"><span data-stu-id="eb535-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="eb535-107">Se `Option Strict` for `On` , você deve usar conversões de alargamento ou palavras-chave de conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="eb535-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="eb535-108">Para obter mais informações, consulte [conversões de ampliação e estreitamento](../data-types/widening-and-narrowing-conversions.md) e [funções de conversão de tipo](../../../language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="eb535-108">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="eb535-109">Para obter mais informações, consulte [parâmetros e argumentos de procedimento](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="eb535-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="eb535-110">Para passar um ou mais argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="eb535-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="eb535-111">Na instrução de chamada, siga o nome do procedimento com parênteses.</span><span class="sxs-lookup"><span data-stu-id="eb535-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="eb535-112">Dentro dos parênteses, coloque uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="eb535-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="eb535-113">Inclua um argumento para cada parâmetro necessário que o procedimento define e separe os argumentos com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="eb535-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="eb535-114">Certifique-se de que cada argumento é uma expressão válida que é avaliada como um tipo de dados conversível para o tipo que o procedimento define para o parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="eb535-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="eb535-115">Se um parâmetro for definido como [opcional](../../../language-reference/modifiers/optional.md), você poderá incluí-lo na lista de argumentos ou omiti-lo.</span><span class="sxs-lookup"><span data-stu-id="eb535-115">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="eb535-116">Se você omiti-lo, o procedimento usará o valor padrão definido para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="eb535-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="eb535-117">Se você omitir um argumento para um `Optional` parâmetro e houver outro parâmetro depois dele na lista de parâmetros, você poderá marcar o lugar do argumento omitido por uma vírgula extra na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="eb535-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="eb535-118">O exemplo a seguir chama a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> função Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb535-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="eb535-119">O exemplo anterior fornece o primeiro argumento necessário, que é a cadeia de caracteres da mensagem a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="eb535-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="eb535-120">Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eb535-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="eb535-121">Como a chamada não fornece um valor, `MsgBox` o usa o valor padrão, `MsgBoxStyle.OKOnly` , que exibe apenas um botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="eb535-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="eb535-122">A segunda vírgula na lista de argumentos marca o lugar do segundo argumento omitido e a última cadeia de caracteres é passada para o terceiro parâmetro opcional de `MsgBox` , que é o texto a ser exibido na barra de título.</span><span class="sxs-lookup"><span data-stu-id="eb535-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb535-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb535-123">See also</span></span>

- [<span data-ttu-id="eb535-124">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="eb535-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="eb535-125">Procedimentos de função</span><span class="sxs-lookup"><span data-stu-id="eb535-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="eb535-126">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="eb535-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="eb535-127">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="eb535-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="eb535-128">Como definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="eb535-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="eb535-129">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="eb535-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="eb535-130">Procedimentos recursivos</span><span class="sxs-lookup"><span data-stu-id="eb535-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="eb535-131">Sobrecarga de procedimento</span><span class="sxs-lookup"><span data-stu-id="eb535-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="eb535-132">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="eb535-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="eb535-133">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb535-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
