---
title: Parâmetros opcionais (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 4ae2366552426af0107c8d7a35bb5368fe30c8a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824670"
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="22f8c-102">Parâmetros opcionais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22f8c-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="22f8c-103">Você pode especificar que um parâmetro de procedimento é opcional e nenhum argumento precisa ser fornecido para ele quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="22f8c-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="22f8c-104">*Parâmetros opcionais* são indicados pelo `Optional` palavra-chave na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="22f8c-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="22f8c-105">As seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="22f8c-105">The following rules apply:</span></span>  
  
-   <span data-ttu-id="22f8c-106">Cada parâmetro opcional na definição do procedimento deve especificar um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="22f8c-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
-   <span data-ttu-id="22f8c-107">O valor padrão para um parâmetro opcional deve ser uma expressão constante.</span><span class="sxs-lookup"><span data-stu-id="22f8c-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
-   <span data-ttu-id="22f8c-108">Todo parâmetro após um parâmetro opcional na definição do procedimento também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="22f8c-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="22f8c-109">A sintaxe a seguir mostra uma declaração de procedimento com um parâmetro opcional:</span><span class="sxs-lookup"><span data-stu-id="22f8c-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="22f8c-110">Chamando procedimentos com parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="22f8c-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="22f8c-111">Ao chamar um procedimento com um parâmetro opcional, você pode escolher se deseja fornecer o argumento.</span><span class="sxs-lookup"><span data-stu-id="22f8c-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="22f8c-112">Caso contrário, o procedimento usa o valor padrão declarado para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="22f8c-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="22f8c-113">Ao omitir um ou mais argumentos opcionais no lista de argumentos, você use sucessivas vírgulas para marcar as posições.</span><span class="sxs-lookup"><span data-stu-id="22f8c-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="22f8c-114">A chamada de exemplo a seguir fornece o primeiro e o quarto argumentos, mas não o segundo ou terceiro:</span><span class="sxs-lookup"><span data-stu-id="22f8c-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="22f8c-115">O exemplo a seguir faz várias chamadas para a função `MsgBox`.</span><span class="sxs-lookup"><span data-stu-id="22f8c-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="22f8c-116">`MsgBox` tem um parâmetro obrigatório e dois parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="22f8c-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="22f8c-117">A primeira chamada para `MsgBox` fornece todos os três argumentos na ordem que `MsgBox` os define.</span><span class="sxs-lookup"><span data-stu-id="22f8c-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="22f8c-118">A segunda chamada fornece apenas o argumento necessário.</span><span class="sxs-lookup"><span data-stu-id="22f8c-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="22f8c-119">A terceira e a quarta chamadas fornecem o primeiro e o terceiro argumentos.</span><span class="sxs-lookup"><span data-stu-id="22f8c-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="22f8c-120">A terceira chamada faz isso por posição, e a quarta chamada faz isso por nome.</span><span class="sxs-lookup"><span data-stu-id="22f8c-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="22f8c-121">Determinando se um argumento opcional está presente</span><span class="sxs-lookup"><span data-stu-id="22f8c-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="22f8c-122">Um procedimento não pode detectar no tempo de execução se um determinado argumento foi omitido ou o código de chamada forneceu explicitamente o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="22f8c-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="22f8c-123">Se você precisar fazer essa distinção, defina um valor improvável como o padrão.</span><span class="sxs-lookup"><span data-stu-id="22f8c-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="22f8c-124">O procedimento a seguir define o parâmetro opcional `office`e testa seu valor padrão, `QJZ`, para ver se ele foi omitido na chamada:</span><span class="sxs-lookup"><span data-stu-id="22f8c-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 <span data-ttu-id="22f8c-125">Se o parâmetro opcional for um tipo de referência como `String`, você poderá usar `Nothing` como valor padrão, desde que não seja um valor esperado para o argumento.</span><span class="sxs-lookup"><span data-stu-id="22f8c-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="22f8c-126">Parâmetros opcionais e sobrecarga</span><span class="sxs-lookup"><span data-stu-id="22f8c-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="22f8c-127">Outra maneira de definir um procedimento com parâmetros opcionais é usar a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="22f8c-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="22f8c-128">Se você tiver um parâmetro opcional, poderá definir duas versões sobrecarregadas do procedimento, uma aceitando o parâmetro e outra sem ele.</span><span class="sxs-lookup"><span data-stu-id="22f8c-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="22f8c-129">Essa abordagem torna-se mais complicada à medida que o número de parâmetros opcionais aumenta.</span><span class="sxs-lookup"><span data-stu-id="22f8c-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="22f8c-130">No entanto, sua vantagem é que você pode ter certeza absoluta se o programa de chamada forneceu cada argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="22f8c-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f8c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f8c-131">See also</span></span>

- [<span data-ttu-id="22f8c-132">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="22f8c-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="22f8c-133">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="22f8c-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="22f8c-134">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="22f8c-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="22f8c-135">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="22f8c-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="22f8c-136">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22f8c-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="22f8c-137">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="22f8c-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="22f8c-138">Opcional</span><span class="sxs-lookup"><span data-stu-id="22f8c-138">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="22f8c-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="22f8c-139">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
