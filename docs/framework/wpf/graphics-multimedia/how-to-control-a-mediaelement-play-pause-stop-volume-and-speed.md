---
title: 'Como: Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930156"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="cd5bb-102">Como: Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)</span><span class="sxs-lookup"><span data-stu-id="cd5bb-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="cd5bb-103">O exemplo a seguir mostra como controlar a reprodução de mídia usando <xref:System.Windows.Controls.MediaElement>um.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="cd5bb-104">O exemplo cria um player de mídia simples que permite reproduzir, pausar, parar, retroceder e avançar a mídia, bem como ajustar a taxa de velocidade e o volume.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd5bb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd5bb-105">Example</span></span>  
 <span data-ttu-id="cd5bb-106">O código a seguir cria a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd5bb-107">A <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriedade de <xref:System.Windows.Controls.MediaElement> deve ser definida como `Manual` para poder parar, pausar e reproduzir a mídia interativamente.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="cd5bb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd5bb-108">Example</span></span>  
 <span data-ttu-id="cd5bb-109">O código a seguir implementa a funcionalidade dos controles de interface do usuário de exemplo.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="cd5bb-110">Os <xref:System.Windows.Controls.MediaElement.Play%2A>métodos <xref:System.Windows.Controls.MediaElement.Pause%2A>, e<xref:System.Windows.Controls.MediaElement.Stop%2A> são usados para reproduzir, pausar e parar a mídia respectivamente.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="cd5bb-111">Alterar a <xref:System.Windows.Controls.MediaElement.Position%2A> propriedade <xref:System.Windows.Controls.MediaElement> do permite que você pule na mídia.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="cd5bb-112">Por fim, <xref:System.Windows.Controls.MediaElement.Volume%2A> as <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> Propriedades e são usadas para ajustar o volume e a velocidade de reprodução da mídia.</span><span class="sxs-lookup"><span data-stu-id="cd5bb-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="cd5bb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd5bb-113">See also</span></span>

- [<span data-ttu-id="cd5bb-114">Controlar um MediaElement usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="cd5bb-114">Control a MediaElement by Using a Storyboard</span></span>](how-to-control-a-mediaelement-by-using-a-storyboard.md)
