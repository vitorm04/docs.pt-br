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
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="5b995-102">Como recusar a atualização automática da caixa de diálogo do arquivo</span><span class="sxs-lookup"><span data-stu-id="5b995-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="5b995-103">Quando as classes <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são usadas em um aplicativo, sua aparência e comportamento dependem da versão do Windows em que o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="5b995-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="5b995-104">Quando um aplicativo que foi criado no .NET Framework 2,0 ou anterior é exibido no Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> são exibidos automaticamente com a aparência e o comportamento do Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="5b995-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the Windows Vista appearance and behavior.</span></span> <span data-ttu-id="5b995-105">A partir do .NET Framework 3,0, você pode recusar a atualização automática para exibir o <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> com uma aparência e um comportamento no estilo do Windows XP.</span><span class="sxs-lookup"><span data-stu-id="5b995-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a Windows XP-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="5b995-106">Para recusar a atualização automática da caixa de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="5b995-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="5b995-107">Defina a propriedade <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> de <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> como `false` antes de exibir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="5b995-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b995-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b995-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
