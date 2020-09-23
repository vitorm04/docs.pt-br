---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: d4b50d56373676bf78a7591102095209401c907d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097586"
---
# <a name="-optimize"></a><span data-ttu-id="69f86-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="69f86-102">-optimize</span></span>

<span data-ttu-id="69f86-103">Habilita ou desabilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="69f86-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69f86-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="69f86-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="69f86-105">Arguments</span></span>  
  
|<span data-ttu-id="69f86-106">Termo</span><span class="sxs-lookup"><span data-stu-id="69f86-106">Term</span></span>|<span data-ttu-id="69f86-107">Definição</span><span class="sxs-lookup"><span data-stu-id="69f86-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="69f86-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="69f86-108">`+` &#124; `-`</span></span>|<span data-ttu-id="69f86-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="69f86-109">Optional.</span></span> <span data-ttu-id="69f86-110">A `-optimize-` opção desabilita otimizações de compilador.</span><span class="sxs-lookup"><span data-stu-id="69f86-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="69f86-111">A `-optimize+` opção habilita otimizações.</span><span class="sxs-lookup"><span data-stu-id="69f86-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="69f86-112">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="69f86-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69f86-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="69f86-113">Remarks</span></span>  

 <span data-ttu-id="69f86-114">Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="69f86-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="69f86-115">No entanto, como as otimizações resultam na reorganização de código no arquivo de saída, o `-optimize+` pode dificultar a depuração.</span><span class="sxs-lookup"><span data-stu-id="69f86-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="69f86-116">Todos os módulos gerados com `-target:module` para um assembly devem usar as mesmas `-optimize` configurações que o assembly.</span><span class="sxs-lookup"><span data-stu-id="69f86-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="69f86-117">Para obter mais informações, consulte [-Target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="69f86-117">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="69f86-118">Você pode combinar as `-optimize` `-debug` Opções e.</span><span class="sxs-lookup"><span data-stu-id="69f86-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="69f86-119">Para definir-otimizar no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="69f86-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="69f86-120">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="69f86-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="69f86-121">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="69f86-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="69f86-122">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="69f86-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="69f86-123">3. Clique no botão **avançado** .</span><span class="sxs-lookup"><span data-stu-id="69f86-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="69f86-124">4. modifique a caixa de seleção **habilitar otimizações** .</span><span class="sxs-lookup"><span data-stu-id="69f86-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="69f86-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69f86-125">Example</span></span>  

 <span data-ttu-id="69f86-126">O código a seguir compila `T2.vb` e habilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="69f86-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="69f86-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="69f86-127">See also</span></span>

- [<span data-ttu-id="69f86-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69f86-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="69f86-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69f86-129">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="69f86-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="69f86-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="69f86-131">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69f86-131">-target (Visual Basic)</span></span>](target.md)
