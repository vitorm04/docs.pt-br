---
description: -nowarn (opções do compilador C#)
title: -nowarn (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194018"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="2aa2b-103">-nowarn (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="2aa2b-103">-nowarn (C# Compiler Options)</span></span>

<span data-ttu-id="2aa2b-104">A opção **-nowarn** permite suprimir a exibição de um ou mais avisos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="2aa2b-105">Separe vários números de aviso com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa2b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2aa2b-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2aa2b-107">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2aa2b-107">Arguments</span></span>  

 <span data-ttu-id="2aa2b-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="2aa2b-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="2aa2b-109">Números de aviso que você deseja que o compilador suprima.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2aa2b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2aa2b-110">Remarks</span></span>  

 <span data-ttu-id="2aa2b-111">Você só precisa especificar a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="2aa2b-112">Por exemplo, se quiser suprimir CS0028, você pode especificar `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="2aa2b-113">O compilador ignorará silenciosamente números de aviso passados para `-nowarn` que eram válidos em versões anteriores, mas que foram removidos do compilador.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="2aa2b-114">Por exemplo, CS0679 era válido no compilador no Visual Studio .NET 2002, mas foi removido posteriormente.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="2aa2b-115">Os avisos a seguir não podem ser suprimidos pela opção `-nowarn`:</span><span class="sxs-lookup"><span data-stu-id="2aa2b-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="2aa2b-116">Aviso do compilador (nível 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="2aa2b-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="2aa2b-117">Aviso do compilador (nível 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="2aa2b-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="2aa2b-118">Aviso do compilador (nível 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="2aa2b-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2aa2b-119">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2aa2b-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2aa2b-120">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="2aa2b-121">Para obter detalhes, consulte [Página de Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="2aa2b-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="2aa2b-122">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="2aa2b-123">Modifique a propriedade **Suprimir Avisos**.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="2aa2b-124">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="2aa2b-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa2b-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="2aa2b-125">See also</span></span>

- [<span data-ttu-id="2aa2b-126">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="2aa2b-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2aa2b-127">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="2aa2b-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="2aa2b-128">Erros do compilador C#</span><span class="sxs-lookup"><span data-stu-id="2aa2b-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
