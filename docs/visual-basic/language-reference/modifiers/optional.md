---
title: Opcional (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
dev_langs:
- VB
helpviewer_keywords:
- Optional keyword, contexts
- Optional keyword
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: 14
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
ms.openlocfilehash: cfda4c11616df7de853a82df8554f73916360915
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optional-visual-basic"></a><span data-ttu-id="b7418-102">Opcional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7418-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="b7418-103">Especifica que um argumento de procedimento pode ser omitido quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="b7418-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7418-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7418-104">Remarks</span></span>  
 <span data-ttu-id="b7418-105">Para cada parâmetro opcional, você deve especificar uma expressão constante como o valor padrão desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7418-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="b7418-106">Se a expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o valor padrão do tipo de dados valor é usado como o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7418-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="b7418-107">Se a lista de parâmetros contém um parâmetro opcional, cada parâmetro seguinte também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="b7418-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="b7418-108">O `Optional` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="b7418-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="b7418-109">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="b7418-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="b7418-110">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="b7418-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="b7418-111">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="b7418-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="b7418-112">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="b7418-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="b7418-113">Ao chamar um procedimento com ou sem parâmetros opcionais, você pode passar argumentos por posição ou por nome.</span><span class="sxs-lookup"><span data-stu-id="b7418-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="b7418-114">Para obter mais informações, consulte [passando argumentos por posição e nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="b7418-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7418-115">Você também pode definir um procedimento com parâmetros opcionais usando a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="b7418-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="b7418-116">Se você tiver um parâmetro opcional, você pode definir duas versões sobrecarregadas do procedimento, uma que aceita o parâmetro e um que não.</span><span class="sxs-lookup"><span data-stu-id="b7418-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="b7418-117">Para obter mais informações, consulte [sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="b7418-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7418-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7418-118">Example</span></span>  
 <span data-ttu-id="b7418-119">O exemplo a seguir define um procedimento com um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="b7418-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b7418-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7418-120">Example</span></span>  
 <span data-ttu-id="b7418-121">O exemplo a seguir demonstra como chamar um procedimento com os argumentos passados por posição e argumentos passados pelo nome.</span><span class="sxs-lookup"><span data-stu-id="b7418-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="b7418-122">O procedimento tem dois parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="b7418-122">The procedure has two optional parameters.</span></span>  
  
 <span data-ttu-id="b7418-123">[!code-vb[VbVbalrKeywords&#21;](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b7418-123">[!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7418-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7418-124">See Also</span></span>  
 <span data-ttu-id="b7418-125">[Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="b7418-125">[Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) </span></span>  
<span data-ttu-id="b7418-126"> [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="b7418-126"> [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span></span>  
<span data-ttu-id="b7418-127"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="b7418-127"> [Keywords](../../../visual-basic/language-reference/keywords/index.md)</span></span>
