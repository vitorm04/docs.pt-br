---
title: Como adicionar referências a bibliotecas de tipos
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c05e7399e9378751f803ae56dfaf664490e6d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388411"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="e218a-102">Como adicionar referências a bibliotecas de tipos</span><span class="sxs-lookup"><span data-stu-id="e218a-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="e218a-103">O Visual Studio gera um assembly de interoperabilidade que contém metadados quando você adiciona uma referência a uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="e218a-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="e218a-104">Se um assembly de interoperabilidade primário estiver disponível, o Visual Studio usará o assembly existente antes de gerar um novo assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="e218a-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="e218a-105">Para adicionar uma referência a uma biblioteca de tipos no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e218a-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="e218a-106">Instale o arquivo COM DLL ou EXE em seu computador, a menos que o arquivo Windows Setup.exe execute a instalação para você.</span><span class="sxs-lookup"><span data-stu-id="e218a-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="e218a-107">Escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="e218a-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="e218a-108">No Gerenciador de Referências, escolha **COM**.</span><span class="sxs-lookup"><span data-stu-id="e218a-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="e218a-109">Selecione a biblioteca de tipos na lista ou navegue até o arquivo .tlb.</span><span class="sxs-lookup"><span data-stu-id="e218a-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="e218a-110">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="e218a-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="e218a-111">No Gerenciador de Soluções, abra o menu de atalho da referência recém-adicionada e, depois, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e218a-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="e218a-112">Na janela **Propriedades**, verifique se a propriedade **Inserir Tipos de Interoperabilidade** está definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="e218a-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="e218a-113">Isso faz com que o Visual Studio insira informações sobre tipos para tipos COM em seus executáveis, eliminando a necessidade de implantar assemblies de interoperabilidade primário com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e218a-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e218a-114">As opções de menu e de caixa de diálogo podem variar, dependendo da versão do Visual Studio que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e218a-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="e218a-115">Para adicionar uma referência a uma biblioteca de tipos para compilação da linha de comando</span><span class="sxs-lookup"><span data-stu-id="e218a-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="e218a-116">Gere um assembly de interoperabilidade, conforme descrito em [Como gerar assemblies de interoperabilidade em bibliotecas de tipos](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="e218a-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="e218a-117">Use a opção do compilador [/link (Opções do Compilador do C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) com o nome do assembly de interoperabilidade para inserir informações de tipo para tipos COM nos executáveis.</span><span class="sxs-lookup"><span data-stu-id="e218a-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e218a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e218a-118">See Also</span></span>  
 [<span data-ttu-id="e218a-119">Importando uma biblioteca de tipos como um assembly</span><span class="sxs-lookup"><span data-stu-id="e218a-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="e218a-120">Expondo componentes do COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e218a-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
 <span data-ttu-id="e218a-121">[Instruções passo a passo: inserindo informações de tipo dos Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e218a-121">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>  
 [<span data-ttu-id="e218a-122">Instruções passo a passo: inserindo tipos de assemblies gerenciados</span><span class="sxs-lookup"><span data-stu-id="e218a-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="e218a-123">/link (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="e218a-123">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="e218a-124">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e218a-124">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
