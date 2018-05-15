---
title: Como executar um som inserido em um recurso a partir de um Windows Form
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
ms.openlocfilehash: c9dc8499e2d12ed17f9b409a805148d08da894fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="6c4bb-102">Como executar um som inserido em um recurso a partir de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="6c4bb-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="6c4bb-103">Você pode usar o <xref:System.Media.SoundPlayer> classe tocar um som de um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="6c4bb-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c4bb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c4bb-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c4bb-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6c4bb-105">Compiling the Code</span></span>  
 <span data-ttu-id="6c4bb-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6c4bb-106">This example requires:</span></span>  
  
 <span data-ttu-id="6c4bb-107">Importando o <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="6c4bb-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="6c4bb-108">Incluindo o arquivo de som como um recurso inserido em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6c4bb-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="6c4bb-109">Substituindo "\<AssemblyName >" com o nome do assembly no qual é incorporado no arquivo de som.</span><span class="sxs-lookup"><span data-stu-id="6c4bb-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="6c4bb-110">Não inclua o sufixo ". dll".</span><span class="sxs-lookup"><span data-stu-id="6c4bb-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4bb-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c4bb-111">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="6c4bb-112">Como reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="6c4bb-112">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="6c4bb-113">Como executar um loop de um som tocado em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="6c4bb-113">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
