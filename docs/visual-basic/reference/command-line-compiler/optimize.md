---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 337cb794ef9a405a178f1998cbe27b5da7709382
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397435"
---
# <a name="-optimize"></a><span data-ttu-id="78eb2-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="78eb2-102">-optimize</span></span>
<span data-ttu-id="78eb2-103">Habilita ou desabilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="78eb2-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78eb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78eb2-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="78eb2-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="78eb2-105">Arguments</span></span>  
  
|<span data-ttu-id="78eb2-106">Termo</span><span class="sxs-lookup"><span data-stu-id="78eb2-106">Term</span></span>|<span data-ttu-id="78eb2-107">Definição</span><span class="sxs-lookup"><span data-stu-id="78eb2-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="78eb2-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="78eb2-108">`+` &#124; `-`</span></span>|<span data-ttu-id="78eb2-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="78eb2-109">Optional.</span></span> <span data-ttu-id="78eb2-110">A `-optimize-` opção desabilita otimizações de compilador.</span><span class="sxs-lookup"><span data-stu-id="78eb2-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="78eb2-111">A `-optimize+` opção habilita otimizações.</span><span class="sxs-lookup"><span data-stu-id="78eb2-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="78eb2-112">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="78eb2-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78eb2-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="78eb2-113">Remarks</span></span>  
 <span data-ttu-id="78eb2-114">Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="78eb2-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="78eb2-115">No entanto, como as otimizações resultam na reorganização de código no arquivo de saída, o `-optimize+` pode dificultar a depuração.</span><span class="sxs-lookup"><span data-stu-id="78eb2-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="78eb2-116">Todos os módulos gerados com `-target:module` para um assembly devem usar as mesmas `-optimize` configurações que o assembly.</span><span class="sxs-lookup"><span data-stu-id="78eb2-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="78eb2-117">Para obter mais informações, consulte [-Target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="78eb2-117">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="78eb2-118">Você pode combinar as `-optimize` `-debug` Opções e.</span><span class="sxs-lookup"><span data-stu-id="78eb2-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="78eb2-119">Para definir-otimizar no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="78eb2-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="78eb2-120">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="78eb2-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="78eb2-121">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="78eb2-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="78eb2-122">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="78eb2-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="78eb2-123">3. Clique no botão **avançado** .</span><span class="sxs-lookup"><span data-stu-id="78eb2-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="78eb2-124">4. modifique a caixa de seleção **habilitar otimizações** .</span><span class="sxs-lookup"><span data-stu-id="78eb2-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="78eb2-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78eb2-125">Example</span></span>  
 <span data-ttu-id="78eb2-126">O código a seguir compila `T2.vb` e habilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="78eb2-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="78eb2-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="78eb2-127">See also</span></span>

- [<span data-ttu-id="78eb2-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78eb2-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="78eb2-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78eb2-129">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="78eb2-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="78eb2-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="78eb2-131">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78eb2-131">-target (Visual Basic)</span></span>](target.md)
