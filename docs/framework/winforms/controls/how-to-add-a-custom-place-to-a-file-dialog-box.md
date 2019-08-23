---
title: 'Como: Adicionar um local personalizado a uma caixa de diálogo Arquivo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916345"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="8dcf5-102">Como: Adicionar um local personalizado a uma caixa de diálogo Arquivo</span><span class="sxs-lookup"><span data-stu-id="8dcf5-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="8dcf5-103">As caixas de diálogo padrão abrir e salvar [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] em têm uma área no lado esquerdo da caixa de diálogo chamada **links favoritos**.</span><span class="sxs-lookup"><span data-stu-id="8dcf5-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="8dcf5-104">Essa área é chamada de locais personalizados.</span><span class="sxs-lookup"><span data-stu-id="8dcf5-104">This area is called custom places.</span></span> <span data-ttu-id="8dcf5-105">As <xref:System.Windows.Forms.OpenFileDialog> classes <xref:System.Windows.Forms.SaveFileDialog> e permitem que você adicione pastas à <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="8dcf5-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8dcf5-106">Para que um local personalizado apareça <xref:System.Windows.Forms.OpenFileDialog> no ou <xref:System.Windows.Forms.SaveFileDialog>, a <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade deve ser definida como `true` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="8dcf5-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="8dcf5-107">Para adicionar um local personalizado a uma caixa de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="8dcf5-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="8dcf5-108">Adicione um caminho, um GUID de pasta conhecida ou um <xref:System.Windows.Forms.FileDialogCustomPlace> objeto <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> à coleção da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="8dcf5-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="8dcf5-109">O exemplo de código a seguir mostra como adicionar um caminho:</span><span class="sxs-lookup"><span data-stu-id="8dcf5-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8dcf5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dcf5-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8dcf5-111">GUIDs de pasta conhecida para locais personalizados de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="8dcf5-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
