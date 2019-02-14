---
title: 'Como: Carregar um som de forma assíncrona dentro de um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 8619ea3fb06a9c7c6896176fe3ae2a4b8dfe4ded
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260693"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="6840d-102">Como: Carregar um som de forma assíncrona dentro de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="6840d-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="6840d-103">O exemplo de código a seguir carrega um som de forma assíncrona de uma URL e é reproduzido em um novo thread.</span><span class="sxs-lookup"><span data-stu-id="6840d-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6840d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6840d-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6840d-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6840d-105">Compiling the Code</span></span>  
 <span data-ttu-id="6840d-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6840d-106">This example requires:</span></span>  
  
-   <span data-ttu-id="6840d-107">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6840d-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="6840d-108">Se você substituir o nome de arquivo `"http://www.tailspintoys.com/sounds/stop.wav"` com um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="6840d-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="6840d-109">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6840d-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6840d-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="6840d-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6840d-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="6840d-111">Robust Programming</span></span>  
 <span data-ttu-id="6840d-112">Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.</span><span class="sxs-lookup"><span data-stu-id="6840d-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="6840d-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="6840d-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6840d-114">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="6840d-114">The path name is malformed.</span></span> <span data-ttu-id="6840d-115">Por exemplo, ele contém caracteres que não são válidos ou é somente um espaço em branco (<xref:System.ArgumentException> classe).</span><span class="sxs-lookup"><span data-stu-id="6840d-115">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="6840d-116">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="6840d-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="6840d-117">É o nome do caminho `Nothing` (<xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="6840d-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="6840d-118">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="6840d-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="6840d-119">O caminho não é válido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="6840d-119">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="6840d-120">O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="6840d-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6840d-121">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6840d-121">.NET Framework Security</span></span>  
 <span data-ttu-id="6840d-122">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6840d-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="6840d-123">Por exemplo, o arquivo `Form1.vb` não pode ser um arquivo de origem do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6840d-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="6840d-124">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6840d-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6840d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6840d-125">See also</span></span>
- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="6840d-126">Como: Reproduzir um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="6840d-126">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
