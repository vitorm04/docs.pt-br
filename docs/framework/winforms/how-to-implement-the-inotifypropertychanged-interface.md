---
title: 'Como: implementar a interface INotifyPropertyChanged'
description: Saiba como implementar a interface INotifyPropertyChanged em objetos comerciais que são usados em Windows Forms Associação de dados.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619262"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="8fa16-103">Como: implementar a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="8fa16-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="8fa16-104">O exemplo de código a seguir demonstra como implementar a <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="8fa16-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="8fa16-105">Implemente essa interface em objetos comerciais que são usados em Windows Forms Associação de dados.</span><span class="sxs-lookup"><span data-stu-id="8fa16-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="8fa16-106">Quando implementada, a interface se comunica com um controle associado que a propriedade altera em um objeto comercial.</span><span class="sxs-lookup"><span data-stu-id="8fa16-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fa16-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8fa16-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8fa16-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="8fa16-108">See also</span></span>

- [<span data-ttu-id="8fa16-109">Como: aplicar o padrão PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="8fa16-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="8fa16-110">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fa16-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="8fa16-111">Como acionar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="8fa16-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="8fa16-112">Notificação de alteração na associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fa16-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
