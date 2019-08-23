---
title: 'Como: Reproduzir um aviso sonoro de um Windows Form'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: 1a72f88c05fb21c11864058ffbe81c1957525375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966516"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="1a457-102">Como: Reproduzir um aviso sonoro de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="1a457-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="1a457-103">Este exemplo reproduz um aviso sonoro no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1a457-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a457-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a457-104">Example</span></span>  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="1a457-105">O som tocado no exemplo C# de código é determinado pela configuração <xref:System.Media.SystemSounds.Beep%2A> de som do sistema.</span><span class="sxs-lookup"><span data-stu-id="1a457-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="1a457-106">Para obter mais informações, consulte <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="1a457-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a457-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1a457-107">Compiling the Code</span></span>  
 <span data-ttu-id="1a457-108">Para C#, este exemplo requer uma referência ao <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="1a457-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a457-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a457-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="1a457-110">Como: Reproduzir um som do sistema de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="1a457-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="1a457-111">Como: Tocar um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="1a457-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
