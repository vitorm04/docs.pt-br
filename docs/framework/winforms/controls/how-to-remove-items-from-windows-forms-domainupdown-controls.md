---
title: 'Como: Remover itens de controles DomainUpDown dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: f1cc4a26929a39e85fa6028613b0712cc76ed4f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644225"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Como: Remover itens de controles DomainUpDown dos Windows Forms
Você pode remover itens dos formulários do Windows <xref:System.Windows.Forms.DomainUpDown> controle chamando o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> método da <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe. O <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> método Remove um item específico, enquanto o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> método Remove um item por sua posição.  
  
### <a name="to-remove-an-item"></a>Para remover um item  
  
-   Use o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> método da <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe para remover um item por nome.  
  
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
- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [Controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
- [Visão geral do controle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
