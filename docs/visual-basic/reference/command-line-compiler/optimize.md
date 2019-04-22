---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842155"
---
# <a name="-optimize"></a><span data-ttu-id="78e06-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="78e06-102">-optimize</span></span>
<span data-ttu-id="78e06-103">Habilita ou desabilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="78e06-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78e06-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="78e06-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="78e06-105">Arguments</span></span>  
  
|<span data-ttu-id="78e06-106">Termo</span><span class="sxs-lookup"><span data-stu-id="78e06-106">Term</span></span>|<span data-ttu-id="78e06-107">Definição</span><span class="sxs-lookup"><span data-stu-id="78e06-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="78e06-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="78e06-108">`+` &#124; `-`</span></span>|<span data-ttu-id="78e06-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="78e06-109">Optional.</span></span> <span data-ttu-id="78e06-110">O `-optimize-` opção desabilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="78e06-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="78e06-111">O `-optimize+` opção habilita as otimizações.</span><span class="sxs-lookup"><span data-stu-id="78e06-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="78e06-112">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="78e06-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e06-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="78e06-113">Remarks</span></span>  
 <span data-ttu-id="78e06-114">Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="78e06-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="78e06-115">No entanto, porque as otimizações resultam na reorganização de código no arquivo de saída, `-optimize+` pode dificultar a depuração.</span><span class="sxs-lookup"><span data-stu-id="78e06-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="78e06-116">Todos os módulos gerados com `-target:module` para um assembly deve usar a mesma `-optimize` configurações que o assembly.</span><span class="sxs-lookup"><span data-stu-id="78e06-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="78e06-117">Para obter mais informações, consulte [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="78e06-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="78e06-118">Você pode combinar as `-optimize` e `-debug` opções.</span><span class="sxs-lookup"><span data-stu-id="78e06-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="78e06-119">Para definir - otimizar no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="78e06-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="78e06-120">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="78e06-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="78e06-121">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="78e06-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="78e06-122">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="78e06-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="78e06-123">3.  Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="78e06-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="78e06-124">4.  Modificar a **habilitar otimizações** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="78e06-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="78e06-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78e06-125">Example</span></span>  
 <span data-ttu-id="78e06-126">O seguinte código compila `T2.vb` e habilita as otimizações do compilador.</span><span class="sxs-lookup"><span data-stu-id="78e06-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="78e06-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78e06-127">See also</span></span>

- [<span data-ttu-id="78e06-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78e06-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="78e06-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78e06-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="78e06-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="78e06-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="78e06-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78e06-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
