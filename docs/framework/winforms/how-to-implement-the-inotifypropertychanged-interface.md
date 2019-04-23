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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Como: implementar a interface INotifyPropertyChanged
O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Implemente essa interface em objetos de negócios que são usados na associação de dados de formulários do Windows. Quando implementada, a interface se comunica com um controle associado a alteração de propriedade em um objeto comercial.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Aplicar o padrão PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
- [Como: Gerar notificações de alteração usando um BindingSource e a Interface INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Notificação de alteração na vinculação de dados dos Windows Forms](change-notification-in-windows-forms-data-binding.md)
