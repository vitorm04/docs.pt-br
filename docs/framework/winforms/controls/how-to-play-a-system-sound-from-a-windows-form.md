---
title: Como executar um som de sistema a partir de um Windows Form
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
ms.openlocfilehash: 4dfda2b6d73e346d85690f66a3e92858381ae7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532393"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="aa5c9-102">Como executar um som de sistema a partir de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="aa5c9-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="aa5c9-103">O código a seguir exemplo desempenha o `Exclamation` som de sistema em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="aa5c9-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="aa5c9-104">Para obter mais informações sobre sons do sistema, consulte <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="aa5c9-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa5c9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa5c9-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa5c9-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="aa5c9-106">Compiling the Code</span></span>  
 <span data-ttu-id="aa5c9-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="aa5c9-107">This example requires:</span></span>  
  
-   <span data-ttu-id="aa5c9-108">Uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="aa5c9-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5c9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa5c9-109">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>  
 [<span data-ttu-id="aa5c9-110">Como executar um bipe de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="aa5c9-110">How to: Play a Beep from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 [<span data-ttu-id="aa5c9-111">Como reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="aa5c9-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
