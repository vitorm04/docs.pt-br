---
title: 'Como: Controlar um MediaElement (executar, pausar, parar, volume e velocidade)'
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
ms.openlocfilehash: e9939c2d3d740bfe9296c23e47ef8ea09d837e01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498915"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="13aeb-102">Como: Controlar um MediaElement (executar, pausar, parar, volume e velocidade)</span><span class="sxs-lookup"><span data-stu-id="13aeb-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="13aeb-103">O exemplo a seguir mostra como controlar a reprodução de mídia usando um <xref:System.Windows.Controls.MediaElement>.</span><span class="sxs-lookup"><span data-stu-id="13aeb-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="13aeb-104">O exemplo cria um player de mídia simples que permite reproduzir, pausar, parar, retroceder e avançar a mídia, bem como ajustar a taxa de velocidade e o volume.</span><span class="sxs-lookup"><span data-stu-id="13aeb-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13aeb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13aeb-105">Example</span></span>  
 <span data-ttu-id="13aeb-106">O código a seguir cria a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="13aeb-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13aeb-107">O <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriedade de <xref:System.Windows.Controls.MediaElement> deve ser definida como `Manual` para poder interativamente parar, pausar e reproduzir a mídia.</span><span class="sxs-lookup"><span data-stu-id="13aeb-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="13aeb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13aeb-108">Example</span></span>  
 <span data-ttu-id="13aeb-109">O código a seguir implementa a funcionalidade dos controles de interface do usuário de exemplo.</span><span class="sxs-lookup"><span data-stu-id="13aeb-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="13aeb-110">O <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, e <xref:System.Windows.Controls.MediaElement.Stop%2A> métodos são usados para, respectivamente, reproduzir, pausar e parar a mídia.</span><span class="sxs-lookup"><span data-stu-id="13aeb-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="13aeb-111">Alterando a <xref:System.Windows.Controls.MediaElement.Position%2A> propriedade do <xref:System.Windows.Controls.MediaElement> permite que você se desloque pela mídia.</span><span class="sxs-lookup"><span data-stu-id="13aeb-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="13aeb-112">Por fim, o <xref:System.Windows.Controls.MediaElement.Volume%2A> e <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propriedades são usadas para ajustar a velocidade de reprodução e o volume da mídia.</span><span class="sxs-lookup"><span data-stu-id="13aeb-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="13aeb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13aeb-113">See also</span></span>
- [<span data-ttu-id="13aeb-114">Controlar um MediaElement usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="13aeb-114">Control a MediaElement by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
