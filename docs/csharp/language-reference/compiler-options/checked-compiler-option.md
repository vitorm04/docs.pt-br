---
title: "-checked (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 63ba89ec42748ccea065bf0fd258fb559abca099
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="checked-c-compiler-options"></a><span data-ttu-id="00bfd-102">/checked (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="00bfd-102">/checked (C# Compiler Options)</span></span>
<span data-ttu-id="00bfd-103">A opção **/checked** especifica se uma instrução de aritmética de inteiros que resulta em um valor fora do intervalo do tipo de dados e que não está no escopo de uma palavra-chave [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md), causará uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00bfd-103">The **/checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00bfd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00bfd-104">Syntax</span></span>  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="00bfd-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="00bfd-105">Remarks</span></span>  
 <span data-ttu-id="00bfd-106">Uma instrução de aritmética de inteiros que está no escopo de uma palavra-chave `checked` ou `unchecked` não está sujeita ao efeito da opção **/checked**.</span><span class="sxs-lookup"><span data-stu-id="00bfd-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **/checked** option.</span></span>  
  
 <span data-ttu-id="00bfd-107">Se uma instrução de aritmética de inteiros que não está no escopo de uma palavra-chave `checked` ou `unchecked` resultar em um valor fora do intervalo do tipo de dados e **/checked+** (**/checked**) for usado na compilação, a instrução causará uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00bfd-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **/checked+** (**/checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="00bfd-108">Se **/checked-** for usado na compilação, a instrução não causará uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00bfd-108">If **/checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="00bfd-109">O valor padrão desta opção é **/checked-**.</span><span class="sxs-lookup"><span data-stu-id="00bfd-109">The default value for this option is **/checked-**.</span></span> <span data-ttu-id="00bfd-110">Um cenário de uso de **/checked-** é a compilação de aplicativos grandes.</span><span class="sxs-lookup"><span data-stu-id="00bfd-110">One scenario for using **/checked-** is in building large applications.</span></span> <span data-ttu-id="00bfd-111">Às vezes, ferramentas automatizadas são usadas para compilar esses aplicativos e a ferramenta pode definir automaticamente **/checked** como +.</span><span class="sxs-lookup"><span data-stu-id="00bfd-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **/checked** to +.</span></span> <span data-ttu-id="00bfd-112">Você pode substituir o padrão global da ferramenta especificando **/checked-**.</span><span class="sxs-lookup"><span data-stu-id="00bfd-112">You can override the tool's global default by specifying **/checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="00bfd-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="00bfd-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="00bfd-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="00bfd-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="00bfd-115">Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="00bfd-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="00bfd-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="00bfd-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="00bfd-117">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="00bfd-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="00bfd-118">Modifique a propriedade **Procurar estouro/estouro negativo aritmético**.</span><span class="sxs-lookup"><span data-stu-id="00bfd-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="00bfd-119">Para acessar programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="00bfd-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00bfd-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00bfd-120">Example</span></span>  
 <span data-ttu-id="00bfd-121">O comando a seguir compila `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="00bfd-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="00bfd-122">O uso de `/checked` no comando especifica que qualquer instrução de aritmética de inteiros no arquivo que não está no escopo de uma palavra-chave `checked` ou `unchecked` e que resulta em um valor fora do intervalo do tipo de dados, causa uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="00bfd-122">The use of `/checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="00bfd-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00bfd-123">See Also</span></span>  
 <span data-ttu-id="00bfd-124">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="00bfd-124">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="00bfd-125">[Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties) </span><span class="sxs-lookup"><span data-stu-id="00bfd-125">[Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties) </span></span>  
 [<span data-ttu-id="00bfd-126">Introdução ao Designer de Projeto</span><span class="sxs-lookup"><span data-stu-id="00bfd-126">Introduction to the Project Designer</span></span>](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)

