---
title: Instrução REM (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604270"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="37c57-102">Instrução REM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37c57-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="37c57-103">Usado para incluir comentários explicativos no código-fonte de um programa.</span><span class="sxs-lookup"><span data-stu-id="37c57-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c57-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37c57-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="37c57-105">Partes</span><span class="sxs-lookup"><span data-stu-id="37c57-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="37c57-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="37c57-106">Optional.</span></span> <span data-ttu-id="37c57-107">O texto de qualquer comentário que você deseja incluir.</span><span class="sxs-lookup"><span data-stu-id="37c57-107">The text of any comment you want to include.</span></span> <span data-ttu-id="37c57-108">Um espaço é necessário entre a `REM` palavra-chave e `comment`.</span><span class="sxs-lookup"><span data-stu-id="37c57-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37c57-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="37c57-109">Remarks</span></span>  
 <span data-ttu-id="37c57-110">Você pode colocar um `REM` instrução sozinha em uma linha, ou você pode colocá-lo em uma linha após outra instrução.</span><span class="sxs-lookup"><span data-stu-id="37c57-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="37c57-111">O `REM` instrução deve ser a última instrução na linha.</span><span class="sxs-lookup"><span data-stu-id="37c57-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="37c57-112">Se ela segue outra instrução, o `REM` devem ser separados dessa instrução por um espaço.</span><span class="sxs-lookup"><span data-stu-id="37c57-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="37c57-113">Você pode usar aspas simples (`'`) em vez de `REM`.</span><span class="sxs-lookup"><span data-stu-id="37c57-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="37c57-114">Isso é verdadeiro se o seu comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.</span><span class="sxs-lookup"><span data-stu-id="37c57-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37c57-115">Você não pode continuar uma `REM` instrução usando uma sequência de continuação de linha (`_`).</span><span class="sxs-lookup"><span data-stu-id="37c57-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="37c57-116">Quando um comentário começa, o compilador não examina os caracteres para um significado especial.</span><span class="sxs-lookup"><span data-stu-id="37c57-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="37c57-117">Para um comentário de várias linhas, use outra `REM` instrução ou um símbolo de comentário (`'`) em cada linha.</span><span class="sxs-lookup"><span data-stu-id="37c57-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37c57-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37c57-118">Example</span></span>  
 <span data-ttu-id="37c57-119">O exemplo a seguir ilustra o `REM` instrução, que é usada para incluir comentários explicativos em um programa.</span><span class="sxs-lookup"><span data-stu-id="37c57-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="37c57-120">Ele também mostra a possibilidade de usar o caractere de aspas simples (`'`) em vez de `REM`.</span><span class="sxs-lookup"><span data-stu-id="37c57-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="37c57-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37c57-121">See Also</span></span>  
 [<span data-ttu-id="37c57-122">Comentários no Código</span><span class="sxs-lookup"><span data-stu-id="37c57-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [<span data-ttu-id="37c57-123">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="37c57-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
