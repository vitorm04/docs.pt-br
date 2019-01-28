---
title: -warnaserror (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: b208f6e4e768e400af203117d185944be285cb72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634604"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="c8c78-102">-warnaserror (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="c8c78-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="c8c78-103">A opção **-warnaserror+** trata todos os avisos como erros</span><span class="sxs-lookup"><span data-stu-id="c8c78-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c78-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8c78-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8c78-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8c78-105">Remarks</span></span>  
 <span data-ttu-id="c8c78-106">Quaisquer mensagens que seriam, normalmente, ser relatadas como avisos, são relatadas como erros e o processo de build é interrompido (os arquivos de saída não são compilados).</span><span class="sxs-lookup"><span data-stu-id="c8c78-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="c8c78-107">Por padrão, a opção **-warnaserror-** está em vigor, o que faz com que os avisos não impeçam a geração de um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c8c78-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="c8c78-108">A **-warnaserror**, que é a mesma que **-warnaserror+**, faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="c8c78-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="c8c78-109">Opcionalmente, se você deseja que apenas avisos específicos sejam tratados como erros, você pode especificar uma lista separada por vírgulas de números de aviso para serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="c8c78-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="c8c78-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) para especificar o nível de avisos que você deseja que o compilador exiba.</span><span class="sxs-lookup"><span data-stu-id="c8c78-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="c8c78-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) para desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="c8c78-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c8c78-112">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8c78-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c8c78-113">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8c78-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="c8c78-114">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="c8c78-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="c8c78-115">Modifique a propriedade **Tratar Avisos como Erros**.</span><span class="sxs-lookup"><span data-stu-id="c8c78-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="c8c78-116">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="c8c78-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c78-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8c78-117">Example</span></span>  
 <span data-ttu-id="c8c78-118">Compilar `in.cs` e fazer com que o compilador não exiba avisos:</span><span class="sxs-lookup"><span data-stu-id="c8c78-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8c78-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8c78-119">See also</span></span>

- [<span data-ttu-id="c8c78-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="c8c78-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="c8c78-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="c8c78-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
