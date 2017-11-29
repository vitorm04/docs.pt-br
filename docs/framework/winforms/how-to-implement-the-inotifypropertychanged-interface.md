---
title: Como implementar a interface INotifyPropertyChanged
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Como implementar a interface INotifyPropertyChanged
O exemplo de código a seguir demonstra como implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Implemente essa interface em objetos de negócios que são usados na associação de dados de formulários do Windows. Quando implementada, a interface comunica-se a um controle associado as alterações de propriedade em um objeto de negócios.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como aplicar o padrão PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Vinculação de dados dos Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Como gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Notificação de alteração na vinculação de dados dos Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
