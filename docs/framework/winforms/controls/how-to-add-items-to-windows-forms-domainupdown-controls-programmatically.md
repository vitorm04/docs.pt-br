---
title: adicionar itens a controles DomainUpDown de modo programático
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745584"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Como adicionar itens a controles DomainUpDown dos Windows Forms de forma programática
Você pode adicionar itens ao controle de <xref:System.Windows.Forms.DomainUpDown> de Windows Forms no código. Chame o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> da classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> para adicionar itens à propriedade <xref:System.Windows.Forms.DomainUpDown.Items%2A> do controle. O método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> adiciona um item ao final de uma coleção, enquanto o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> adiciona um item em uma posição especificada.  
  
### <a name="to-add-a-new-item"></a>Para adicionar um novo item  
  
1. Use o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> para adicionar um item ao final da lista de itens.  
  
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
  
2. Use o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> para inserir um item na lista em uma posição especificada.  
  
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

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [Controle DomainUpDown](domainupdown-control-windows-forms.md)
- [Visão geral do controle DomainUpDown](domainupdown-control-overview-windows-forms.md)
