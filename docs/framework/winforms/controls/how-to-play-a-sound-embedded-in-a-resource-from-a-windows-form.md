---
title: 'Como: Reproduzir um som inserido em um recurso de um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: f52cac4ca16adee232fae6fe2c1540bf5d3cb8cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708178"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="14ede-102">Como: Reproduzir um som inserido em um recurso de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="14ede-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="14ede-103">Você pode usar o <xref:System.Media.SoundPlayer> classe para tocar um som de um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="14ede-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14ede-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14ede-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14ede-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="14ede-105">Compiling the Code</span></span>  
 <span data-ttu-id="14ede-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="14ede-106">This example requires:</span></span>  
  
 <span data-ttu-id="14ede-107">Importando o <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="14ede-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="14ede-108">Incluindo o arquivo de som como um recurso inserido em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="14ede-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="14ede-109">Substituindo "\<AssemblyName >" com o nome do assembly no qual o arquivo de som é inserido.</span><span class="sxs-lookup"><span data-stu-id="14ede-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="14ede-110">Não inclua o sufixo ". dll".</span><span class="sxs-lookup"><span data-stu-id="14ede-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ede-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14ede-111">See also</span></span>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="14ede-112">Como: Reproduzir um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="14ede-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="14ede-113">Como: Loop de um som tocado em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="14ede-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
