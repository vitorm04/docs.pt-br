---
title: Executando sons
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345515"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="ab009-102">Executando sons (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab009-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="ab009-103">O objeto `My.Computer.Audio` fornece métodos para reproduzir sons.</span><span class="sxs-lookup"><span data-stu-id="ab009-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="ab009-104">Executando sons</span><span class="sxs-lookup"><span data-stu-id="ab009-104">Playing Sounds</span></span>  

 <span data-ttu-id="ab009-105">A reprodução em segundo plano permite que o aplicativo execute outro código enquanto o som é reproduzido.</span><span class="sxs-lookup"><span data-stu-id="ab009-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="ab009-106">O método `My.Computer.Audio.Play` permite que o aplicativo para reproduza apenas um som de tela de fundo de cada vez. Quando o aplicativo reproduz um novo som de tela de fundo, ele para de reproduzir o som de tela de fundo anterior.</span><span class="sxs-lookup"><span data-stu-id="ab009-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="ab009-107">Você também pode reproduzir um som e aguardar sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="ab009-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="ab009-108">No exemplo a seguir, o método `My.Computer.Audio.Play` toca um som.</span><span class="sxs-lookup"><span data-stu-id="ab009-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="ab009-109">Quando `AudioPlayMode.WaitToComplete` for especificado, `My.Computer.Audio.Play` aguardará até que o som seja concluído antes de o código de chamada continuar.</span><span class="sxs-lookup"><span data-stu-id="ab009-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="ab009-110">Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som .wav no seu computador</span><span class="sxs-lookup"><span data-stu-id="ab009-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="ab009-111">No exemplo a seguir, o método `My.Computer.Audio.Play` toca um som.</span><span class="sxs-lookup"><span data-stu-id="ab009-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="ab009-112">Ao usar este exemplo, você deve garantir que os recursos do aplicativo incluem um arquivo de som .wav chamado Waterfall.</span><span class="sxs-lookup"><span data-stu-id="ab009-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="ab009-113">Reproduzindo sons em loop</span><span class="sxs-lookup"><span data-stu-id="ab009-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="ab009-114">No exemplo a seguir, o método `My.Computer.Audio.Play` toca o som especificado na tela de fundo quando `PlayMode.BackgroundLoop` é especificado.</span><span class="sxs-lookup"><span data-stu-id="ab009-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="ab009-115">Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som .wav no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ab009-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="ab009-116">No exemplo a seguir, o método `My.Computer.Audio.Play` toca o som especificado na tela de fundo quando `PlayMode.BackgroundLoop` é especificado.</span><span class="sxs-lookup"><span data-stu-id="ab009-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="ab009-117">Ao usar este exemplo, você deve garantir que os recursos do aplicativo incluem um arquivo de som .wav chamado Waterfall.</span><span class="sxs-lookup"><span data-stu-id="ab009-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="ab009-118">O exemplo de código anterior também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ab009-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ab009-119">No seletor de snippet de código, ele está localizado em **Aplicativos do Windows Forms &gt; Sons**.</span><span class="sxs-lookup"><span data-stu-id="ab009-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="ab009-120">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ab009-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="ab009-121">Em geral, quando um aplicativo reproduz um som em loop, ele deve interromper o som eventualmente.</span><span class="sxs-lookup"><span data-stu-id="ab009-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="ab009-122">Parando a reprodução de sons na tela de fundo</span><span class="sxs-lookup"><span data-stu-id="ab009-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="ab009-123">Use o método `My.Computer.Audio.Stop` para parar o som do aplicativo em loop ou na tela de fundo sendo reproduzido no momento.</span><span class="sxs-lookup"><span data-stu-id="ab009-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="ab009-124">Em geral, quando um aplicativo reproduz um som em loop, ele deve interromper o som em algum momento.</span><span class="sxs-lookup"><span data-stu-id="ab009-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="ab009-125">O exemplo a seguir interrompe um som que está sendo reproduzido na tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="ab009-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="ab009-126">O exemplo de código anterior também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ab009-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ab009-127">No seletor de snippet de código, ele está localizado em **Aplicativos do Windows Forms &gt; Sons**.</span><span class="sxs-lookup"><span data-stu-id="ab009-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="ab009-128">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ab009-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="ab009-129">Reproduzindo sons do sistema</span><span class="sxs-lookup"><span data-stu-id="ab009-129">Playing System Sounds</span></span>  

 <span data-ttu-id="ab009-130">Use o método `My.Computer.Audio.PlaySystemSound` para reproduzir o som do sistema especificado.</span><span class="sxs-lookup"><span data-stu-id="ab009-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="ab009-131">O método `My.Computer.Audio.PlaySystemSound` utiliza como parâmetro um dos membros compartilhados da classe <xref:System.Media.SystemSound>.</span><span class="sxs-lookup"><span data-stu-id="ab009-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="ab009-132">O som do sistema <xref:System.Media.SystemSounds.Asterisk%2A> geralmente indica erros.</span><span class="sxs-lookup"><span data-stu-id="ab009-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="ab009-133">O exemplo a seguir usa o método `My.Computer.Audio.PlaySystemSound` para reproduzir um som do sistema.</span><span class="sxs-lookup"><span data-stu-id="ab009-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="ab009-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab009-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
