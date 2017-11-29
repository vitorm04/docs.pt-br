---
title: '#<a name="const-directive"></a>Diretiva const'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a><span data-ttu-id="96192-102">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="96192-102">#Const Directive</span></span>
<span data-ttu-id="96192-103">Define constantes condicionais de compilador do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="96192-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96192-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96192-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="96192-105">Partes</span><span class="sxs-lookup"><span data-stu-id="96192-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="96192-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="96192-106">Required.</span></span> <span data-ttu-id="96192-107">Nome da constante sendo definida.</span><span class="sxs-lookup"><span data-stu-id="96192-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="96192-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="96192-108">Required.</span></span> <span data-ttu-id="96192-109">Literal, outra constante condicional de compilador ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos exceto `Is`.</span><span class="sxs-lookup"><span data-stu-id="96192-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96192-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="96192-110">Remarks</span></span>  
 <span data-ttu-id="96192-111">Constantes condicionais de compilador são sempre privadas para o arquivo em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="96192-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="96192-112">Você não pode criar constantes de compilador públicas usando o `#Const` diretiva; você pode criá-los apenas na interface do usuário ou com o `/define` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="96192-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="96192-113">Você pode usar apenas constantes condicionais de compilador e literais em `expression`.</span><span class="sxs-lookup"><span data-stu-id="96192-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="96192-114">Usar uma condição padrão definida com `Const` causa um erro.</span><span class="sxs-lookup"><span data-stu-id="96192-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="96192-115">Por outro lado, você pode usar constantes definidas com o `#Const` palavra-chave para compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="96192-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="96192-116">Constantes também podem ser indefinidas, caso em que eles têm um valor de `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="96192-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96192-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96192-117">Example</span></span>  
 <span data-ttu-id="96192-118">Este exemplo usa o `#Const` diretiva.</span><span class="sxs-lookup"><span data-stu-id="96192-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="96192-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96192-119">See Also</span></span>  
 [<span data-ttu-id="96192-120">/Define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96192-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="96192-121">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="96192-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="96192-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="96192-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="96192-123">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="96192-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="96192-124">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="96192-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
