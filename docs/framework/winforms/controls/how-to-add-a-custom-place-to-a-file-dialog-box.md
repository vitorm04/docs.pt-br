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
ms.openlocfilehash: 79836dd260cb13912ccba43cfb4a0a3e0ad195fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011145"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Como: Adicionar um local personalizado a uma caixa de diálogo Arquivo
O padrão abrir e salvar as caixas de diálogo no [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] têm uma área no lado esquerdo da caixa de diálogo intitulada **Links Favoritos**. Essa área é chamada de locais personalizados. O <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes permitem que você adicione pastas para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção.  
  
> [!NOTE]
>  Em ordem para um local personalizado apareça na <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, o <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade deve ser definida como `true` (o padrão).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Para adicionar um local personalizado a uma caixa de diálogo de arquivo  
  
- Adicionar um caminho, um GUID de pasta conhecida, ou um <xref:System.Windows.Forms.FileDialogCustomPlace> do objeto para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção da caixa de diálogo.  
  
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
