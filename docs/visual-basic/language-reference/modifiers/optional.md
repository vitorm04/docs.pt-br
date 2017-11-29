---
title: Opcional (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a><span data-ttu-id="86893-102">Opcional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86893-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="86893-103">Especifica que um argumento de procedimento pode ser omitido quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="86893-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86893-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="86893-104">Remarks</span></span>  
 <span data-ttu-id="86893-105">Para cada parâmetro opcional, você deve especificar uma expressão constante como o valor padrão desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="86893-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="86893-106">Se a expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o valor padrão do tipo de dados de valor é usado como o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="86893-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="86893-107">Se a lista de parâmetros contém um parâmetro opcional, cada parâmetro que o segue também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="86893-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="86893-108">O `Optional` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="86893-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="86893-109">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="86893-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="86893-110">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="86893-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="86893-111">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="86893-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="86893-112">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="86893-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="86893-113">Ao chamar um procedimento com ou sem parâmetros opcionais, você pode passar argumentos por posição ou por nome.</span><span class="sxs-lookup"><span data-stu-id="86893-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="86893-114">Para obter mais informações, consulte [passando argumentos por posição e nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="86893-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86893-115">Você também pode definir um procedimento com parâmetros opcionais usando a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="86893-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="86893-116">Se você tiver um parâmetro opcional, você pode definir duas versões sobrecarregadas do procedimento, uma que aceita o parâmetro e um que não.</span><span class="sxs-lookup"><span data-stu-id="86893-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="86893-117">Para obter mais informações, consulte [sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="86893-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86893-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86893-118">Example</span></span>  
 <span data-ttu-id="86893-119">O exemplo a seguir define um procedimento que tem um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="86893-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="86893-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86893-120">Example</span></span>  
 <span data-ttu-id="86893-121">O exemplo a seguir demonstra como chamar um procedimento com os argumentos transmitidos por posição e argumentos passados pelo nome.</span><span class="sxs-lookup"><span data-stu-id="86893-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="86893-122">O procedimento tem dois parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="86893-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="86893-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86893-123">See Also</span></span>  
 [<span data-ttu-id="86893-124">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86893-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="86893-125">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="86893-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="86893-126">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="86893-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
