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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Como: Adicionar um local personalizado a uma caixa de diálogo Arquivo
As caixas de diálogo padrão abrir e salvar [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] em têm uma área no lado esquerdo da caixa de diálogo chamada **links favoritos**. Essa área é chamada de locais personalizados. As <xref:System.Windows.Forms.OpenFileDialog> classes <xref:System.Windows.Forms.SaveFileDialog> e permitem que você adicione pastas à <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção.  
  
> [!NOTE]
> Para que um local personalizado apareça <xref:System.Windows.Forms.OpenFileDialog> no ou <xref:System.Windows.Forms.SaveFileDialog>, a <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade deve ser definida como `true` (o padrão).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Para adicionar um local personalizado a uma caixa de diálogo de arquivo  
  
- Adicione um caminho, um GUID de pasta conhecida ou um <xref:System.Windows.Forms.FileDialogCustomPlace> objeto <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> à coleção da caixa de diálogo.  
  
     O exemplo de código a seguir mostra como adicionar um caminho:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [GUIDs de pasta conhecida para locais personalizados de diálogo de arquivo](known-folder-guids-for-file-dialog-custom-places.md)
