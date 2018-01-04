---
title: "Como aplicar o padrão PropertyNameChanged"
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
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe397a92ac6e79e84757baa0c41f6e0c54b7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="5bf77-102">Como aplicar o padrão PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="5bf77-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="5bf77-103">O exemplo de código a seguir demonstra como aplicar o *PropertyName*padrão alterado para um controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="5bf77-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="5bf77-104">Aplica esse padrão quando você implementar controles personalizados que são usados com o mecanismo de associação de dados de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5bf77-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bf77-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5bf77-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bf77-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5bf77-106">Compiling the Code</span></span>  
 <span data-ttu-id="5bf77-107">Para compilar o exemplo de código anterior:</span><span class="sxs-lookup"><span data-stu-id="5bf77-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="5bf77-108">Cole o código em um arquivo de código vazio.</span><span class="sxs-lookup"><span data-stu-id="5bf77-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="5bf77-109">Você deve usar o controle personalizado em um Windows Form que contém um `Main` método.</span><span class="sxs-lookup"><span data-stu-id="5bf77-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf77-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bf77-110">See Also</span></span>  
 [<span data-ttu-id="5bf77-111">Como implementar a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="5bf77-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="5bf77-112">Notificação de alteração na vinculação de dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5bf77-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="5bf77-113">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5bf77-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
