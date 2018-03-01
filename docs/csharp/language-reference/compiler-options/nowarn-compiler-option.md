---
title: "-nowarn (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2784e63b7c1e67b32fc448b4b112ad0252b1abd9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="eec24-102">-nowarn (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="eec24-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="eec24-103">A opção **-nowarn** permite suprimir a exibição de um ou mais avisos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="eec24-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="eec24-104">Separe vários números de aviso com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="eec24-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec24-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eec24-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="eec24-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="eec24-106">Arguments</span></span>  
 <span data-ttu-id="eec24-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="eec24-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="eec24-108">Números de aviso que você deseja que o compilador suprima.</span><span class="sxs-lookup"><span data-stu-id="eec24-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eec24-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eec24-109">Remarks</span></span>  
 <span data-ttu-id="eec24-110">Você só precisa especificar a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="eec24-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="eec24-111">Por exemplo, se quiser suprimir CS0028, você pode especificar `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="eec24-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="eec24-112">O compilador ignorará silenciosamente números de aviso passados para `-nowarn` que eram válidos em versões anteriores, mas que foram removidos do compilador.</span><span class="sxs-lookup"><span data-stu-id="eec24-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="eec24-113">Por exemplo, CS0679 era válido no compilador no Visual Studio .NET 2002, mas foi removido posteriormente.</span><span class="sxs-lookup"><span data-stu-id="eec24-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="eec24-114">Os avisos a seguir não podem ser suprimidos pela opção `-nowarn`:</span><span class="sxs-lookup"><span data-stu-id="eec24-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
-   <span data-ttu-id="eec24-115">Aviso do compilador (nível 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="eec24-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="eec24-116">Aviso do compilador (nível 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="eec24-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="eec24-117">Aviso do compilador (nível 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="eec24-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="eec24-118">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eec24-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="eec24-119">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="eec24-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="eec24-120">Para obter detalhes, consulte [Página de Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="eec24-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="eec24-121">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="eec24-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="eec24-122">Modifique a propriedade **Suprimir Avisos**.</span><span class="sxs-lookup"><span data-stu-id="eec24-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="eec24-123">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="eec24-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec24-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eec24-124">See Also</span></span>  
 [<span data-ttu-id="eec24-125">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="eec24-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="eec24-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="eec24-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="eec24-127">Erros do Compilador do C#</span><span class="sxs-lookup"><span data-stu-id="eec24-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
