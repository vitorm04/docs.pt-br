---
title: /Optimize | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization, enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: 15
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
ms.openlocfilehash: f01ab17d4a2f5d123538294a7a13d7a6d7a40267
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optimize"></a><span data-ttu-id="88451-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="88451-102">/optimize</span></span>
<span data-ttu-id="88451-103">Habilita ou desabilita otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="88451-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88451-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88451-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="88451-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="88451-105">Arguments</span></span>  
  
|<span data-ttu-id="88451-106">Termo</span><span class="sxs-lookup"><span data-stu-id="88451-106">Term</span></span>|<span data-ttu-id="88451-107">Definição</span><span class="sxs-lookup"><span data-stu-id="88451-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="88451-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="88451-108">`+` &#124; `-`</span></span>|<span data-ttu-id="88451-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="88451-109">Optional.</span></span> <span data-ttu-id="88451-110">O `/optimize-` desabilita otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="88451-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="88451-111">O `/optimize+` opção habilita otimizações.</span><span class="sxs-lookup"><span data-stu-id="88451-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="88451-112">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="88451-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88451-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="88451-113">Remarks</span></span>  
 <span data-ttu-id="88451-114">Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="88451-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="88451-115">No entanto, como a reorganização de código no arquivo de saída, gerar otimizações `/optimize+` pode dificultar a depuração.</span><span class="sxs-lookup"><span data-stu-id="88451-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="88451-116">Todos os módulos gerados com `/target:module` para um assembly deve usar o mesmo `/optimize` configurações do assembly.</span><span class="sxs-lookup"><span data-stu-id="88451-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="88451-117">Para obter mais informações, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="88451-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="88451-118">Você pode combinar o `/optimize` e `/debug` opções.</span><span class="sxs-lookup"><span data-stu-id="88451-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="88451-119">Para definir /Optimize no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88451-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="88451-120">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="88451-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="88451-121">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="88451-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="88451-122">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="88451-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="88451-123">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="88451-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="88451-124">3.  Clique o **avançado** botão.</span><span class="sxs-lookup"><span data-stu-id="88451-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="88451-125">4.  Modificar o **habilitar otimizações** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="88451-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="88451-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88451-126">Example</span></span>  
 <span data-ttu-id="88451-127">O seguinte código compila `T2.vb` e permite otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="88451-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="88451-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88451-128">See Also</span></span>  
 <span data-ttu-id="88451-129">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="88451-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="88451-130"> [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span><span class="sxs-lookup"><span data-stu-id="88451-130"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span></span>  
<span data-ttu-id="88451-131"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="88451-131"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="88451-132"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)</span><span class="sxs-lookup"><span data-stu-id="88451-132"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)</span></span>
