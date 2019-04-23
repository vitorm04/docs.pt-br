---
title: 'Como: Reproduzir um som inserido em um recurso de um Windows Form'
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
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078571"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="b9b2b-102">Como: Reproduzir um som inserido em um recurso de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="b9b2b-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="b9b2b-103">Você pode usar o <xref:System.Media.SoundPlayer> classe para tocar um som de um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="b9b2b-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9b2b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9b2b-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9b2b-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b9b2b-105">Compiling the Code</span></span>  
 <span data-ttu-id="b9b2b-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b9b2b-106">This example requires:</span></span>  
  
 <span data-ttu-id="b9b2b-107">Importando o <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="b9b2b-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="b9b2b-108">Incluindo o arquivo de som como um recurso inserido em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b9b2b-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="b9b2b-109">Substituindo "\<AssemblyName >" com o nome do assembly no qual o arquivo de som é inserido.</span><span class="sxs-lookup"><span data-stu-id="b9b2b-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="b9b2b-110">Não inclua o sufixo ". dll".</span><span class="sxs-lookup"><span data-stu-id="b9b2b-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b2b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9b2b-111">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="b9b2b-112">Como: Reproduzir um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="b9b2b-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="b9b2b-113">Como: Loop de um som tocado em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="b9b2b-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
