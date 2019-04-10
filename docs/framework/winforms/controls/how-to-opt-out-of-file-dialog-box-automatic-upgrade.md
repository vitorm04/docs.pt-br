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
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="b257c-102">Como: Recusar a atualização automática da caixa de diálogo do arquivo</span><span class="sxs-lookup"><span data-stu-id="b257c-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="b257c-103">Quando o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes são usadas em um aplicativo, sua aparência e comportamento dependem da versão do Windows, o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b257c-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="b257c-104">Quando um aplicativo que foi criado a [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ou anteriormente é exibida na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são exibidos automaticamente com o [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="b257c-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="b257c-105">A partir o [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], você pode recusar a atualização automática para exibir o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> com um [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-estilizar a aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="b257c-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="b257c-106">Para recusar a atualização automática da caixa de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="b257c-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="b257c-107">Defina as <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade de <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> para `false` antes de exibir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="b257c-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b257c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b257c-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
