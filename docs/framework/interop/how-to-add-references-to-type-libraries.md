---
title: 'Como: Adicionar referências a bibliotecas de tipos'
description: Entenda como adicionar referências a bibliotecas de tipos no Visual Studio ou à compilação de linha de comando.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: a3c24385c9cc7debe95aa10369b050897415bc46
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617425"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="f4960-103">Como: Adicionar referências a bibliotecas de tipos</span><span class="sxs-lookup"><span data-stu-id="f4960-103">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="f4960-104">O Visual Studio gera um assembly de interoperabilidade que contém metadados quando você adiciona uma referência a uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f4960-104">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="f4960-105">Se um assembly de interoperabilidade primário estiver disponível, o Visual Studio usará o assembly existente antes de gerar um novo assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="f4960-105">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="f4960-106">Para adicionar uma referência a uma biblioteca de tipos no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4960-106">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="f4960-107">Instale o arquivo COM DLL ou EXE em seu computador, a menos que o arquivo Windows Setup.exe execute a instalação para você.</span><span class="sxs-lookup"><span data-stu-id="f4960-107">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="f4960-108">Escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="f4960-108">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="f4960-109">No Gerenciador de Referências, escolha **COM**.</span><span class="sxs-lookup"><span data-stu-id="f4960-109">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="f4960-110">Selecione a biblioteca de tipos na lista ou navegue até o arquivo .tlb.</span><span class="sxs-lookup"><span data-stu-id="f4960-110">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="f4960-111">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="f4960-111">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="f4960-112">No Gerenciador de Soluções, abra o menu de atalho da referência recém-adicionada e, depois, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f4960-112">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="f4960-113">Na janela **Propriedades**, verifique se a propriedade **Inserir Tipos de Interoperabilidade** está definida como **True**.</span><span class="sxs-lookup"><span data-stu-id="f4960-113">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="f4960-114">Isso faz com que o Visual Studio insira informações sobre tipos para tipos COM em seus executáveis, eliminando a necessidade de implantar assemblies de interoperabilidade primário com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4960-114">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4960-115">As opções de menu e de caixa de diálogo podem variar, dependendo da versão do Visual Studio que você está usando.</span><span class="sxs-lookup"><span data-stu-id="f4960-115">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="f4960-116">Para adicionar uma referência a uma biblioteca de tipos para compilação da linha de comando</span><span class="sxs-lookup"><span data-stu-id="f4960-116">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="f4960-117">Gere um assembly de interoperabilidade, conforme descrito em [Como gerar assemblies de interoperabilidade em bibliotecas de tipos](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="f4960-117">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="f4960-118">Use a opção de compilador [-link (opções do compilador C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) com o nome do assembly de interoperabilidade para inserir informações de tipo para tipos com em seus executáveis.</span><span class="sxs-lookup"><span data-stu-id="f4960-118">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4960-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4960-119">See also</span></span>

- [<span data-ttu-id="f4960-120">Importando uma biblioteca de tipos como um assembly</span><span class="sxs-lookup"><span data-stu-id="f4960-120">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="f4960-121">Expondo componentes do COM para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f4960-121">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="f4960-122">Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4960-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="f4960-123">-link (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="f4960-123">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="f4960-124">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4960-124">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
