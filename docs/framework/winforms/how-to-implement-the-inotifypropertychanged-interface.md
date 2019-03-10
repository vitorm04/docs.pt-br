---
title: 'Como: Implementar a Interface INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 51c0b1fa535921b7b33a16f55bdc8b76d6125e72
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704083"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Como: Implementar a Interface INotifyPropertyChanged
O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Implemente essa interface em objetos de negócios que são usados na associação de dados de formulários do Windows. Quando implementada, a interface se comunica com um controle associado a alteração de propriedade em um objeto comercial.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- [Como: Aplicar o padrão PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
- [Como: Gerar notificações de alteração usando um BindingSource e a Interface INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Notificação de alteração na vinculação de dados dos Windows Forms](change-notification-in-windows-forms-data-binding.md)
