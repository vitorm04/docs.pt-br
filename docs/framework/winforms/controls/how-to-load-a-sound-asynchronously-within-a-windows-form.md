---
title: Como carregar um som de forma assíncrona dentro de um Windows Form
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 2de2be478e81183201cc85e1a6dfd6f1a1833af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538604"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="e5c74-102">Como carregar um som de forma assíncrona dentro de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="e5c74-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="e5c74-103">O exemplo de código a seguir carrega um som de forma assíncrona de uma URL e é reproduzido em um novo thread.</span><span class="sxs-lookup"><span data-stu-id="e5c74-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5c74-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5c74-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5c74-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e5c74-105">Compiling the Code</span></span>  
 <span data-ttu-id="e5c74-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e5c74-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e5c74-107">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e5c74-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="e5c74-108">Se você substituir o nome de arquivo `"http://www.tailspintoys.com/sounds/stop.wav"` com um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="e5c74-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="e5c74-109">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e5c74-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e5c74-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e5c74-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e5c74-111">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e5c74-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e5c74-112">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e5c74-112">Robust Programming</span></span>  
 <span data-ttu-id="e5c74-113">Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.</span><span class="sxs-lookup"><span data-stu-id="e5c74-113">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="e5c74-114">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e5c74-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e5c74-115">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="e5c74-115">The path name is malformed.</span></span> <span data-ttu-id="e5c74-116">Por exemplo, ele contém caracteres que não são válidos ou é somente um espaço em branco (<xref:System.ArgumentException> classe).</span><span class="sxs-lookup"><span data-stu-id="e5c74-116">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="e5c74-117">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="e5c74-117">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="e5c74-118">É o nome do caminho `Nothing` (<xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="e5c74-118">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="e5c74-119">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="e5c74-119">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="e5c74-120">O caminho não é válido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="e5c74-120">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="e5c74-121">O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="e5c74-121">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e5c74-122">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e5c74-122">.NET Framework Security</span></span>  
 <span data-ttu-id="e5c74-123">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e5c74-123">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e5c74-124">Por exemplo, o arquivo `Form1.vb` não pode ser um arquivo de origem do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e5c74-124">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="e5c74-125">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5c74-125">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c74-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5c74-126">See Also</span></span>  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [<span data-ttu-id="e5c74-127">Como reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="e5c74-127">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
