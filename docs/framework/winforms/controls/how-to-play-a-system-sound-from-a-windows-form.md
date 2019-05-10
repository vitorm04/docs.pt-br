---
title: 'Como: Reproduzir um som do sistema de um Windows Form'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
ms.openlocfilehash: 765021875767a754e62e3ec11e56487e4de91e93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602772"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="044dc-102">Como: Reproduzir um som do sistema de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="044dc-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="044dc-103">O código a seguir exemplo reproduz o `Exclamation` som do sistema em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="044dc-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="044dc-104">Para obter mais informações sobre os sons do sistema, consulte <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="044dc-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="044dc-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="044dc-105">Example</span></span>  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="044dc-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="044dc-106">Compiling the Code</span></span>  
 <span data-ttu-id="044dc-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="044dc-107">This example requires:</span></span>  
  
- <span data-ttu-id="044dc-108">Uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="044dc-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044dc-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="044dc-109">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [<span data-ttu-id="044dc-110">Como: Executar um bipe de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="044dc-110">How to: Play a Beep from a Windows Form</span></span>](how-to-play-a-beep-from-a-windows-form.md)
- [<span data-ttu-id="044dc-111">Como: Reproduzir um som de um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="044dc-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
