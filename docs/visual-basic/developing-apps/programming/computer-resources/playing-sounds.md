---
title: Executando sons (Visual Basic)
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
ms.openlocfilehash: decd845fde5bd4fad702cfe05fd63fcc180b63a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588452"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="bc719-102">Executando sons (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc719-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="bc719-103">O objeto `My.Computer.Audio` fornece métodos para reproduzir sons.</span><span class="sxs-lookup"><span data-stu-id="bc719-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="bc719-104">Executando sons</span><span class="sxs-lookup"><span data-stu-id="bc719-104">Playing Sounds</span></span>  
 <span data-ttu-id="bc719-105">A reprodução em segundo plano permite que o aplicativo execute outro código enquanto o som é reproduzido.</span><span class="sxs-lookup"><span data-stu-id="bc719-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="bc719-106">O método `My.Computer.Audio.Play` permite que o aplicativo para reproduza apenas um som de tela de fundo de cada vez. Quando o aplicativo reproduz um novo som de tela de fundo, ele para de reproduzir o som de tela de fundo anterior.</span><span class="sxs-lookup"><span data-stu-id="bc719-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="bc719-107">Você também pode reproduzir um som e aguardar sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="bc719-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="bc719-108">No exemplo a seguir, o método `My.Computer.Audio.Play` toca um som.</span><span class="sxs-lookup"><span data-stu-id="bc719-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="bc719-109">Quando `AudioPlayMode.WaitToComplete` for especificado, `My.Computer.Audio.Play` aguardará até que o som seja concluído antes de o código de chamada continuar.</span><span class="sxs-lookup"><span data-stu-id="bc719-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="bc719-110">Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som .wav no seu computador</span><span class="sxs-lookup"><span data-stu-id="bc719-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 <span data-ttu-id="bc719-111">No exemplo a seguir, o método `My.Computer.Audio.Play` toca um som.</span><span class="sxs-lookup"><span data-stu-id="bc719-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="bc719-112">Ao usar este exemplo, você deve garantir que os recursos do aplicativo incluem um arquivo de som .wav chamado Waterfall.</span><span class="sxs-lookup"><span data-stu-id="bc719-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="bc719-113">Reproduzindo sons em loop</span><span class="sxs-lookup"><span data-stu-id="bc719-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="bc719-114">No exemplo a seguir, o método `My.Computer.Audio.Play` toca o som especificado na tela de fundo quando `PlayMode.BackgroundLoop` é especificado.</span><span class="sxs-lookup"><span data-stu-id="bc719-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="bc719-115">Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som .wav no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bc719-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 <span data-ttu-id="bc719-116">No exemplo a seguir, o método `My.Computer.Audio.Play` toca o som especificado na tela de fundo quando `PlayMode.BackgroundLoop` é especificado.</span><span class="sxs-lookup"><span data-stu-id="bc719-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="bc719-117">Ao usar este exemplo, você deve garantir que os recursos do aplicativo incluem um arquivo de som .wav chamado Waterfall.</span><span class="sxs-lookup"><span data-stu-id="bc719-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 <span data-ttu-id="bc719-118">O exemplo de código anterior também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bc719-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="bc719-119">No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Sons**.</span><span class="sxs-lookup"><span data-stu-id="bc719-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="bc719-120">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="bc719-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="bc719-121">Em geral, quando um aplicativo reproduz um som em loop, ele deve interromper o som eventualmente.</span><span class="sxs-lookup"><span data-stu-id="bc719-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="bc719-122">Parando a reprodução de sons na tela de fundo</span><span class="sxs-lookup"><span data-stu-id="bc719-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="bc719-123">Use o método `My.Computer.Audio.Stop` para parar o som do aplicativo em loop ou na tela de fundo sendo reproduzido no momento.</span><span class="sxs-lookup"><span data-stu-id="bc719-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="bc719-124">Em geral, quando um aplicativo reproduz um som em loop, ele deve interromper o som em algum momento.</span><span class="sxs-lookup"><span data-stu-id="bc719-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="bc719-125">O exemplo a seguir interrompe um som que está sendo reproduzido na tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="bc719-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 <span data-ttu-id="bc719-126">O exemplo de código anterior também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bc719-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="bc719-127">No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Sons**.</span><span class="sxs-lookup"><span data-stu-id="bc719-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="bc719-128">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="bc719-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="bc719-129">Reproduzindo sons do sistema</span><span class="sxs-lookup"><span data-stu-id="bc719-129">Playing System Sounds</span></span>  
 <span data-ttu-id="bc719-130">Use o método `My.Computer.Audio.PlaySystemSound` para reproduzir o som do sistema especificado.</span><span class="sxs-lookup"><span data-stu-id="bc719-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="bc719-131">O método `My.Computer.Audio.PlaySystemSound` utiliza como parâmetro um dos membros compartilhados da classe <xref:System.Media.SystemSound>.</span><span class="sxs-lookup"><span data-stu-id="bc719-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="bc719-132">O som do sistema <xref:System.Media.SystemSounds.Asterisk%2A> geralmente indica erros.</span><span class="sxs-lookup"><span data-stu-id="bc719-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="bc719-133">O exemplo a seguir usa o método `My.Computer.Audio.PlaySystemSound` para reproduzir um som do sistema.</span><span class="sxs-lookup"><span data-stu-id="bc719-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bc719-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc719-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
