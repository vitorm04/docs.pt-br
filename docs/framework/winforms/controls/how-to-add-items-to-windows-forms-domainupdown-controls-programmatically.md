---
title: Como adicionar itens a controles DomainUpDown dos Windows Forms de forma programática
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 7359310b092e84b250c09153ef86d44c70d413fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Como adicionar itens a controles DomainUpDown dos Windows Forms de forma programática
Você pode adicionar itens ao Windows Forms <xref:System.Windows.Forms.DomainUpDown> controle no código. Chamar o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> método o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe para adicionar itens ao controle de <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade. O <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> método adiciona um item ao final de uma coleção, enquanto o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> método adiciona um item em uma posição especificada.  
  
### <a name="to-add-a-new-item"></a>Para adicionar um novo item  
  
1.  Use o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> método para adicionar um item ao final da lista de itens.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     -ou-  
  
2.  Use o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> método para inserir um item na lista em uma posição especificada.  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>  
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>  
 [Controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [Visão geral do controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
