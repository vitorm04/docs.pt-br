---
title: "Mid instrução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e94500c8bd7f2c6351c91ba028c1ad6d8d3dd4c3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="mid-statement"></a><span data-ttu-id="92176-102">Instrução Mid</span><span class="sxs-lookup"><span data-stu-id="92176-102">Mid Statement</span></span>
<span data-ttu-id="92176-103">Substitui um número especificado de caracteres em um `String` variável com caracteres de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92176-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92176-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92176-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="92176-105">Partes</span><span class="sxs-lookup"><span data-stu-id="92176-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="92176-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92176-106">Required.</span></span> <span data-ttu-id="92176-107">Nome da `String` variável para modificar.</span><span class="sxs-lookup"><span data-stu-id="92176-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="92176-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92176-108">Required.</span></span> <span data-ttu-id="92176-109">Expressão `Integer`.</span><span class="sxs-lookup"><span data-stu-id="92176-109">`Integer` expression.</span></span> <span data-ttu-id="92176-110">Posição de caractere `Target` onde a substituição do texto começa.</span><span class="sxs-lookup"><span data-stu-id="92176-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="92176-111">`Start`usa um índice baseado em um.</span><span class="sxs-lookup"><span data-stu-id="92176-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="92176-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="92176-112">Optional.</span></span> <span data-ttu-id="92176-113">Expressão `Integer`.</span><span class="sxs-lookup"><span data-stu-id="92176-113">`Integer` expression.</span></span> <span data-ttu-id="92176-114">Número de caracteres a substituir.</span><span class="sxs-lookup"><span data-stu-id="92176-114">Number of characters to replace.</span></span> <span data-ttu-id="92176-115">Se omitido, todos `String` é usado.</span><span class="sxs-lookup"><span data-stu-id="92176-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="92176-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92176-116">Required.</span></span> <span data-ttu-id="92176-117">`String`expressão que substitui parte de `Target`.</span><span class="sxs-lookup"><span data-stu-id="92176-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="92176-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="92176-118">Exceptions</span></span>  
  
|<span data-ttu-id="92176-119">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="92176-119">Exception type</span></span>|<span data-ttu-id="92176-120">Condição</span><span class="sxs-lookup"><span data-stu-id="92176-120">Condition</span></span>|  
|--------------------|---------------|  
|<span data-ttu-id="92176-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="92176-121"><xref:System.ArgumentException></span></span>|<span data-ttu-id="92176-122">`Start` <= 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="92176-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92176-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="92176-123">Remarks</span></span>  
 <span data-ttu-id="92176-124">O número de caracteres substituído é sempre menor ou igual ao número de caracteres em `Target`.</span><span class="sxs-lookup"><span data-stu-id="92176-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="92176-125">O Visual Basic possui uma <xref:Microsoft.VisualBasic.Strings.Mid%2A>função e um `Mid` instrução.</xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="92176-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="92176-126">Os dois elementos operam em um número especificado de caracteres em uma cadeia de caracteres, mas o `Mid` função retorna os caracteres enquanto o `Mid` instrução substitui os caracteres.</span><span class="sxs-lookup"><span data-stu-id="92176-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="92176-127">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="92176-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92176-128">O `MidB` instrução de versões anteriores do Visual Basic substitui uma substring em bytes, em vez de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92176-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="92176-129">Ele é usado principalmente para converter cadeias de caracteres de dois bytes (DBCS) conjunto de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="92176-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="92176-130">Todas as cadeias de caracteres do Visual Basic estão em Unicode, e `MidB` não é mais suportado.</span><span class="sxs-lookup"><span data-stu-id="92176-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92176-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92176-131">Example</span></span>  
 <span data-ttu-id="92176-132">Este exemplo usa o `Mid` instrução para substituir um número especificado de caracteres em uma variável de cadeia de caracteres com caracteres de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92176-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 <span data-ttu-id="92176-133">[!code-vb[VbVbalrStrings n º&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="92176-133">[!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92176-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92176-134">Requirements</span></span>  
 <span data-ttu-id="92176-135">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="92176-135">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="92176-136">**Módulo:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="92176-136">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="92176-137">**Assembly:**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span><span class="sxs-lookup"><span data-stu-id="92176-137">**Assembly:** [!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92176-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92176-138">See Also</span></span>  
 <span data-ttu-id="92176-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="92176-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
<span data-ttu-id="92176-140"> [Cadeias de caracteres](../../../visual-basic/programming-guide/language-features/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="92176-140"> [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md) </span></span>  
<span data-ttu-id="92176-141"> [Introdução a cadeias de caracteres no Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="92176-141"> [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
