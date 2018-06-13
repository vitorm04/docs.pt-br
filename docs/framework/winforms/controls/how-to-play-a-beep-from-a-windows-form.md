---
title: Como executar um bipe a partir de um Windows Form
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
ms.openlocfilehash: 460309d853f2b3b423d14a820771e0230358e3c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531203"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="56e74-102">Como executar um bipe a partir de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="56e74-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="56e74-103">Este exemplo executa um bipe em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="56e74-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e74-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56e74-104">Example</span></span>  
  
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
>  <span data-ttu-id="56e74-105">O som tocado no exemplo de código c# é determinado pelo <xref:System.Media.SystemSounds.Beep%2A> configuração do sistema de som.</span><span class="sxs-lookup"><span data-stu-id="56e74-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="56e74-106">Para obter mais informações, consulte <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="56e74-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56e74-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="56e74-107">Compiling the Code</span></span>  
 <span data-ttu-id="56e74-108">Para c#, este exemplo requer uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="56e74-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e74-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56e74-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="56e74-110">Como reproduzir um som do sistema de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="56e74-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [<span data-ttu-id="56e74-111">Como reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="56e74-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
