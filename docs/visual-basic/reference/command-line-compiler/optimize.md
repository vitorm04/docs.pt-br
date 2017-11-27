---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a><span data-ttu-id="0e85b-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="0e85b-102">/optimize</span></span>
<span data-ttu-id="0e85b-103">Habilita ou desabilita otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="0e85b-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e85b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e85b-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e85b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0e85b-105">Arguments</span></span>  
  
|<span data-ttu-id="0e85b-106">Termo</span><span class="sxs-lookup"><span data-stu-id="0e85b-106">Term</span></span>|<span data-ttu-id="0e85b-107">Definição</span><span class="sxs-lookup"><span data-stu-id="0e85b-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0e85b-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0e85b-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0e85b-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="0e85b-109">Optional.</span></span> <span data-ttu-id="0e85b-110">O `/optimize-` opção desabilita otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="0e85b-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="0e85b-111">O `/optimize+` opção habilita as otimizações.</span><span class="sxs-lookup"><span data-stu-id="0e85b-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="0e85b-112">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="0e85b-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e85b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e85b-113">Remarks</span></span>  
 <span data-ttu-id="0e85b-114">Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="0e85b-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="0e85b-115">No entanto, como a reorganização de código no arquivo de saída, gerar otimizações `/optimize+` pode dificultar a depuração.</span><span class="sxs-lookup"><span data-stu-id="0e85b-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="0e85b-116">Todos os módulos gerados com `/target:module` para um assembly deve usar o mesmo `/optimize` configurações como o assembly.</span><span class="sxs-lookup"><span data-stu-id="0e85b-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="0e85b-117">Para obter mais informações, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="0e85b-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="0e85b-118">Você pode combinar o `/optimize` e `/debug` opções.</span><span class="sxs-lookup"><span data-stu-id="0e85b-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="0e85b-119">Para definir /Optimize no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e85b-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0e85b-120">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="0e85b-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0e85b-121">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0e85b-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="0e85b-122">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="0e85b-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="0e85b-123">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="0e85b-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0e85b-124">3.  Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="0e85b-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="0e85b-125">4.  Modificar o **habilitar otimizações** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="0e85b-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e85b-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e85b-126">Example</span></span>  
 <span data-ttu-id="0e85b-127">O código a seguir compila `T2.vb` e habilita otimizações de compilador.</span><span class="sxs-lookup"><span data-stu-id="0e85b-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e85b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e85b-128">See Also</span></span>  
 [<span data-ttu-id="0e85b-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e85b-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0e85b-130">/Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e85b-130">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="0e85b-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e85b-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0e85b-132">/Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e85b-132">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
