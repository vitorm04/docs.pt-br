---
title: "Como adicionar referências a bibliotecas de tipos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a0c4fc9b96ec310e20839be851cfddbb34e09201
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="e0709-102">Como adicionar referências a bibliotecas de tipos</span><span class="sxs-lookup"><span data-stu-id="e0709-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="e0709-103">O Visual Studio gera um assembly de interoperabilidade que contém metadados quando você adiciona uma referência a uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="e0709-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="e0709-104">Se um assembly de interoperabilidade primário estiver disponível, o Visual Studio usará o assembly existente antes de gerar um novo assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="e0709-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="e0709-105">Para adicionar uma referência a uma biblioteca de tipos no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0709-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="e0709-106">Instale o arquivo COM DLL ou EXE em seu computador, a menos que o arquivo Windows Setup.exe execute a instalação para você.</span><span class="sxs-lookup"><span data-stu-id="e0709-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="e0709-107">Escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="e0709-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="e0709-108">No Gerenciador de Referências, escolha **COM**.</span><span class="sxs-lookup"><span data-stu-id="e0709-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="e0709-109">Selecione a biblioteca de tipos na lista ou navegue até o arquivo .tlb.</span><span class="sxs-lookup"><span data-stu-id="e0709-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="e0709-110">Escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="e0709-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="e0709-111">No Gerenciador de Soluções, abra o menu de atalho da referência recém-adicionada e, depois, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e0709-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="e0709-112">Na janela **Propriedades**, verifique se a propriedade **Inserir Tipos de Interoperabilidade** está definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="e0709-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="e0709-113">Isso faz com que o Visual Studio insira informações sobre tipos para tipos COM em seus executáveis, eliminando a necessidade de implantar assemblies de interoperabilidade primário com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0709-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0709-114">As opções de menu e de caixa de diálogo podem variar, dependendo da versão do Visual Studio que você está usando.</span><span class="sxs-lookup"><span data-stu-id="e0709-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="e0709-115">Para adicionar uma referência a uma biblioteca de tipos para compilação da linha de comando</span><span class="sxs-lookup"><span data-stu-id="e0709-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="e0709-116">Gere um assembly de interoperabilidade, conforme descrito em [Como gerar assemblies de interoperabilidade em bibliotecas de tipos](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="e0709-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="e0709-117">Use a opção do compilador [/link (Opções do Compilador do C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) com o nome do assembly de interoperabilidade para inserir informações de tipo para tipos COM nos executáveis.</span><span class="sxs-lookup"><span data-stu-id="e0709-117">Use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0709-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0709-118">See Also</span></span>  
 <span data-ttu-id="e0709-119">[Importando uma biblioteca de tipos como um assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="e0709-119">[Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md) </span></span>  
 <span data-ttu-id="e0709-120">[Expondo componentes COM para o .NET Framework](../../../docs/framework/interop/exposing-com-components.md) </span><span class="sxs-lookup"><span data-stu-id="e0709-120">[Exposing COM Components to the .NET Framework](../../../docs/framework/interop/exposing-com-components.md) </span></span>  
 <span data-ttu-id="e0709-121">[Instruções passo a passo: Inserindo informações de tipo dos Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) </span><span class="sxs-lookup"><span data-stu-id="e0709-121">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) </span></span>  
 <span data-ttu-id="e0709-122">[Instruções passo a passo: Inserindo tipos de assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span><span class="sxs-lookup"><span data-stu-id="e0709-122">[Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span></span>  
 <span data-ttu-id="e0709-123">[/link (opções do compilador C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="e0709-123">[/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) </span></span>  
 [<span data-ttu-id="e0709-124">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0709-124">/link (Visual Basic)</span></span>](~/docs/visual-basic/reference/command-line-compiler/link.md)

