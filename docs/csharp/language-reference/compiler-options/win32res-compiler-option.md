---
title: "-win32res (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c24da8bb745847612d882d00eff7f03dbc60475
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="35267-102">-win32res (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="35267-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="35267-103">A opção **-win32res** insere um recurso do Win32 no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="35267-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35267-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35267-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="35267-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="35267-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="35267-106">O arquivo de recurso que você deseja adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="35267-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35267-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="35267-107">Remarks</span></span>  
 <span data-ttu-id="35267-108">Um arquivo de recurso do Win32 pode ser criado com o [Compilador de Recursos](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="35267-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="35267-109">O Compilador de Recursos é invocado quando você compila um programa do Visual C++; um arquivo .res é criado com base no arquivo .rc.</span><span class="sxs-lookup"><span data-stu-id="35267-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="35267-110">Um recurso do Win32 pode conter informações de versão ou de bitmap (ícone) que ajudariam a identificar seu aplicativo no Explorador de Arquivos.</span><span class="sxs-lookup"><span data-stu-id="35267-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="35267-111">Se você não especificar a **-win32res**, o compilador gerará informações de versão com base na versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="35267-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="35267-112">Consulte [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (para referenciar) ou [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (para anexar) um arquivo de recurso do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35267-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="35267-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35267-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="35267-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="35267-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="35267-115">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="35267-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="35267-116">Clique no botão **Arquivo de Recurso** e escolha um arquivo usando a caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="35267-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35267-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35267-117">Example</span></span>  
 <span data-ttu-id="35267-118">Compilar `in.cs` e anexar um arquivo de recurso do Win32 `rf.res` para produzir `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="35267-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="35267-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35267-119">See Also</span></span>  
 [<span data-ttu-id="35267-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="35267-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="35267-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="35267-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
