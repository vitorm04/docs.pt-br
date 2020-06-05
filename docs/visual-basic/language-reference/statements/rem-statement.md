---
title: Instrução REM
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
ms.openlocfilehash: 68c898145bd8845c657b6ebb8776a3a9027c359c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404259"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="321a9-102">Instrução REM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321a9-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="321a9-103">Usado para incluir comentários explicativos no código-fonte de um programa.</span><span class="sxs-lookup"><span data-stu-id="321a9-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="321a9-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="321a9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="321a9-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="321a9-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="321a9-106">Optional.</span></span> <span data-ttu-id="321a9-107">O texto de qualquer comentário que você deseja incluir.</span><span class="sxs-lookup"><span data-stu-id="321a9-107">The text of any comment you want to include.</span></span> <span data-ttu-id="321a9-108">Um espaço é necessário entre a `REM` palavra-chave e `comment` .</span><span class="sxs-lookup"><span data-stu-id="321a9-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="321a9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="321a9-109">Remarks</span></span>  
 <span data-ttu-id="321a9-110">Você pode colocar uma `REM` instrução sozinha em uma linha ou pode colocá-la em uma linha após outra instrução.</span><span class="sxs-lookup"><span data-stu-id="321a9-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="321a9-111">A `REM` instrução deve ser a última instrução na linha.</span><span class="sxs-lookup"><span data-stu-id="321a9-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="321a9-112">Se ele seguir outra instrução, o `REM` deverá ser separado dessa instrução por um espaço.</span><span class="sxs-lookup"><span data-stu-id="321a9-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="321a9-113">Você pode usar uma aspa simples ( `'` ) em vez de `REM` .</span><span class="sxs-lookup"><span data-stu-id="321a9-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="321a9-114">Isso é verdadeiro se o comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.</span><span class="sxs-lookup"><span data-stu-id="321a9-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="321a9-115">Você não pode continuar uma `REM` instrução usando uma sequência de continuação de linha ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="321a9-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="321a9-116">Depois que um comentário é iniciado, o compilador não examina os caracteres para obter um significado especial.</span><span class="sxs-lookup"><span data-stu-id="321a9-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="321a9-117">Para um comentário de várias linhas, use outra `REM` instrução ou um símbolo de comentário ( `'` ) em cada linha.</span><span class="sxs-lookup"><span data-stu-id="321a9-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="321a9-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="321a9-118">Example</span></span>  
 <span data-ttu-id="321a9-119">O exemplo a seguir ilustra a `REM` instrução, que é usada para incluir comentários explicativos em um programa.</span><span class="sxs-lookup"><span data-stu-id="321a9-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="321a9-120">Ele também mostra a alternativa de usar o caractere de aspa simples ( `'` ) em vez de `REM` .</span><span class="sxs-lookup"><span data-stu-id="321a9-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="321a9-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="321a9-121">See also</span></span>

- [<span data-ttu-id="321a9-122">Comentários no código</span><span class="sxs-lookup"><span data-stu-id="321a9-122">Comments in Code</span></span>](../../programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="321a9-123">Como: Quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="321a9-123">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
