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
ms.openlocfilehash: 129ebed6d0a2b075020e635c8463536f97629d2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624114"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="4abfa-102">Como: Adicionar um local personalizado a uma caixa de diálogo Arquivo</span><span class="sxs-lookup"><span data-stu-id="4abfa-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="4abfa-103">O padrão abrir e salvar as caixas de diálogo no [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] têm uma área no lado esquerdo da caixa de diálogo intitulada **Links Favoritos**.</span><span class="sxs-lookup"><span data-stu-id="4abfa-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="4abfa-104">Essa área é chamada de locais personalizados.</span><span class="sxs-lookup"><span data-stu-id="4abfa-104">This area is called custom places.</span></span> <span data-ttu-id="4abfa-105">O <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes permitem que você adicione pastas para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="4abfa-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4abfa-106">Em ordem para um local personalizado apareça na <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, o <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade deve ser definida como `true` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="4abfa-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="4abfa-107">Para adicionar um local personalizado a uma caixa de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="4abfa-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="4abfa-108">Adicionar um caminho, um GUID de pasta conhecida, ou um <xref:System.Windows.Forms.FileDialogCustomPlace> do objeto para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4abfa-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="4abfa-109">O exemplo de código a seguir mostra como adicionar um caminho:</span><span class="sxs-lookup"><span data-stu-id="4abfa-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4abfa-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4abfa-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4abfa-111">GUIDs de pasta conhecida para locais personalizados de diálogo de arquivo</span><span class="sxs-lookup"><span data-stu-id="4abfa-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
