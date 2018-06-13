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
ms.locfileid: "33532481"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="df24b-102">Como recusar a atualização automática da caixa de diálogo do arquivo</span><span class="sxs-lookup"><span data-stu-id="df24b-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="df24b-103">Quando o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes são usadas em um aplicativo, sua aparência e comportamento dependem da versão do Windows que o aplicativo está em execução no.</span><span class="sxs-lookup"><span data-stu-id="df24b-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="df24b-104">Quando um aplicativo que foi criado o [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ou anterior é exibido na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são exibidas automaticamente com o [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="df24b-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="df24b-105">A partir de [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], poderá recusar a atualização automática para exibir o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> com um [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-aparência e comportamento de estilo.</span><span class="sxs-lookup"><span data-stu-id="df24b-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="df24b-106">Para recusar a atualização automática da caixa de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="df24b-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1.  <span data-ttu-id="df24b-107">Definir o <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> para `false` antes de exibir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="df24b-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df24b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df24b-108">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>
