---
title: 'Como: manipular eventos de entrada do usuário em controles do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: ae230f22c929be39ea00eafe378c6910c4a9d35f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592088"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="95120-102">Como: manipular eventos de entrada do usuário em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95120-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="95120-103">Este exemplo demonstra como lidar com a maioria dos teclado, mouse, foco e eventos de validação que podem ocorrer em um controle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="95120-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="95120-104">A caixa de texto denominada `TextBoxInput` recebe os eventos quando ele tem o foco e informações sobre cada evento são gravadas na caixa de texto chamada `TextBoxOutput` na ordem em que os eventos são gerados.</span><span class="sxs-lookup"><span data-stu-id="95120-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="95120-105">O aplicativo também inclui um conjunto de caixas de seleção que pode ser usado para filtrar quais eventos de relatório.</span><span class="sxs-lookup"><span data-stu-id="95120-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95120-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95120-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95120-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="95120-107">Compiling the Code</span></span>  
 <span data-ttu-id="95120-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="95120-108">This example requires:</span></span>  
  
- <span data-ttu-id="95120-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="95120-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95120-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95120-110">See also</span></span>

- [<span data-ttu-id="95120-111">Entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95120-111">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
