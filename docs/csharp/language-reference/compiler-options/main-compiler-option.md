---
title: -main (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212414"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="0f781-102">-main (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="0f781-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="0f781-103">Esta opção especifica a classe que contém o ponto de entrada para o programa, se mais de uma classe contiver um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="0f781-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f781-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f781-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f781-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f781-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="0f781-106">O tipo que contém o método **Main**.</span><span class="sxs-lookup"><span data-stu-id="0f781-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f781-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f781-107">Remarks</span></span>  
 <span data-ttu-id="0f781-108">Se sua compilação incluir mais de um tipo com um método [Main](../../../csharp/programming-guide/main-and-command-args/index.md), você poderá especificar qual tipo contém o método **Main** que deseja usar como o ponto de entrada para o programa.</span><span class="sxs-lookup"><span data-stu-id="0f781-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="0f781-109">Essa opção é para uso durante a compilação de um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="0f781-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0f781-110">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0f781-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="0f781-111">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="0f781-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="0f781-112">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="0f781-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="0f781-113">Modifique a propriedade **Objeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="0f781-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="0f781-114">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f781-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f781-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f781-115">Example</span></span>  
 <span data-ttu-id="0f781-116">Compile `t2.cs` e `t3.cs`, especificando que o método **Main** será encontrado em `Test2`:</span><span class="sxs-lookup"><span data-stu-id="0f781-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f781-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f781-117">See Also</span></span>  
 [<span data-ttu-id="0f781-118">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="0f781-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="0f781-119">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="0f781-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
