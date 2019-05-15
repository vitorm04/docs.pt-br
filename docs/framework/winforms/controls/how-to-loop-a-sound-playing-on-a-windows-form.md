---
title: 'Como: Fazer Loop de um Som Tocado em um Formulário do Windows'
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
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592364"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="e4c32-102">Como: Fazer Loop de um Som Tocado em um Formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="e4c32-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="e4c32-103">O exemplo de código a seguir toca um som repetidamente.</span><span class="sxs-lookup"><span data-stu-id="e4c32-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="e4c32-104">Quando o código a `stopPlayingButton_Click` manipulador de eventos é executado, nenhum som é interrompido em reprodução no momento.</span><span class="sxs-lookup"><span data-stu-id="e4c32-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="e4c32-105">Se nenhum som estiver em execução, nada acontece.</span><span class="sxs-lookup"><span data-stu-id="e4c32-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c32-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c32-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4c32-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e4c32-107">Compiling the Code</span></span>  
 <span data-ttu-id="e4c32-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e4c32-108">This example requires:</span></span>  
  
- <span data-ttu-id="e4c32-109">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e4c32-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="e4c32-110">Se você substituir o nome de arquivo `"c:\Windows\Media\chimes.wav"` com um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="e4c32-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e4c32-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e4c32-111">Robust Programming</span></span>  
 <span data-ttu-id="e4c32-112">Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.</span><span class="sxs-lookup"><span data-stu-id="e4c32-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="e4c32-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e4c32-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e4c32-114">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="e4c32-114">The path name is malformed.</span></span> <span data-ttu-id="e4c32-115">Por exemplo, ele contém caracteres que não são válidos ou é somente espaço em branco (<xref:System.ArgumentException> classe).</span><span class="sxs-lookup"><span data-stu-id="e4c32-115">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="e4c32-116">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="e4c32-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="e4c32-117">É o nome do caminho `Nothing` (<xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="e4c32-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="e4c32-118">O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="e4c32-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="e4c32-119">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="e4c32-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="e4c32-120">O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="e4c32-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e4c32-121">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e4c32-121">.NET Framework Security</span></span>  
 <span data-ttu-id="e4c32-122">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4c32-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e4c32-123">Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e4c32-123">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="e4c32-124">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4c32-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c32-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4c32-125">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="e4c32-126">Como: Reproduzir um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="e4c32-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="e4c32-127">Visão geral da classe SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="e4c32-127">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
