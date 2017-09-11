---
title: "Parâmetros opcionais (Visual Basic) | Documentos do Microsoft"
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
- parameters, optional
- Visual Basic code, procedures
- procedures, optional arguments
- optional arguments
- named arguments, and optional arguments
- optional parameters
- Optional keyword, optional arguments
- arguments [Visual Basic], optional
- optional arguments, and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: bdea022c50ef9aa8100581adc82aaf9c43a58772
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="6b19f-102">Parâmetros opcionais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b19f-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="6b19f-103">Você pode especificar que um parâmetro de procedimento é opcional e nenhum argumento precisa ser fornecido para ele quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="6b19f-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="6b19f-104">*Parâmetros opcionais* são indicadas pelo `Optional` palavra-chave na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="6b19f-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="6b19f-105">As seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="6b19f-105">The following rules apply:</span></span>  
  
-   <span data-ttu-id="6b19f-106">Cada parâmetro opcional na definição do procedimento deve especificar um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="6b19f-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
-   <span data-ttu-id="6b19f-107">O valor padrão para um parâmetro opcional deve ser uma expressão constante.</span><span class="sxs-lookup"><span data-stu-id="6b19f-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
-   <span data-ttu-id="6b19f-108">Todo parâmetro após um parâmetro opcional na definição do procedimento também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="6b19f-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="6b19f-109">A sintaxe a seguir mostra uma declaração de procedimento com um parâmetro opcional:</span><span class="sxs-lookup"><span data-stu-id="6b19f-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```  
Sub sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="6b19f-110">Chamando procedimentos com parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="6b19f-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="6b19f-111">Ao chamar um procedimento com um parâmetro opcional, você pode escolher se deseja fornecer o argumento.</span><span class="sxs-lookup"><span data-stu-id="6b19f-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="6b19f-112">Caso contrário, o procedimento usa o valor padrão declarado para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6b19f-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="6b19f-113">Ao omitir um ou mais argumentos opcionais no lista de argumentos, você use sucessivas vírgulas para marcar as posições.</span><span class="sxs-lookup"><span data-stu-id="6b19f-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="6b19f-114">A chamada de exemplo a seguir fornece o primeiro e o quarto argumentos, mas não o segundo ou terceiro:</span><span class="sxs-lookup"><span data-stu-id="6b19f-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```  
sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="6b19f-115">O exemplo a seguir faz várias chamadas para a função `MsgBox`.</span><span class="sxs-lookup"><span data-stu-id="6b19f-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="6b19f-116">`MsgBox` tem um parâmetro obrigatório e dois parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="6b19f-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="6b19f-117">A primeira chamada para `MsgBox` fornece todos os três argumentos na ordem que `MsgBox` os define.</span><span class="sxs-lookup"><span data-stu-id="6b19f-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="6b19f-118">A segunda chamada fornece apenas o argumento necessário.</span><span class="sxs-lookup"><span data-stu-id="6b19f-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="6b19f-119">A terceira e a quarta chamadas fornecem o primeiro e o terceiro argumentos.</span><span class="sxs-lookup"><span data-stu-id="6b19f-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="6b19f-120">A terceira chamada faz isso por posição, e a quarta chamada faz isso por nome.</span><span class="sxs-lookup"><span data-stu-id="6b19f-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 <span data-ttu-id="6b19f-121">[!code-vb[47 VbVbcnProcedures](./codesnippet/VisualBasic/optional-parameters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6b19f-121">[!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]</span></span>  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="6b19f-122">Determinando se um argumento opcional está presente</span><span class="sxs-lookup"><span data-stu-id="6b19f-122">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="6b19f-123">Um procedimento não pode detectar no tempo de execução se um determinado argumento foi omitido ou o código de chamada forneceu explicitamente o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="6b19f-123">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="6b19f-124">Se você precisar fazer essa distinção, defina um valor improvável como o padrão.</span><span class="sxs-lookup"><span data-stu-id="6b19f-124">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="6b19f-125">O procedimento a seguir define o parâmetro opcional `office`e testa seu valor padrão, `QJZ`, para ver se ele foi omitido na chamada:</span><span class="sxs-lookup"><span data-stu-id="6b19f-125">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 <span data-ttu-id="6b19f-126">[!code-vb[46 VbVbcnProcedures](./codesnippet/VisualBasic/optional-parameters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6b19f-126">[!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]</span></span>  
  
 <span data-ttu-id="6b19f-127">Se o parâmetro opcional for um tipo de referência como `String`, você poderá usar `Nothing` como valor padrão, desde que não seja um valor esperado para o argumento.</span><span class="sxs-lookup"><span data-stu-id="6b19f-127">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="6b19f-128">Parâmetros opcionais e sobrecarga</span><span class="sxs-lookup"><span data-stu-id="6b19f-128">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="6b19f-129">Outra maneira de definir um procedimento com parâmetros opcionais é usar a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="6b19f-129">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="6b19f-130">Se você tiver um parâmetro opcional, poderá definir duas versões sobrecarregadas do procedimento, uma aceitando o parâmetro e outra sem ele.</span><span class="sxs-lookup"><span data-stu-id="6b19f-130">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="6b19f-131">Essa abordagem torna-se mais complicada à medida que o número de parâmetros opcionais aumenta.</span><span class="sxs-lookup"><span data-stu-id="6b19f-131">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="6b19f-132">No entanto, sua vantagem é que você pode ter certeza absoluta se o programa de chamada forneceu cada argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="6b19f-132">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b19f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b19f-133">See Also</span></span>  
 <span data-ttu-id="6b19f-134">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="6b19f-135"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="6b19f-136"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-136"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="6b19f-137"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-137"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="6b19f-138"> [Matrizes de parâmetros](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-138"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="6b19f-139"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-139"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="6b19f-140"> [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) </span><span class="sxs-lookup"><span data-stu-id="6b19f-140"> [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) </span></span>  
<span data-ttu-id="6b19f-141"> [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)</span><span class="sxs-lookup"><span data-stu-id="6b19f-141"> [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)</span></span>

