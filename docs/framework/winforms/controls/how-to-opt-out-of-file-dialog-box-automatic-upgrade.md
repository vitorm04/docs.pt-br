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
ms.openlocfilehash: 380f8abe502c37e57207c43696158c1e3bdc7697
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Como recusar a atualização automática da caixa de diálogo do arquivo
Quando o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes são usadas em um aplicativo, sua aparência e comportamento dependem da versão do Windows que o aplicativo está em execução no. Quando um aplicativo que foi criado o [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ou anterior é exibido na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são exibidas automaticamente com o [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] aparência e comportamento. A partir de [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], poderá recusar a atualização automática para exibir o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> com um [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-aparência e comportamento de estilo.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Para recusar a atualização automática da caixa de diálogo de arquivo  
  
1.  Definir o <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> para `false` antes de exibir a caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FileDialog>
