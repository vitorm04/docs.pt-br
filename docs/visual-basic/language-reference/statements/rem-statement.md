---
title: "Instrução REM (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
dev_langs:
- VB
helpviewer_keywords:
- REM statement
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: 11
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
ms.openlocfilehash: bcf937e9d65f1e1be67513f04ddd6ac1b7676caa
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="5e12b-102">Instrução REM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e12b-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="5e12b-103">Usado para incluir comentários explicativos no código-fonte de um programa.</span><span class="sxs-lookup"><span data-stu-id="5e12b-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e12b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e12b-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="5e12b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5e12b-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="5e12b-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5e12b-106">Optional.</span></span> <span data-ttu-id="5e12b-107">O texto de qualquer comentário que você deseja incluir.</span><span class="sxs-lookup"><span data-stu-id="5e12b-107">The text of any comment you want to include.</span></span> <span data-ttu-id="5e12b-108">Um espaço é necessário entre a `REM` palavra-chave e `comment`.</span><span class="sxs-lookup"><span data-stu-id="5e12b-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e12b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e12b-109">Remarks</span></span>  
 <span data-ttu-id="5e12b-110">Você pode colocar um `REM` instrução sozinha em uma linha, ou você pode colocá-lo em uma linha após outra instrução.</span><span class="sxs-lookup"><span data-stu-id="5e12b-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="5e12b-111">O `REM` instrução deve ser a última instrução na linha.</span><span class="sxs-lookup"><span data-stu-id="5e12b-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="5e12b-112">Se ela segue outra instrução, o `REM` deve ser separada dessa instrução por um espaço.</span><span class="sxs-lookup"><span data-stu-id="5e12b-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="5e12b-113">Você pode usar aspas simples (`'`) em vez de `REM`.</span><span class="sxs-lookup"><span data-stu-id="5e12b-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="5e12b-114">Isso é verdadeiro se o seu comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.</span><span class="sxs-lookup"><span data-stu-id="5e12b-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e12b-115">Você não pode continuar uma `REM` instrução usando uma sequência de continuação de linha (`_`).</span><span class="sxs-lookup"><span data-stu-id="5e12b-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="5e12b-116">Quando um comentário começa, o compilador não examina os caracteres para um significado especial.</span><span class="sxs-lookup"><span data-stu-id="5e12b-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="5e12b-117">Para um comentário de várias linhas, use outra `REM` instrução ou um símbolo de comentário (`'`) em cada linha.</span><span class="sxs-lookup"><span data-stu-id="5e12b-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e12b-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e12b-118">Example</span></span>  
 <span data-ttu-id="5e12b-119">O exemplo a seguir ilustra o `REM` instrução, que é usada para incluir comentários explicativos em um programa.</span><span class="sxs-lookup"><span data-stu-id="5e12b-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="5e12b-120">Ele também mostra a alternativa de usar o caractere de aspas simples (`'`) em vez de `REM`.</span><span class="sxs-lookup"><span data-stu-id="5e12b-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 <span data-ttu-id="5e12b-121">[!code-vb[VbVbalrStatements n º&6;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e12b-121">[!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e12b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e12b-122">See Also</span></span>  
 <span data-ttu-id="5e12b-123">[Comentários no código](../../../visual-basic/programming-guide/program-structure/comments-in-code.md) </span><span class="sxs-lookup"><span data-stu-id="5e12b-123">[Comments in Code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md) </span></span>  
<span data-ttu-id="5e12b-124"> [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="5e12b-124"> [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span></span>
