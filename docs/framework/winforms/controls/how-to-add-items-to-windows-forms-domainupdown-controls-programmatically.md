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
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="84e29-102">Como adicionar itens a controles DomainUpDown dos Windows Forms de forma programática</span><span class="sxs-lookup"><span data-stu-id="84e29-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="84e29-103">Você pode adicionar itens ao controle de <xref:System.Windows.Forms.DomainUpDown> de Windows Forms no código.</span><span class="sxs-lookup"><span data-stu-id="84e29-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="84e29-104">Chame o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> da classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> para adicionar itens à propriedade <xref:System.Windows.Forms.DomainUpDown.Items%2A> do controle.</span><span class="sxs-lookup"><span data-stu-id="84e29-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="84e29-105">O método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> adiciona um item ao final de uma coleção, enquanto o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> adiciona um item em uma posição especificada.</span><span class="sxs-lookup"><span data-stu-id="84e29-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="84e29-106">Para adicionar um novo item</span><span class="sxs-lookup"><span data-stu-id="84e29-106">To add a new item</span></span>  
  
1. <span data-ttu-id="84e29-107">Use o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> para adicionar um item ao final da lista de itens.</span><span class="sxs-lookup"><span data-stu-id="84e29-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="84e29-108">-ou-</span><span class="sxs-lookup"><span data-stu-id="84e29-108">-or-</span></span>  
  
2. <span data-ttu-id="84e29-109">Use o método <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> para inserir um item na lista em uma posição especificada.</span><span class="sxs-lookup"><span data-stu-id="84e29-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84e29-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84e29-110">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [<span data-ttu-id="84e29-111">Controle DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="84e29-111">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="84e29-112">Visão geral do controle DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="84e29-112">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
