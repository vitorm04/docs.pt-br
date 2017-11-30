---
title: "Instrução REM (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="b64fa-102">Instrução REM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64fa-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="b64fa-103">Usado para incluir comentários explicativos no código-fonte de um programa.</span><span class="sxs-lookup"><span data-stu-id="b64fa-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b64fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b64fa-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="b64fa-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b64fa-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="b64fa-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b64fa-106">Optional.</span></span> <span data-ttu-id="b64fa-107">O texto de qualquer comentário que você deseja incluir.</span><span class="sxs-lookup"><span data-stu-id="b64fa-107">The text of any comment you want to include.</span></span> <span data-ttu-id="b64fa-108">Um espaço é necessário entre a `REM` palavra-chave e `comment`.</span><span class="sxs-lookup"><span data-stu-id="b64fa-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b64fa-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b64fa-109">Remarks</span></span>  
 <span data-ttu-id="b64fa-110">Você pode colocar um `REM` instrução sozinha em uma linha, ou você pode colocá-lo em uma linha após outra instrução.</span><span class="sxs-lookup"><span data-stu-id="b64fa-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="b64fa-111">O `REM` instrução deve ser a última instrução na linha.</span><span class="sxs-lookup"><span data-stu-id="b64fa-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="b64fa-112">Se ela segue outra instrução, o `REM` devem ser separados dessa instrução por um espaço.</span><span class="sxs-lookup"><span data-stu-id="b64fa-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="b64fa-113">Você pode usar aspas simples (`'`) em vez de `REM`.</span><span class="sxs-lookup"><span data-stu-id="b64fa-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="b64fa-114">Isso é verdadeiro se o seu comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.</span><span class="sxs-lookup"><span data-stu-id="b64fa-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b64fa-115">Você não pode continuar uma `REM` instrução usando uma sequência de continuação de linha (`_`).</span><span class="sxs-lookup"><span data-stu-id="b64fa-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="b64fa-116">Quando um comentário começa, o compilador não examina os caracteres para um significado especial.</span><span class="sxs-lookup"><span data-stu-id="b64fa-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="b64fa-117">Para um comentário de várias linhas, use outra `REM` instrução ou um símbolo de comentário (`'`) em cada linha.</span><span class="sxs-lookup"><span data-stu-id="b64fa-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b64fa-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b64fa-118">Example</span></span>  
 <span data-ttu-id="b64fa-119">O exemplo a seguir ilustra o `REM` instrução, que é usada para incluir comentários explicativos em um programa.</span><span class="sxs-lookup"><span data-stu-id="b64fa-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="b64fa-120">Ele também mostra a possibilidade de usar o caractere de aspas simples (`'`) em vez de `REM`.</span><span class="sxs-lookup"><span data-stu-id="b64fa-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b64fa-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b64fa-121">See Also</span></span>  
 [<span data-ttu-id="b64fa-122">Comentários no Código</span><span class="sxs-lookup"><span data-stu-id="b64fa-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [<span data-ttu-id="b64fa-123">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="b64fa-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
