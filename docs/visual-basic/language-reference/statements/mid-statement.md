---
title: Instrução mid (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963544"
---
# <a name="mid-statement"></a><span data-ttu-id="a2a42-102">Instrução Mid</span><span class="sxs-lookup"><span data-stu-id="a2a42-102">Mid Statement</span></span>
<span data-ttu-id="a2a42-103">Substitui um número especificado de caracteres em uma `String` variável por caracteres de outra cadeia de caractere.</span><span class="sxs-lookup"><span data-stu-id="a2a42-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2a42-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="a2a42-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a2a42-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="a2a42-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a2a42-106">Required.</span></span> <span data-ttu-id="a2a42-107">Nome da `String` variável a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="a2a42-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="a2a42-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a2a42-108">Required.</span></span> <span data-ttu-id="a2a42-109">Expressão `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a2a42-109">`Integer` expression.</span></span> <span data-ttu-id="a2a42-110">Posição do caractere `Target` em que começa a substituição do texto.</span><span class="sxs-lookup"><span data-stu-id="a2a42-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="a2a42-111">`Start`usa um índice baseado em um.</span><span class="sxs-lookup"><span data-stu-id="a2a42-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="a2a42-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a2a42-112">Optional.</span></span> <span data-ttu-id="a2a42-113">Expressão `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a2a42-113">`Integer` expression.</span></span> <span data-ttu-id="a2a42-114">Número de caracteres a serem substituídos.</span><span class="sxs-lookup"><span data-stu-id="a2a42-114">Number of characters to replace.</span></span> <span data-ttu-id="a2a42-115">Se omitido, todos `String` serão usados.</span><span class="sxs-lookup"><span data-stu-id="a2a42-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="a2a42-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a2a42-116">Required.</span></span> <span data-ttu-id="a2a42-117">`String`expressão que substitui parte de `Target`.</span><span class="sxs-lookup"><span data-stu-id="a2a42-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="a2a42-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="a2a42-118">Exceptions</span></span>  
  
|<span data-ttu-id="a2a42-119">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="a2a42-119">Exception type</span></span>|<span data-ttu-id="a2a42-120">Condição</span><span class="sxs-lookup"><span data-stu-id="a2a42-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="a2a42-121">`Start` <= 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="a2a42-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2a42-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2a42-122">Remarks</span></span>  
 <span data-ttu-id="a2a42-123">O número de caracteres substituídos é sempre menor ou igual ao número de caracteres em `Target`.</span><span class="sxs-lookup"><span data-stu-id="a2a42-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="a2a42-124">Visual Basic tem uma <xref:Microsoft.VisualBasic.Strings.Mid%2A> função e uma `Mid` instrução.</span><span class="sxs-lookup"><span data-stu-id="a2a42-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="a2a42-125">Esses elementos operam em um número especificado de caracteres em uma cadeia de caracteres, `Mid` mas a função retorna os caracteres `Mid` enquanto a instrução substitui os caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2a42-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="a2a42-126">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2a42-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2a42-127">A `MidB` instrução das versões anteriores do Visual Basic substitui uma Subcadeia em bytes, em vez de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2a42-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="a2a42-128">Ele é usado principalmente para converter cadeias de caracteres em aplicativos DBCS.</span><span class="sxs-lookup"><span data-stu-id="a2a42-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="a2a42-129">Todas as cadeias de caracteres Visual Basic estão `MidB` em Unicode e não têm mais suporte.</span><span class="sxs-lookup"><span data-stu-id="a2a42-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2a42-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2a42-130">Example</span></span>  
 <span data-ttu-id="a2a42-131">Este exemplo usa a `Mid` instrução para substituir um número especificado de caracteres em uma variável String por caracteres de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a2a42-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="a2a42-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2a42-132">Requirements</span></span>  
 <span data-ttu-id="a2a42-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="a2a42-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="a2a42-134">**Módulo:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="a2a42-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="a2a42-135">**)** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="a2a42-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a42-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2a42-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="a2a42-137">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="a2a42-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="a2a42-138">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2a42-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
