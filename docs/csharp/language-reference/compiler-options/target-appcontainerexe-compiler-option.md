---
title: "-target:appcontainerexe (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e49047ee5a639189331b89f3c5e16f6a1f1d4cd5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="26f85-102">-target:appcontainerexe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="26f85-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="26f85-103">Se você usar a opção do compilador **-target:appcontainerexe**, o compilador criará um arquivo executável (.exe) do Windows que deverá ser executado em um contêiner de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="26f85-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="26f85-104">Essa opção é equivalente a [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), mas foi projetada para aplicativos [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26f85-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f85-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26f85-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="26f85-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="26f85-106">Remarks</span></span>  
 <span data-ttu-id="26f85-107">Para exigir que o aplicativo seja executado em um contêiner de aplicativos, esta opção define um bit no arquivo [PE](http://go.microsoft.com/fwlink/p/?LinkId=236960).</span><span class="sxs-lookup"><span data-stu-id="26f85-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE) file.</span></span> <span data-ttu-id="26f85-108">Quando esse bit estiver definido, ocorrerá um erro se o método CreateProcess tentar inicializar o arquivo executável fora de um contêiner de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="26f85-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="26f85-109">A menos que você use a opção [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../../csharp/programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="26f85-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="26f85-110">Quando você especifica essa opção em um prompt de comando, todos os arquivos até a próxima opção **-out** ou **-target** são usados para criar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="26f85-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="26f85-111">Para definir esta opção do compilador no IDE</span><span class="sxs-lookup"><span data-stu-id="26f85-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="26f85-112">No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="26f85-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="26f85-113">Na guia **Aplicativo**, na lista **Tipo de saída**, escolha **Aplicativo da Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="26f85-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="26f85-114">Essa opção está disponível apenas para modelos de aplicativo [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26f85-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="26f85-115">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="26f85-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26f85-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26f85-116">Example</span></span>  
 <span data-ttu-id="26f85-117">O comando a seguir compila `filename.cs` em um arquivo executável do Windows que pode ser executado somente em um contêiner de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="26f85-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="26f85-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26f85-118">See Also</span></span>  
 [<span data-ttu-id="26f85-119">-target (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="26f85-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="26f85-120">-target:winexe (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="26f85-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="26f85-121">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="26f85-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
