---
title: Remover itens de controles DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735774"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Como remover itens de controles DomainUpDown dos Windows Forms
Você pode remover itens do controle de <xref:System.Windows.Forms.DomainUpDown> de Windows Forms chamando o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> da classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>. O método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> remove um item específico, enquanto o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> remove um item por sua posição.  
  
### <a name="to-remove-an-item"></a>Para remover um item  
  
- Use o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> da classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> para remover um item por nome.  
  
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
  
- Use o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> para remover um item pela sua posição.  
  
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
- [Controle DomainUpDown](domainupdown-control-windows-forms.md)
- [Visão geral do controle DomainUpDown](domainupdown-control-overview-windows-forms.md)
