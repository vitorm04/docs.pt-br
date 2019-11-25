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
ms.openlocfilehash: 7172e484451cf932413920910ec9124b3388bd76
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976986"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="bc12a-102">Como adicionar um local personalizado a uma caixa de diálogo Arquivo</span><span class="sxs-lookup"><span data-stu-id="bc12a-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="bc12a-103">As caixas de diálogo padrão abrir e salvar no Windows Vista têm uma área no lado esquerdo da caixa de diálogo chamada **links favoritos**.</span><span class="sxs-lookup"><span data-stu-id="bc12a-103">The default open and save dialog boxes on Windows Vista have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="bc12a-104">Essa área é chamada de locais personalizados.</span><span class="sxs-lookup"><span data-stu-id="bc12a-104">This area is called custom places.</span></span> <span data-ttu-id="bc12a-105">As classes <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> permitem que você adicione pastas à coleção de <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc12a-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc12a-106">Para que um local personalizado apareça no <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, a propriedade <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> deve ser definida como `true` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="bc12a-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="bc12a-107">Para adicionar um local personalizado a uma caixa de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="bc12a-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="bc12a-108">Adicione um caminho, um GUID de pasta conhecido ou um objeto <xref:System.Windows.Forms.FileDialogCustomPlace> à coleção <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bc12a-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="bc12a-109">O exemplo de código a seguir mostra como adicionar um caminho:</span><span class="sxs-lookup"><span data-stu-id="bc12a-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bc12a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc12a-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc12a-111">GUIDs de pasta conhecida para locais personalizados de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="bc12a-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
