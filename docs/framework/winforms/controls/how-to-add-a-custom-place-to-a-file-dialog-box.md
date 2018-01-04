---
title: "Como adicionar um local personalizado a uma caixa de diálogo Arquivo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1a10a58552dd416084da39838a9e36f15e85074
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
