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
ms.openlocfilehash: 5c90696edd3031271e16cd2c1a332da5b605f81f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125937"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="3b7f8-103">-checked (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="3b7f8-103">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="3b7f8-104">A opção **-checked** especifica se uma instrução de aritmética de inteiros que resulta em um valor fora do intervalo do tipo de dados e que não está no escopo de uma palavra-chave [checked](../keywords/checked.md) ou [unchecked](../keywords/unchecked.md), causa uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-104">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7f8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b7f8-105">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b7f8-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b7f8-106">Remarks</span></span>  
 <span data-ttu-id="3b7f8-107">Uma instrução de aritmética de inteiros que está no escopo de uma palavra-chave `checked` ou `unchecked` não está sujeita ao efeito da opção **-checked**.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-107">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="3b7f8-108">Se uma instrução de aritmética de inteiros que não está no escopo de uma palavra-chave `checked` ou `unchecked` resultar em um valor fora do intervalo do tipo de dados e **-checked+** (ou **-checked**) for usado na compilação, a instrução causará uma exceção no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-108">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="3b7f8-109">Se **-checked-** for usado na compilação, a instrução não causará uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-109">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="3b7f8-110">O valor padrão para essa opção é **-checked-**. A verificação de estouro é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-110">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="3b7f8-111">Às vezes, as ferramentas automatizadas que são usadas para compilar grandes aplicativos definem -checked como +.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-111">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="3b7f8-112">Um cenário para uso de -checked- é substituir o padrão global da ferramenta especificando -checked-.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-112">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3b7f8-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b7f8-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3b7f8-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="3b7f8-115">Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="3b7f8-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="3b7f8-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="3b7f8-117">Clique no botão **Avançado** .</span><span class="sxs-lookup"><span data-stu-id="3b7f8-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="3b7f8-118">Modifique a propriedade **verificar estouro aritmético** .</span><span class="sxs-lookup"><span data-stu-id="3b7f8-118">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="3b7f8-119">Para acessar programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7f8-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b7f8-120">Example</span></span>  
 <span data-ttu-id="3b7f8-121">O comando a seguir compila `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="3b7f8-122">O uso de `-checked` no comando especifica que qualquer instrução de aritmética de inteiros no arquivo que não está no escopo de uma palavra-chave `checked` ou `unchecked` e que resulta em um valor fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b7f8-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="3b7f8-123">See also</span></span>

- [<span data-ttu-id="3b7f8-124">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="3b7f8-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3b7f8-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="3b7f8-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
