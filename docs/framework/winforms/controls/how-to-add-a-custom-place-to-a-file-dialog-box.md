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
ms.locfileid: "33525733"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Como adicionar um local personalizado a uma caixa de diálogo Arquivo
O padrão abrir e salvar caixas de diálogo em [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] tem uma área no lado esquerdo da caixa de diálogo intitulada **Links Favoritos**. Essa área é denominada locais personalizados. O <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> classes permitem que você adicione pastas para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção.  
  
> [!NOTE]
>  Para que um local personalizado para aparecer no <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>, o <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriedade deve ser definida como `true` (o padrão).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Para adicionar um local personalizado para uma caixa de diálogo  
  
-   Adicione um caminho, um GUID de pasta conhecidas, ou um <xref:System.Windows.Forms.FileDialogCustomPlace> o objeto para o <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> coleção da caixa de diálogo.  
  
     O exemplo de código a seguir mostra como adicionar um caminho:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [GUIDs de pasta conhecida para locais personalizados de diálogo de arquivo](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
