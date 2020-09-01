---
description: -win32icon (opções do compilador C#)
title: -win32icon (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 76a54f9011371492bdc15f15c3e40d51082deed3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138404"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="be75f-103">-win32icon (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="be75f-103">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="be75f-104">A opção **-win32icon** insere um arquivo .ico no arquivo de saída, que fornece ao arquivo de saída a aparência desejada no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="be75f-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be75f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be75f-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="be75f-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="be75f-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="be75f-107">O arquivo .ico que você deseja adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="be75f-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be75f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="be75f-108">Remarks</span></span>  
 <span data-ttu-id="be75f-109">Um arquivo .ico pode ser criado com o [Compilador de Recurso](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="be75f-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="be75f-110">O Compilador de Recurso é invocado quando você compila um programa do Visual C++; um arquivo .ico é criado com base no arquivo .rc.</span><span class="sxs-lookup"><span data-stu-id="be75f-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="be75f-111">Consulte [-linkresource](./linkresource-compiler-option.md) (para referenciar) ou [-resource](./resource-compiler-option.md) (para anexar) um arquivo de recurso do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be75f-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="be75f-112">Consulte [-win32res](./win32res-compiler-option.md) para importar um arquivo. res.</span><span class="sxs-lookup"><span data-stu-id="be75f-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="be75f-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be75f-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="be75f-114">Abra a página de **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="be75f-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="be75f-115">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="be75f-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="be75f-116">Modifique a propriedade **Ícone do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="be75f-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="be75f-117">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="be75f-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be75f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be75f-118">Example</span></span>  
 <span data-ttu-id="be75f-119">Compilar `in.cs` e anexar um arquivo .ico `rf.ico` para produzir `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="be75f-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="be75f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="be75f-120">See also</span></span>

- [<span data-ttu-id="be75f-121">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="be75f-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="be75f-122">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="be75f-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
