---
title: -checked (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4ed8467b0e1923aedf38edfd4a25414cbcb88b7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218306"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="08997-102">-checked (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="08997-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="08997-103">A opção **-checked** especifica se uma instrução de aritmética de inteiros que resulta em um valor fora do intervalo do tipo de dados e que não está no escopo de uma palavra-chave [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md), causa uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08997-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08997-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08997-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="08997-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="08997-105">Remarks</span></span>  
 <span data-ttu-id="08997-106">Uma instrução de aritmética de inteiros que está no escopo de uma palavra-chave `checked` ou `unchecked` não está sujeita ao efeito da opção **-checked**.</span><span class="sxs-lookup"><span data-stu-id="08997-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="08997-107">Se uma instrução de aritmética de inteiros que não está no escopo de uma palavra-chave `checked` ou `unchecked` resultar em um valor fora do intervalo do tipo de dados e **-checked+** (**-checked**) for usado na compilação, a instrução causará uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08997-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (**-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="08997-108">Se **-checked-** for usado na compilação, a instrução não causará uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08997-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="08997-109">O valor padrão desta opção é **-checked-**.</span><span class="sxs-lookup"><span data-stu-id="08997-109">The default value for this option is **-checked-**.</span></span> <span data-ttu-id="08997-110">Um cenário de uso de **-checked-** é a compilação de aplicativos grandes.</span><span class="sxs-lookup"><span data-stu-id="08997-110">One scenario for using **-checked-** is in building large applications.</span></span> <span data-ttu-id="08997-111">Às vezes, ferramentas automatizadas são usadas para compilar esses aplicativos e esse tipo de ferramenta pode definir automaticamente **-checked** como +.</span><span class="sxs-lookup"><span data-stu-id="08997-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **-checked** to +.</span></span> <span data-ttu-id="08997-112">Você pode substituir o padrão global da ferramenta especificando **-checked-**.</span><span class="sxs-lookup"><span data-stu-id="08997-112">You can override the tool's global default by specifying **-checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="08997-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08997-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="08997-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="08997-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="08997-115">Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="08997-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="08997-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="08997-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="08997-117">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="08997-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="08997-118">Modifique a propriedade **Procurar estouro/estouro negativo aritmético**.</span><span class="sxs-lookup"><span data-stu-id="08997-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="08997-119">Para acessar programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="08997-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08997-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08997-120">Example</span></span>  
 <span data-ttu-id="08997-121">O comando a seguir compila `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="08997-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="08997-122">O uso de `-checked` no comando especifica que qualquer instrução de aritmética de inteiros no arquivo que não está no escopo de uma palavra-chave `checked` ou `unchecked` e que resulta em um valor fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="08997-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="08997-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08997-123">See Also</span></span>  
 [<span data-ttu-id="08997-124">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="08997-124">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="08997-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="08997-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
