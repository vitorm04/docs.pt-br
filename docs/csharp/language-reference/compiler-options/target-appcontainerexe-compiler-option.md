---
title: -target:appcontainerexe (opções do compilador C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204530"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="3c2dd-102">-target:appcontainerexe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="3c2dd-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="3c2dd-103">Se você usar a opção do compilador **-target:appcontainerexe**, o compilador criará um arquivo executável (.exe) do Windows que deverá ser executado em um contêiner de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="3c2dd-104">Essa opção é equivalente a [-target: winexe](./target-winexe-compiler-option.md) , mas é projetada para aplicativos da loja do Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2dd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c2dd-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="3c2dd-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c2dd-106">Remarks</span></span>  
 <span data-ttu-id="3c2dd-107">Para exigir que o aplicativo seja executado em um contêiner de aplicativos, esta opção define um bit no arquivo [PE](/windows/desktop/Debug/pe-format).</span><span class="sxs-lookup"><span data-stu-id="3c2dd-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="3c2dd-108">Quando esse bit estiver definido, ocorrerá um erro se o método CreateProcess tentar inicializar o arquivo executável fora de um contêiner de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="3c2dd-109">A menos que você use a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="3c2dd-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="3c2dd-110">Quando você especifica essa opção em um prompt de comando, todos os arquivos até a próxima opção **-out** ou **-target** são usados para criar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="3c2dd-111">Para definir esta opção do compilador no IDE</span><span class="sxs-lookup"><span data-stu-id="3c2dd-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="3c2dd-112">No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="3c2dd-113">Na guia **Aplicativo**, na lista **Tipo de saída**, escolha **Aplicativo da Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="3c2dd-114">Essa opção está disponível somente para modelos de aplicativo da loja do Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-114">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="3c2dd-115">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c2dd-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c2dd-116">Example</span></span>  
 <span data-ttu-id="3c2dd-117">O comando a seguir compila `filename.cs` em um arquivo executável do Windows que pode ser executado somente em um contêiner de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c2dd-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c2dd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c2dd-118">See also</span></span>

- [<span data-ttu-id="3c2dd-119">-target (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="3c2dd-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="3c2dd-120">-target:winexe (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="3c2dd-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="3c2dd-121">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="3c2dd-121">C# Compiler Options</span></span>](./index.md)
