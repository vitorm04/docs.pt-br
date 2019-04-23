---
title: 'Como: implementar a interface INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225593"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="43daa-102">Como: implementar a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="43daa-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="43daa-103">O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="43daa-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="43daa-104">Implemente essa interface em objetos de negócios que são usados na associação de dados de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="43daa-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="43daa-105">Quando implementada, a interface se comunica com um controle associado a alteração de propriedade em um objeto comercial.</span><span class="sxs-lookup"><span data-stu-id="43daa-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43daa-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43daa-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="43daa-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43daa-107">See also</span></span>

- [<span data-ttu-id="43daa-108">Como: Aplicar o padrão PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="43daa-108">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="43daa-109">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43daa-109">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="43daa-110">Como: Gerar notificações de alteração usando um BindingSource e a Interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="43daa-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="43daa-111">Notificação de alteração na vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43daa-111">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
