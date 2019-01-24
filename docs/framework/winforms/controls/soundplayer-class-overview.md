---
title: Visão geral da classe SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 041e7d0170bc98797278e209fd86cff0f82db9fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690677"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="009a1-102">Visão geral da classe SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="009a1-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="009a1-103">A classe <xref:System.Media.SoundPlayer> permite que você inclua facilmente sons em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="009a1-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="009a1-104">O <xref:System.Media.SoundPlayer> classe pode reproduzir arquivos de som no formato. wav, a partir de um recurso ou de locais UNC ou HTTP.</span><span class="sxs-lookup"><span data-stu-id="009a1-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="009a1-105">Além disso, o <xref:System.Media.SoundPlayer> classe permite que você carregue ou reproduza sons de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="009a1-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="009a1-106">Você também pode usar o <xref:System.Media.SystemSounds> classe para reproduzir sons comuns do sistema, incluindo um aviso sonoro.</span><span class="sxs-lookup"><span data-stu-id="009a1-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="009a1-107">Propriedades, métodos e eventos normalmente usados</span><span class="sxs-lookup"><span data-stu-id="009a1-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="009a1-108">Nome</span><span class="sxs-lookup"><span data-stu-id="009a1-108">Name</span></span>|<span data-ttu-id="009a1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="009a1-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="009a1-110">Propriedade <xref:System.Media.SoundPlayer.SoundLocation%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="009a1-111">O caminho do arquivo ou o endereço Web do som.</span><span class="sxs-lookup"><span data-stu-id="009a1-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="009a1-112">Os valores aceitáveis podem ser HTTP ou UNC.</span><span class="sxs-lookup"><span data-stu-id="009a1-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="009a1-113">Propriedade <xref:System.Media.SoundPlayer.LoadTimeout%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="009a1-114">O número de milissegundos que o programa irá esperar para carregar um som antes que ele gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="009a1-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="009a1-115">O padrão é 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="009a1-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="009a1-116">Propriedade <xref:System.Media.SoundPlayer.IsLoadCompleted%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="009a1-117">Um valor booliano que indica se o som terminou de ser carregado.</span><span class="sxs-lookup"><span data-stu-id="009a1-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="009a1-118">Método <xref:System.Media.SoundPlayer.Load%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="009a1-119">Carrega um som de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="009a1-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="009a1-120">Método <xref:System.Media.SoundPlayer.LoadAsync%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="009a1-121">Começa a carregar um som de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="009a1-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="009a1-122">Quando o carregamento for concluído, ele gera o <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> eventos.</span><span class="sxs-lookup"><span data-stu-id="009a1-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="009a1-123">Método <xref:System.Media.SoundPlayer.Play%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="009a1-124">Reproduz o som especificado na <xref:System.Media.SoundPlayer.SoundLocation%2A> ou <xref:System.Media.SoundPlayer.Stream%2A> propriedade em um novo thread.</span><span class="sxs-lookup"><span data-stu-id="009a1-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="009a1-125">Método <xref:System.Media.SoundPlayer.PlaySync%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="009a1-126">Reproduz o som especificado na <xref:System.Media.SoundPlayer.SoundLocation%2A> ou <xref:System.Media.SoundPlayer.Stream%2A> propriedade no thread atual.</span><span class="sxs-lookup"><span data-stu-id="009a1-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="009a1-127">Método <xref:System.Media.SoundPlayer.Stop%2A></span><span class="sxs-lookup"><span data-stu-id="009a1-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="009a1-128">Interrompe qualquer som que está em reprodução no momento.</span><span class="sxs-lookup"><span data-stu-id="009a1-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="009a1-129">Evento <xref:System.Media.SoundPlayer.LoadCompleted></span><span class="sxs-lookup"><span data-stu-id="009a1-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="009a1-130">Gerado depois que o carregamento de um som é tentado.</span><span class="sxs-lookup"><span data-stu-id="009a1-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="009a1-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="009a1-131">See also</span></span>
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
