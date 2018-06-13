---
title: Como implementar a interface INotifyPropertyChanged
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 8f64b51a7d56f609399baac613a651e82b91e6df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536406"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Como implementar a interface INotifyPropertyChanged
O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Implemente essa interface em objetos de negócios que são usados na associação de dados de formulários do Windows. Quando implementada, a interface comunica-se a um controle associado as alterações de propriedade em um objeto de negócios.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como aplicar o padrão PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Associação de dados do Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Como gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Notificação de alteração na vinculação de dados dos Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
