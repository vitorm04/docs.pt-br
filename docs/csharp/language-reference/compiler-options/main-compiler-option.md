---
title: "-main (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6dca6e62dbf69783babf2e16dc4e7c36c6705c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="main-c-compiler-options"></a><span data-ttu-id="c1108-102">/main (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="c1108-102">/main (C# Compiler Options)</span></span>
<span data-ttu-id="c1108-103">Esta opção especifica a classe que contém o ponto de entrada para o programa, se mais de uma classe contiver um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="c1108-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1108-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1108-104">Syntax</span></span>  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1108-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c1108-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="c1108-106">O tipo que contém o método **Main**.</span><span class="sxs-lookup"><span data-stu-id="c1108-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1108-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1108-107">Remarks</span></span>  
 <span data-ttu-id="c1108-108">Se sua compilação incluir mais de um tipo com um método [Main](../../../csharp/programming-guide/main-and-command-args/index.md), você poderá especificar qual tipo contém o método **Main** que deseja usar como o ponto de entrada para o programa.</span><span class="sxs-lookup"><span data-stu-id="c1108-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="c1108-109">Essa opção é para uso durante a compilação de um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="c1108-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c1108-110">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1108-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c1108-111">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="c1108-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="c1108-112">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="c1108-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="c1108-113">Modifique a propriedade **Objeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="c1108-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="c1108-114">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1108-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1108-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1108-115">Example</span></span>  
 <span data-ttu-id="c1108-116">Compile `t2.cs` e `t3.cs`, especificando que o método **Main** será encontrado em `Test2`:</span><span class="sxs-lookup"><span data-stu-id="c1108-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1108-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1108-117">See Also</span></span>  
 [<span data-ttu-id="c1108-118">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="c1108-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="c1108-119">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="c1108-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
