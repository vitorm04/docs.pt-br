---
title: -nowarn (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: b455a2f719e7350c51cf4a1f095d4669529d0e5e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592804"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="47315-102">-nowarn (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="47315-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="47315-103">A opção **-nowarn** permite suprimir a exibição de um ou mais avisos pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="47315-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="47315-104">Separe vários números de aviso com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="47315-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47315-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47315-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="47315-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="47315-106">Arguments</span></span>  
 <span data-ttu-id="47315-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="47315-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="47315-108">Números de aviso que você deseja que o compilador suprima.</span><span class="sxs-lookup"><span data-stu-id="47315-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47315-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="47315-109">Remarks</span></span>  
 <span data-ttu-id="47315-110">Você só precisa especificar a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="47315-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="47315-111">Por exemplo, se quiser suprimir CS0028, você pode especificar `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="47315-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="47315-112">O compilador ignorará silenciosamente números de aviso passados para `-nowarn` que eram válidos em versões anteriores, mas que foram removidos do compilador.</span><span class="sxs-lookup"><span data-stu-id="47315-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="47315-113">Por exemplo, CS0679 era válido no compilador no Visual Studio .NET 2002, mas foi removido posteriormente.</span><span class="sxs-lookup"><span data-stu-id="47315-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="47315-114">Os avisos a seguir não podem ser suprimidos pela opção `-nowarn`:</span><span class="sxs-lookup"><span data-stu-id="47315-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="47315-115">Aviso do compilador (nível 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="47315-115">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="47315-116">Aviso do compilador (nível 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="47315-116">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="47315-117">Aviso do compilador (nível 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="47315-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="47315-118">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47315-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="47315-119">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="47315-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="47315-120">Para obter detalhes, consulte [Página de Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="47315-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="47315-121">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="47315-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="47315-122">Modifique a propriedade **Suprimir Avisos**.</span><span class="sxs-lookup"><span data-stu-id="47315-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="47315-123">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="47315-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47315-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47315-124">See also</span></span>

- [<span data-ttu-id="47315-125">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="47315-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="47315-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="47315-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="47315-127">Erros do Compilador do C#</span><span class="sxs-lookup"><span data-stu-id="47315-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
