---
title: Como executar um som em loop em um Windows Form
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a88bf4b9dc84af8c6e81167c989943754f64b7d8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="14275-102">Como executar um som em loop em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="14275-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="14275-103">O exemplo de código a seguir toca um som repetidamente.</span><span class="sxs-lookup"><span data-stu-id="14275-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="14275-104">Quando o código de `stopPlayingButton_Click` manipulador de eventos é executado, qualquer som no momento será interrompido.</span><span class="sxs-lookup"><span data-stu-id="14275-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="14275-105">Se nenhum som é reproduzido, nada acontecerá.</span><span class="sxs-lookup"><span data-stu-id="14275-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14275-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14275-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14275-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="14275-107">Compiling the Code</span></span>  
 <span data-ttu-id="14275-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="14275-108">This example requires:</span></span>  
  
-   <span data-ttu-id="14275-109">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="14275-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="14275-110">Se você substituir o nome de arquivo `"c:\Windows\Media\chimes.wav"` com um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="14275-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="14275-111">Para obter informações sobre como criar este exemplo da linha de comando para o visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="14275-111">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="14275-112">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="14275-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="14275-113">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="14275-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="14275-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="14275-114">Robust Programming</span></span>  
 <span data-ttu-id="14275-115">Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.</span><span class="sxs-lookup"><span data-stu-id="14275-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="14275-116">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="14275-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="14275-117">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="14275-117">The path name is malformed.</span></span> <span data-ttu-id="14275-118">Por exemplo, ele contém caracteres que não são válidos ou é somente espaço em branco (<xref:System.ArgumentException> classe).</span><span class="sxs-lookup"><span data-stu-id="14275-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="14275-119">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="14275-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="14275-120">O nome do caminho é `Nothing` (<xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="14275-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="14275-121">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="14275-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="14275-122">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="14275-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="14275-123">O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="14275-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="14275-124">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14275-124">.NET Framework Security</span></span>  
 <span data-ttu-id="14275-125">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="14275-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="14275-126">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="14275-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="14275-127">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14275-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14275-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14275-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="14275-129">Como reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="14275-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="14275-130">Visão geral da classe SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="14275-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
