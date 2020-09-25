---
description: -warnaserror (opções do compilador C#)
title: -warnaserror (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 9c3b307668968865b401aedc04c79f95d4f32513
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171332"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="89e90-103">-warnaserror (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="89e90-103">-warnaserror (C# Compiler Options)</span></span>

<span data-ttu-id="89e90-104">A opção **-warnaserror+** trata todos os avisos como erros</span><span class="sxs-lookup"><span data-stu-id="89e90-104">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e90-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89e90-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="89e90-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="89e90-106">Remarks</span></span>  

 <span data-ttu-id="89e90-107">Quaisquer mensagens que seriam, normalmente, ser relatadas como avisos, são relatadas como erros e o processo de build é interrompido (os arquivos de saída não são compilados).</span><span class="sxs-lookup"><span data-stu-id="89e90-107">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="89e90-108">Por padrão, a opção **-warnaserror-** está em vigor, o que faz com que os avisos não impeçam a geração de um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="89e90-108">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="89e90-109">A **-warnaserror**, que é a mesma que **-warnaserror+**, faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="89e90-109">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="89e90-110">Opcionalmente, se você deseja que apenas avisos específicos sejam tratados como erros, você pode especificar uma lista separada por vírgulas de números de aviso para serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="89e90-110">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="89e90-111">O conjunto de todos os avisos de nulidade pode ser especificado com a abreviação **anulável** .</span><span class="sxs-lookup"><span data-stu-id="89e90-111">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="89e90-112">Use [-warn](./warn-compiler-option.md) para especificar o nível de avisos que você deseja que o compilador exiba.</span><span class="sxs-lookup"><span data-stu-id="89e90-112">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="89e90-113">Use [-nowarn](./nowarn-compiler-option.md) para desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="89e90-113">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="89e90-114">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="89e90-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="89e90-115">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="89e90-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="89e90-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="89e90-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="89e90-117">Modifique a propriedade **Tratar Avisos como Erros**.</span><span class="sxs-lookup"><span data-stu-id="89e90-117">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="89e90-118">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="89e90-118">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89e90-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89e90-119">Example</span></span>  

 <span data-ttu-id="89e90-120">Compilar `in.cs` e fazer com que o compilador não exiba avisos:</span><span class="sxs-lookup"><span data-stu-id="89e90-120">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="89e90-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="89e90-121">See also</span></span>

- [<span data-ttu-id="89e90-122">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="89e90-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="89e90-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="89e90-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
