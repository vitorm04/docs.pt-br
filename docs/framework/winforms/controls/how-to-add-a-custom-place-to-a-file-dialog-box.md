---
title: Como adicionar um local personalizado a uma caixa de diálogo Arquivo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 7a6ace385f7594a467785fbc677517c8a6e1ab53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="3c079-102">Como adicionar um local personalizado a uma caixa de diálogo Arquivo</span><span class="sxs-lookup"><span data-stu-id="3c079-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="3c079-103">O padrão abrir e salvar caixas de diálogo em [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] tem uma área no lado esquerdo da caixa de diálogo intitulada **Links Favoritos**.</span><span class="sxs-lookup"><span data-stu-id="3c079-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="3c079-104">Essa área é denominada locais personalizados.</span><span class="sxs-lookup"><span data-stu-id="3c079-104">This area is called custom places.</span></span> <span data-ttu-id="3c079-105">O <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes permitem que você adicione pastas para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="3c079-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c079-106">Para que um local personalizado para aparecer no <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, o <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade deve ser definida como `true` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="3c079-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="3c079-107">Para adicionar um local personalizado para uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="3c079-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="3c079-108">Adicione um caminho, um GUID de pasta conhecidas, ou um <xref:System.Windows.Forms.FileDialogCustomPlace> o objeto para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3c079-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="3c079-109">O exemplo de código a seguir mostra como adicionar um caminho:</span><span class="sxs-lookup"><span data-stu-id="3c079-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3c079-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c079-110">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3c079-111">GUIDs de pasta conhecida para locais personalizados de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="3c079-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
