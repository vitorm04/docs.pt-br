---
title: Como passar argumentos para um procedimento (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e8f8e438dc749e7f5f0d33aeaa26dfbcf4c29f3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="09157-102">Como passar argumentos para um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09157-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="09157-103">Quando você chama um procedimento, você pode seguir o nome do procedimento com uma lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="09157-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="09157-104">Forneça um argumento correspondente a cada parâmetro necessário que o procedimento define, e, opcionalmente, você pode fornecer argumentos para o `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="09157-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="09157-105">Se você não fornecer um `Optional` parâmetro na chamada, você deve incluir uma vírgula para marcar seu lugar na lista de argumentos, se você estiver fornecendo argumentos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="09157-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="09157-106">Se você pretende passar um argumento de um tipo de dados diferente do seu parâmetro correspondente, como `Byte` para `String`, você pode definir a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) para `Off`.</span><span class="sxs-lookup"><span data-stu-id="09157-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="09157-107">Se `Option Strict` é `On`, você deve usar conversões ampliadoras ou palavras-chave de conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="09157-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="09157-108">Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="09157-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="09157-109">Para obter mais informações, consulte [argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="09157-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="09157-110">Para passar um ou mais argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="09157-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="09157-111">Na instrução de chamada, siga o nome do procedimento com parênteses.</span><span class="sxs-lookup"><span data-stu-id="09157-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="09157-112">Dentro dos parênteses, coloque uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="09157-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="09157-113">Incluir um argumento para cada parâmetro necessário que o procedimento define e separe-os com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="09157-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="09157-114">Verifique se que cada argumento é uma expressão válida que é avaliada como um tipo de dados conversível para o tipo de procedimento define para o parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="09157-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="09157-115">Se um parâmetro for definido como [opcional](../../../../visual-basic/language-reference/modifiers/optional.md), você pode incluí-lo na lista de argumentos ou omiti-lo.</span><span class="sxs-lookup"><span data-stu-id="09157-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="09157-116">Se você omiti-lo, o procedimento usa o valor padrão definido para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="09157-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="09157-117">Se você omitir um argumento para um `Optional` parâmetro e houver outro parâmetro depois, na lista de parâmetros, você pode marcar o local do argumento omitido por uma vírgula extra na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="09157-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="09157-118">O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> função.</span><span class="sxs-lookup"><span data-stu-id="09157-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     <span data-ttu-id="09157-119">O exemplo anterior fornece o primeiro argumento necessário, que é a cadeia de caracteres de mensagem a ser exibida.</span><span class="sxs-lookup"><span data-stu-id="09157-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="09157-120">Ele omite um argumento para o segundo parâmetro opcional, que especifica os botões a serem exibidos na caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="09157-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="09157-121">Como a chamada não fornece um valor, `MsgBox` usa o valor padrão, `MsgBoxStyle.OKOnly`, que exibe apenas uma **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="09157-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="09157-122">A segunda vírgula na lista de argumentos marca o local do segundo argumento omitido, e a última cadeia de caracteres é passada para o terceiro parâmetro opcional de `MsgBox`, que é o texto a ser exibido na barra de título.</span><span class="sxs-lookup"><span data-stu-id="09157-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09157-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09157-123">See also</span></span>

 [<span data-ttu-id="09157-124">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="09157-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="09157-125">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="09157-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="09157-126">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="09157-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="09157-127">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="09157-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="09157-128">Como definir um parâmetro para um procedimento</span><span class="sxs-lookup"><span data-stu-id="09157-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="09157-129">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="09157-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="09157-130">Procedimentos Recursivos</span><span class="sxs-lookup"><span data-stu-id="09157-130">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="09157-131">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="09157-131">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="09157-132">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="09157-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="09157-133">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09157-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
