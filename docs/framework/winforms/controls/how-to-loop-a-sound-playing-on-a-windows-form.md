---
title: 'Como: Loop de um som tocado em um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: 43fcc472960cc3f2432d3872160d9ace4c617836
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719267"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="34d25-102">Como: Loop de um som tocado em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="34d25-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="34d25-103">O exemplo de código a seguir toca um som repetidamente.</span><span class="sxs-lookup"><span data-stu-id="34d25-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="34d25-104">Quando o código a `stopPlayingButton_Click` manipulador de eventos é executado, nenhum som é interrompido em reprodução no momento.</span><span class="sxs-lookup"><span data-stu-id="34d25-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="34d25-105">Se nenhum som estiver em execução, nada acontece.</span><span class="sxs-lookup"><span data-stu-id="34d25-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d25-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34d25-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34d25-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="34d25-107">Compiling the Code</span></span>  
 <span data-ttu-id="34d25-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="34d25-108">This example requires:</span></span>  
  
-   <span data-ttu-id="34d25-109">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="34d25-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="34d25-110">Se você substituir o nome de arquivo `"c:\Windows\Media\chimes.wav"` com um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="34d25-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="34d25-111">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="34d25-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="34d25-112">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="34d25-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="34d25-113">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="34d25-113">Robust Programming</span></span>  
 <span data-ttu-id="34d25-114">Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.</span><span class="sxs-lookup"><span data-stu-id="34d25-114">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="34d25-115">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="34d25-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="34d25-116">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="34d25-116">The path name is malformed.</span></span> <span data-ttu-id="34d25-117">Por exemplo, ele contém caracteres que não são válidos ou é somente espaço em branco (<xref:System.ArgumentException> classe).</span><span class="sxs-lookup"><span data-stu-id="34d25-117">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="34d25-118">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="34d25-118">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="34d25-119">É o nome do caminho `Nothing` (<xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="34d25-119">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="34d25-120">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="34d25-120">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="34d25-121">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="34d25-121">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="34d25-122">O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="34d25-122">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="34d25-123">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="34d25-123">.NET Framework Security</span></span>  
 <span data-ttu-id="34d25-124">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="34d25-124">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="34d25-125">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34d25-125">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="34d25-126">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34d25-126">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d25-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34d25-127">See also</span></span>
- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="34d25-128">Como: Reproduzir um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="34d25-128">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="34d25-129">Visão geral da classe SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="34d25-129">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
