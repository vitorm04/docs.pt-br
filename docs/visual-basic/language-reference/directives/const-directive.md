---
title: '#Diretiva const | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
dev_langs:
- VB
helpviewer_keywords:
- '#Const directive'
- conditional compilation, directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants, Const directive
- constants, declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants, #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: 17
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
ms.openlocfilehash: 7bac82c279394ef0719b192c9cbd779523383483
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="const-directive"></a>#<span data-ttu-id="200a7-102">Diretiva const</span><span class="sxs-lookup"><span data-stu-id="200a7-102">Const Directive</span></span>
<span data-ttu-id="200a7-103">Define constantes condicionais de compilador do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="200a7-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="200a7-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="200a7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="200a7-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="200a7-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="200a7-106">Required.</span></span> <span data-ttu-id="200a7-107">Nome da constante sendo definida.</span><span class="sxs-lookup"><span data-stu-id="200a7-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="200a7-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="200a7-108">Required.</span></span> <span data-ttu-id="200a7-109">Literal, outra constante condicional de compilador ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos exceto `Is`.</span><span class="sxs-lookup"><span data-stu-id="200a7-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="200a7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="200a7-110">Remarks</span></span>  
 <span data-ttu-id="200a7-111">Essas constantes são sempre particulares para o arquivo em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="200a7-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="200a7-112">Você não pode criar constantes de compilador públicas usando o `#Const` diretriz; você pode criá-los apenas na interface do usuário ou com o `/define` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="200a7-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="200a7-113">Você pode usar apenas constantes de compilador condicionais e literais em `expression`.</span><span class="sxs-lookup"><span data-stu-id="200a7-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="200a7-114">Usar uma condição padrão definida com `Const` causa um erro.</span><span class="sxs-lookup"><span data-stu-id="200a7-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="200a7-115">Por outro lado, você pode usar constantes definidas com o `#Const` palavra-chave para compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="200a7-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="200a7-116">Constantes também podem ser indefinidas, caso no qual elas possuem um valor de `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="200a7-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="200a7-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="200a7-117">Example</span></span>  
 <span data-ttu-id="200a7-118">Este exemplo usa a `#Const` diretiva.</span><span class="sxs-lookup"><span data-stu-id="200a7-118">This example uses the `#Const` directive.</span></span>  
  
 <span data-ttu-id="200a7-119">[!code-vb[VbVbalrConditionalComp n º&3;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="200a7-119">[!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200a7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="200a7-120">See Also</span></span>  
 <span data-ttu-id="200a7-121">[/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md) </span><span class="sxs-lookup"><span data-stu-id="200a7-121">[/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md) </span></span>  
<span data-ttu-id="200a7-122"> [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="200a7-122"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="200a7-123"> [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="200a7-123"> [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="200a7-124"> [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="200a7-124"> [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<span data-ttu-id="200a7-125"> [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)</span><span class="sxs-lookup"><span data-stu-id="200a7-125"> [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)</span></span>
