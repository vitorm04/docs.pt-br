---
description: -checked (opções do compilador C#)
title: -checked (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: c92ad61b2f482631230e0e6aeb0af5716a4fcb61
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196826"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="054d5-103">-checked (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="054d5-103">-checked (C# Compiler Options)</span></span>

<span data-ttu-id="054d5-104">A opção **-checked** especifica se uma instrução de aritmética de inteiros que resulta em um valor fora do intervalo do tipo de dados e que não está no escopo de uma palavra-chave [checked](../keywords/checked.md) ou [unchecked](../keywords/unchecked.md), causa uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="054d5-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="054d5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="054d5-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="054d5-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="054d5-106">Remarks</span></span>  

 <span data-ttu-id="054d5-107">Uma instrução de aritmética de inteiros que está no escopo de uma palavra-chave `checked` ou `unchecked` não está sujeita ao efeito da opção **-checked**.</span><span class="sxs-lookup"><span data-stu-id="054d5-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="054d5-108">Se uma instrução de aritmética de inteiros que não está no escopo de uma palavra-chave `checked` ou `unchecked` resultar em um valor fora do intervalo do tipo de dados e **-checked+** (ou **-checked**) for usado na compilação, a instrução causará uma exceção no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="054d5-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="054d5-109">Se **-checked-** for usado na compilação, a instrução não causará uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="054d5-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="054d5-110">O valor padrão para essa opção é **-checked-**. A verificação de estouro é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="054d5-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="054d5-111">Às vezes, as ferramentas automatizadas que são usadas para compilar grandes aplicativos definem -checked como +.</span><span class="sxs-lookup"><span data-stu-id="054d5-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="054d5-112">Um cenário para uso de -checked- é substituir o padrão global da ferramenta especificando -checked-.</span><span class="sxs-lookup"><span data-stu-id="054d5-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="054d5-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="054d5-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="054d5-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="054d5-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="054d5-115">Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="054d5-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="054d5-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="054d5-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="054d5-117">Clique no botão **Avançado** .</span><span class="sxs-lookup"><span data-stu-id="054d5-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="054d5-118">Modifique a propriedade **verificar estouro aritmético** .</span><span class="sxs-lookup"><span data-stu-id="054d5-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="054d5-119">Para acessar programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="054d5-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="054d5-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="054d5-120">Example</span></span>  

 <span data-ttu-id="054d5-121">O comando a seguir compila `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="054d5-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="054d5-122">O uso de `-checked` no comando especifica que qualquer instrução de aritmética de inteiros no arquivo que não está no escopo de uma palavra-chave `checked` ou `unchecked` e que resulta em um valor fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="054d5-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="054d5-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="054d5-123">See also</span></span>

- [<span data-ttu-id="054d5-124">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="054d5-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="054d5-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="054d5-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
