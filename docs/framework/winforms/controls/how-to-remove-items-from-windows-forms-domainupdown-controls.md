---
title: Como remover itens de controles DomainUpDown dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: 702e5e2180148758c4b3775a5cc96a1365703166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Como remover itens de controles DomainUpDown dos Windows Forms
Você pode remover itens de Windows Forms <xref:System.Windows.Forms.DomainUpDown> controle chamando o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> método o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe. O <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> método Remove um item específico, enquanto o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> método Remove um item por sua posição.  
  
### <a name="to-remove-an-item"></a>Para remover um item  
  
-   Use o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> método o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe para remover um item por nome.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     -ou-  
  
-   Use o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> método para remover um item por sua posição.  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [Controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [Visão geral do controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
