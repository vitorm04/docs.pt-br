---
title: Como executar um som em loop em um Windows Form
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e61a15a7a249a90ce9eca035ebe6fd67275bb74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="6a1bf-102">Como executar um som em loop em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="6a1bf-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="6a1bf-103">O exemplo de código a seguir toca um som repetidamente.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="6a1bf-104">Quando o código de `stopPlayingButton_Click` manipulador de eventos é executado, qualquer som no momento será interrompido.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="6a1bf-105">Se nenhum som é reproduzido, nada acontecerá.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a1bf-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a1bf-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a1bf-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6a1bf-107">Compiling the Code</span></span>  
 <span data-ttu-id="6a1bf-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6a1bf-108">This example requires:</span></span>  
  
-   <span data-ttu-id="6a1bf-109">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="6a1bf-110">Se você substituir o nome de arquivo `"c:\Windows\Media\chimes.wav"` com um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="6a1bf-111">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6a1bf-112">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6a1bf-113">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6a1bf-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="6a1bf-114">Robust Programming</span></span>  
 <span data-ttu-id="6a1bf-115">Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="6a1bf-116">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="6a1bf-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6a1bf-117">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-117">The path name is malformed.</span></span> <span data-ttu-id="6a1bf-118">Por exemplo, ele contém caracteres que não são válidos ou é somente espaço em branco (<xref:System.ArgumentException> classe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="6a1bf-119">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="6a1bf-120">O nome do caminho é `Nothing` (<xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="6a1bf-121">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="6a1bf-122">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="6a1bf-123">O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="6a1bf-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6a1bf-124">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6a1bf-124">.NET Framework Security</span></span>  
 <span data-ttu-id="6a1bf-125">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="6a1bf-126">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="6a1bf-127">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a1bf-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1bf-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a1bf-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="6a1bf-129">Como reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="6a1bf-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="6a1bf-130">Visão geral da classe SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="6a1bf-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
