---
title: "-optimize (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2cf6919ee2d4f0a4031e18d46b9e5ebaf816b120
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="ae5f6-102">-optimize (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ae5f6-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="ae5f6-103">A opção **-optimize** habilita ou desabilita otimizações executadas pelo compilador para tornar o arquivo de saída menor, mais rápido e mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae5f6-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae5f6-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae5f6-105">Remarks</span></span>  
 <span data-ttu-id="ae5f6-106">A **-optimize** também informa o Common Language Runtime para otimizar o código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="ae5f6-107">Por padrão, as otimizações estão desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="ae5f6-108">Especifique **-optimize+** para habilitar otimizações.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="ae5f6-109">Ao criar um módulo a ser usado por um assembly, use as mesmas configurações **-optimize** que as do assembly.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="ae5f6-110">**-o** é a forma abreviada de **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="ae5f6-111">É possível combinar as opções **-optimize** e [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ae5f6-111">It is possible to combine the **-optimize** and [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ae5f6-112">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ae5f6-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ae5f6-113">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="ae5f6-114">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="ae5f6-115">Modifique a propriedade **Otimizar código**.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="ae5f6-116">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae5f6-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae5f6-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae5f6-117">Example</span></span>  
 <span data-ttu-id="ae5f6-118">Compile `t2.cs` e habilite as otimizações do compilador:</span><span class="sxs-lookup"><span data-stu-id="ae5f6-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae5f6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae5f6-119">See Also</span></span>  
 [<span data-ttu-id="ae5f6-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="ae5f6-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ae5f6-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="ae5f6-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
