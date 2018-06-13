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
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Como executar um bipe a partir de um Windows Form
Este exemplo executa um bipe em tempo de execução.  
  
## <a name="example"></a>Exemplo  
  
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
>  O som tocado no exemplo de código c# é determinado pelo <xref:System.Media.SystemSounds.Beep%2A> configuração do sistema de som. Para obter mais informações, consulte <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para c#, este exemplo requer uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [Como reproduzir um som do sistema de um Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [Como reproduzir um som de um Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
