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
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="5d2c3-102">Como: Aplicar o padrão PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="5d2c3-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="5d2c3-103">O exemplo de código a seguir demonstra como aplicar a *PropertyName*Changed padrão para um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="5d2c3-104">Aplica esse padrão quando você implementa controles personalizados que são usados com o mecanismo de associação de dados de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d2c3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d2c3-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d2c3-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5d2c3-106">Compiling the Code</span></span>  
 <span data-ttu-id="5d2c3-107">Para compilar o exemplo de código anterior:</span><span class="sxs-lookup"><span data-stu-id="5d2c3-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="5d2c3-108">Cole o código em um arquivo de código vazio.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="5d2c3-109">Você deve usar o controle personalizado em um formulário do Windows que contenha um `Main` método.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d2c3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d2c3-110">See also</span></span>
- [<span data-ttu-id="5d2c3-111">Como: Implementar a Interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="5d2c3-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)
- [<span data-ttu-id="5d2c3-112">Notificação de alteração na vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d2c3-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="5d2c3-113">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d2c3-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
