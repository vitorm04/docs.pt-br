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
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606270"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="ae549-102">-warnaserror (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ae549-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="ae549-103">A opção **-warnaserror+** trata todos os avisos como erros</span><span class="sxs-lookup"><span data-stu-id="ae549-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae549-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae549-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae549-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae549-105">Remarks</span></span>  
 <span data-ttu-id="ae549-106">Quaisquer mensagens que seriam, normalmente, ser relatadas como avisos, são relatadas como erros e o processo de build é interrompido (os arquivos de saída não são compilados).</span><span class="sxs-lookup"><span data-stu-id="ae549-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="ae549-107">Por padrão, a opção **-warnaserror-** está em vigor, o que faz com que os avisos não impeçam a geração de um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="ae549-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="ae549-108">A **-warnaserror**, que é a mesma que **-warnaserror+** , faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="ae549-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="ae549-109">Opcionalmente, se você deseja que apenas avisos específicos sejam tratados como erros, você pode especificar uma lista separada por vírgulas de números de aviso para serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="ae549-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="ae549-110">Use [-warn](./warn-compiler-option.md) para especificar o nível de avisos que você deseja que o compilador exiba.</span><span class="sxs-lookup"><span data-stu-id="ae549-110">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="ae549-111">Use [-nowarn](./nowarn-compiler-option.md) para desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="ae549-111">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ae549-112">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ae549-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ae549-113">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="ae549-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ae549-114">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ae549-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ae549-115">Modifique a propriedade **Tratar Avisos como Erros**.</span><span class="sxs-lookup"><span data-stu-id="ae549-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="ae549-116">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="ae549-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae549-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae549-117">Example</span></span>  
 <span data-ttu-id="ae549-118">Compilar `in.cs` e fazer com que o compilador não exiba avisos:</span><span class="sxs-lookup"><span data-stu-id="ae549-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae549-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae549-119">See also</span></span>

- [<span data-ttu-id="ae549-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="ae549-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ae549-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="ae549-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
