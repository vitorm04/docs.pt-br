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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Como adicionar um local personalizado a uma caixa de diálogo Arquivo
As caixas de diálogo padrão abrir e salvar no Windows Vista têm uma área no lado esquerdo da caixa de diálogo chamada **links favoritos**. Essa área é chamada de locais personalizados. As classes <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> permitem que você adicione pastas à coleção de <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>.  
  
> [!NOTE]
> Para que um local personalizado apareça no <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, a propriedade <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> deve ser definida como `true` (o padrão).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Para adicionar um local personalizado a uma caixa de diálogo de arquivo  
  
- Adicione um caminho, um GUID de pasta conhecido ou um objeto <xref:System.Windows.Forms.FileDialogCustomPlace> à coleção <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> da caixa de diálogo.  
  
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
