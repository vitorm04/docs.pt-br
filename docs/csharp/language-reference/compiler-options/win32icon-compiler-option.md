---
title: "-win32icon (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2ec19bacb975732f2ae04b8cefbfaeaa518b6f15
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="59978-102">-win32icon (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="59978-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="59978-103">A opção **-win32icon** insere um arquivo .ico no arquivo de saída, que fornece ao arquivo de saída a aparência desejada no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="59978-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59978-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59978-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="59978-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="59978-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="59978-106">O arquivo .ico que você deseja adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="59978-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59978-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="59978-107">Remarks</span></span>  
 <span data-ttu-id="59978-108">Um arquivo .ico pode ser criado com o [Compilador de Recurso](https://msdn.microsoft.com/library/aa381042.aspx).</span><span class="sxs-lookup"><span data-stu-id="59978-108">An .ico file can be created with the [Resource Compiler](https://msdn.microsoft.com/library/aa381042.aspx).</span></span> <span data-ttu-id="59978-109">O Compilador de Recurso é invocado quando você compila um programa do Visual C++; um arquivo .ico é criado com base no arquivo .rc.</span><span class="sxs-lookup"><span data-stu-id="59978-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="59978-110">Consulte [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (para referenciar) ou [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (para anexar) um arquivo de recurso do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59978-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="59978-111">Consulte [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) para importar um arquivo .res.</span><span class="sxs-lookup"><span data-stu-id="59978-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="59978-112">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59978-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="59978-113">Abra a página de **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="59978-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="59978-114">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="59978-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="59978-115">Modifique a propriedade **Ícone do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="59978-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="59978-116">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="59978-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59978-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59978-117">Example</span></span>  
 <span data-ttu-id="59978-118">Compilar `in.cs` e anexar um arquivo .ico `rf.ico` para produzir `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="59978-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="59978-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59978-119">See Also</span></span>  
 [<span data-ttu-id="59978-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="59978-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="59978-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="59978-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
