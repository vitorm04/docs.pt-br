---
title: 'Como: Recusar a atualização automática da caixa de diálogo do arquivo'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: a4be35617e8be1c6c83ac6f2d06e03b6cbb2977f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301094"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Como: Recusar a atualização automática da caixa de diálogo do arquivo
Quando o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes são usadas em um aplicativo, sua aparência e comportamento dependem da versão do Windows, o aplicativo está sendo executado. Quando um aplicativo que foi criado a [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ou anteriormente é exibida na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são exibidos automaticamente com o [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] aparência e comportamento. A partir o [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], você pode recusar a atualização automática para exibir o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> com um [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-estilizar a aparência e comportamento.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Para recusar a atualização automática da caixa de diálogo de arquivo  
  
1. Defina as <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade de <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> para `false` antes de exibir a caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FileDialog>
