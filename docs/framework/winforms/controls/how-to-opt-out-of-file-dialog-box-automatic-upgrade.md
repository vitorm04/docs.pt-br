---
title: Como recusar a atualização automática da caixa de diálogo do arquivo
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: 154953680426f98a9506feb0b8f4de25c873b795
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959676"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Como recusar a atualização automática da caixa de diálogo do arquivo
Quando as classes <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são usadas em um aplicativo, sua aparência e comportamento dependem da versão do Windows em que o aplicativo está sendo executado. Quando um aplicativo que foi criado no .NET Framework 2,0 ou anterior é exibido no Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são exibidos automaticamente com a aparência e o comportamento do Windows Vista. A partir do .NET Framework 3,0, você pode recusar a atualização automática para exibir o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> com uma aparência e um comportamento no estilo do Windows XP.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Para recusar a atualização automática da caixa de diálogo de arquivo  
  
1. Defina a propriedade <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> de <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> como `false` antes de exibir a caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FileDialog>
