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
ms.openlocfilehash: a653e63ded04616b6b0c6bdfb26a0a673d9299fc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084703"
---
# <a name="mid-statement"></a><span data-ttu-id="d4d97-102">Instrução Mid</span><span class="sxs-lookup"><span data-stu-id="d4d97-102">Mid Statement</span></span>
<span data-ttu-id="d4d97-103">Substitui um número especificado de caracteres em um `String` variável com caracteres de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d4d97-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4d97-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="d4d97-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d4d97-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="d4d97-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d4d97-106">Required.</span></span> <span data-ttu-id="d4d97-107">Nome da `String` variável para modificar.</span><span class="sxs-lookup"><span data-stu-id="d4d97-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="d4d97-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d4d97-108">Required.</span></span> <span data-ttu-id="d4d97-109">Expressão `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d4d97-109">`Integer` expression.</span></span> <span data-ttu-id="d4d97-110">Posição de caractere `Target` onde a substituição de texto começa.</span><span class="sxs-lookup"><span data-stu-id="d4d97-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="d4d97-111">`Start` usa um índice baseado em um.</span><span class="sxs-lookup"><span data-stu-id="d4d97-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="d4d97-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d4d97-112">Optional.</span></span> <span data-ttu-id="d4d97-113">Expressão `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d4d97-113">`Integer` expression.</span></span> <span data-ttu-id="d4d97-114">Número de caracteres a substituir.</span><span class="sxs-lookup"><span data-stu-id="d4d97-114">Number of characters to replace.</span></span> <span data-ttu-id="d4d97-115">Se omitido, todos os `String` é usado.</span><span class="sxs-lookup"><span data-stu-id="d4d97-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="d4d97-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d4d97-116">Required.</span></span> <span data-ttu-id="d4d97-117">`String` expressão que substitui parte de `Target`.</span><span class="sxs-lookup"><span data-stu-id="d4d97-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="d4d97-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="d4d97-118">Exceptions</span></span>  
  
|<span data-ttu-id="d4d97-119">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="d4d97-119">Exception type</span></span>|<span data-ttu-id="d4d97-120">Condição</span><span class="sxs-lookup"><span data-stu-id="d4d97-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="d4d97-121">`Start` <= 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="d4d97-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d97-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4d97-122">Remarks</span></span>  
 <span data-ttu-id="d4d97-123">O número de caracteres serão substituídos sempre é menor ou igual ao número de caracteres em `Target`.</span><span class="sxs-lookup"><span data-stu-id="d4d97-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="d4d97-124">O Visual Basic possui um <xref:Microsoft.VisualBasic.Strings.Mid%2A> função e um `Mid` instrução.</span><span class="sxs-lookup"><span data-stu-id="d4d97-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="d4d97-125">Os dois elementos operam em um número especificado de caracteres em uma cadeia de caracteres, mas o `Mid` função retorna os caracteres enquanto o `Mid` instrução substitui os caracteres.</span><span class="sxs-lookup"><span data-stu-id="d4d97-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="d4d97-126">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4d97-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4d97-127">O `MidB` declaração de versões anteriores do Visual Basic substitui uma subcadeia de caracteres em bytes, em vez de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d4d97-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="d4d97-128">Ele é usado principalmente para converter cadeias de caracteres em caracteres de byte duplo (DBCS) conjunto de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d4d97-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="d4d97-129">Todas as cadeias de caracteres do Visual Basic estão em Unicode, e `MidB` não é mais suportada.</span><span class="sxs-lookup"><span data-stu-id="d4d97-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4d97-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4d97-130">Example</span></span>  
 <span data-ttu-id="d4d97-131">Este exemplo usa o `Mid` instrução para substituir um número especificado de caracteres em uma variável de cadeia de caracteres com caracteres de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d4d97-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="d4d97-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4d97-132">Requirements</span></span>  
 <span data-ttu-id="d4d97-133">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="d4d97-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="d4d97-134">**Módulo:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="d4d97-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="d4d97-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d97-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d97-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4d97-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="d4d97-137">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="d4d97-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="d4d97-138">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4d97-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
