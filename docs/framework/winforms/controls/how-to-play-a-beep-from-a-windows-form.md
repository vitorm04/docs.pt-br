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
ms.openlocfilehash: 0aa01f600873dd8853e1c33d5443448835e11455
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146218"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Como: Reproduzir um aviso sonoro de um Windows Form
Este exemplo reproduz um aviso sonoro em tempo de execução.  
  
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
>  O som tocado C# exemplo de código é determinado pelo <xref:System.Media.SystemSounds.Beep%2A> configuração do sistema de som. Para obter mais informações, consulte <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para C#, este exemplo requer uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Como: Reproduzir um som do sistema de um formulário do Windows](how-to-play-a-system-sound-from-a-windows-form.md)
- [Como: Reproduzir um som de um formulário do Windows](how-to-play-a-sound-from-a-windows-form.md)
