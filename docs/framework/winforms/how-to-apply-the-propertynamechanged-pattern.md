---
title: 'Como: Aplicar o padrão PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 82856405ab3c9581b398f358e5bf9ecf989ce193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539760"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Como: Aplicar o padrão PropertyNameChanged
O exemplo de código a seguir demonstra como aplicar a *PropertyName*Changed padrão para um controle personalizado. Aplica esse padrão quando você implementa controles personalizados que são usados com o mecanismo de associação de dados de formulários do Windows.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o exemplo de código anterior:  
  
-   Cole o código em um arquivo de código vazio. Você deve usar o controle personalizado em um formulário do Windows que contenha um `Main` método.  
  
## <a name="see-also"></a>Consulte também
- [Como: Implementar a Interface INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)
- [Notificação de alteração na vinculação de dados dos Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [Associação de dados do Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
