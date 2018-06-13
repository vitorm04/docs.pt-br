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
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>Como executar um som de sistema a partir de um Windows Form
O código a seguir exemplo desempenha o `Exclamation` som de sistema em tempo de execução. Para obter mais informações sobre sons do sistema, consulte <xref:System.Media.SystemSounds>.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System.Media?displayProperty=nameWithType> namespace.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>  
 [Como executar um bipe de um Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 [Como reproduzir um som de um Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
