---
title: "-target:winmdobj (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 444fcd69db327ea9d9c3dc739b42520bb9472c4d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="05b7a-102">-target:winmdobj (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="05b7a-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="05b7a-103">Se você usar a opção do compilador **-target:winmdobj**, o compilador criará um arquivo .winmdobj intermediário que pode ser convertido em um arquivo binário do Windows Runtime (.winmd).</span><span class="sxs-lookup"><span data-stu-id="05b7a-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="05b7a-104">O arquivo .winmd pode, então, ser consumido por programas JavaScript e C++, bem como programas de linguagem gerenciada.</span><span class="sxs-lookup"><span data-stu-id="05b7a-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b7a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05b7a-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="05b7a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="05b7a-106">Remarks</span></span>  
 <span data-ttu-id="05b7a-107">A configuração **winmdobj** indica para o compilador que um módulo intermediário é necessário.</span><span class="sxs-lookup"><span data-stu-id="05b7a-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="05b7a-108">Em resposta, o Visual Studio compila a biblioteca de classes do C# como um arquivo .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="05b7a-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="05b7a-109">O arquivo .winmdobj pode, então, ser alimentado por meio da ferramenta de exportação <xref:Microsoft.Build.Tasks.WinMDExp> para produzir um arquivo de metadados do Windows (.winmd).</span><span class="sxs-lookup"><span data-stu-id="05b7a-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="05b7a-110">O arquivo .winmd contém o código da biblioteca original e os metadados do WinMD que são usados pelo JavaScript ou C++ e pelo Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="05b7a-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="05b7a-111">A saída de um arquivo que é compilado usando a opção do compilador **-target:winmdobj** foi criada para ser usada apenas como entrada para a ferramenta de exportação WimMDExp. O arquivo .winmdobj em si não é referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="05b7a-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="05b7a-112">A menos que você use a opção [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do primeiro arquivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="05b7a-112">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="05b7a-113">Um método [Main](../../../csharp/programming-guide/main-and-command-args/index.md) não é necessário.</span><span class="sxs-lookup"><span data-stu-id="05b7a-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="05b7a-114">Se você especificar a opção -target:winmdobj em um prompt de comando, todos os arquivos até a próxima opção **-out** ou [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) serão usados para criar o programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="05b7a-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="05b7a-115">Para definir esta opção de compilador no IDE do Visual Studio para um aplicativo da Windows Store</span><span class="sxs-lookup"><span data-stu-id="05b7a-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1.  <span data-ttu-id="05b7a-116">No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="05b7a-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="05b7a-117">Escolha a guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="05b7a-117">Choose the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="05b7a-118">Na lista **Tipo de saída**, escolha **Arquivo WinMD**.</span><span class="sxs-lookup"><span data-stu-id="05b7a-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="05b7a-119">A opção **Arquivo WinMD** está disponível apenas para modelos de aplicativo [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05b7a-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="05b7a-120">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="05b7a-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b7a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05b7a-121">Example</span></span>  
 <span data-ttu-id="05b7a-122">O comando a seguir compila `filename.cs` em um arquivo .winmdobj intermediário.</span><span class="sxs-lookup"><span data-stu-id="05b7a-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="05b7a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05b7a-123">See Also</span></span>  
 [<span data-ttu-id="05b7a-124">-target (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="05b7a-124">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="05b7a-125">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="05b7a-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
