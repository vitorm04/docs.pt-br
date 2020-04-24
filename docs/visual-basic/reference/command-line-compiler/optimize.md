---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005376"
---
# <a name="-optimize"></a><span data-ttu-id="44ee8-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="44ee8-102">-optimize</span></span>
<span data-ttu-id="44ee8-103">Habilita ou desabilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="44ee8-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ee8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44ee8-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="44ee8-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="44ee8-105">Arguments</span></span>  
  
|<span data-ttu-id="44ee8-106">Termo</span><span class="sxs-lookup"><span data-stu-id="44ee8-106">Term</span></span>|<span data-ttu-id="44ee8-107">Definição</span><span class="sxs-lookup"><span data-stu-id="44ee8-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="44ee8-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="44ee8-108">`+` &#124; `-`</span></span>|<span data-ttu-id="44ee8-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="44ee8-109">Optional.</span></span> <span data-ttu-id="44ee8-110">A `-optimize-` opção desabilita otimizações de compilador.</span><span class="sxs-lookup"><span data-stu-id="44ee8-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="44ee8-111">A `-optimize+` opção habilita otimizações.</span><span class="sxs-lookup"><span data-stu-id="44ee8-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="44ee8-112">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="44ee8-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44ee8-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="44ee8-113">Remarks</span></span>  
 <span data-ttu-id="44ee8-114">Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="44ee8-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="44ee8-115">No entanto, como as otimizações resultam na reorganização de código no `-optimize+` arquivo de saída, o pode dificultar a depuração.</span><span class="sxs-lookup"><span data-stu-id="44ee8-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="44ee8-116">Todos os módulos gerados `-target:module` com para um assembly devem usar as `-optimize` mesmas configurações que o assembly.</span><span class="sxs-lookup"><span data-stu-id="44ee8-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="44ee8-117">Para obter mais informações, consulte [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="44ee8-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="44ee8-118">Você pode combinar as `-optimize` opções `-debug` e.</span><span class="sxs-lookup"><span data-stu-id="44ee8-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="44ee8-119">Para definir-otimizar no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="44ee8-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="44ee8-120">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="44ee8-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="44ee8-121">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="44ee8-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="44ee8-122">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="44ee8-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="44ee8-123">3. Clique no botão **avançado** .</span><span class="sxs-lookup"><span data-stu-id="44ee8-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="44ee8-124">4. modifique a caixa de seleção **habilitar otimizações** .</span><span class="sxs-lookup"><span data-stu-id="44ee8-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44ee8-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44ee8-125">Example</span></span>  
 <span data-ttu-id="44ee8-126">O código a seguir compila `T2.vb` e habilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="44ee8-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="44ee8-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="44ee8-127">See also</span></span>

- [<span data-ttu-id="44ee8-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44ee8-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="44ee8-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44ee8-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="44ee8-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="44ee8-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="44ee8-131">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44ee8-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
