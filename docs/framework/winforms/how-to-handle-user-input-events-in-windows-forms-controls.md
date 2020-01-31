---
title: Manipular eventos de entrada do usuário em controles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 19adeb6c803c76cba4139841f58087487d523a50
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739425"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Como manipular eventos de entrada do usuário em controles do Windows Forms
Este exemplo demonstra como lidar com a maioria dos eventos de teclado, mouse, foco e validação que podem ocorrer em um controle de Windows Forms. A caixa de texto chamada `TextBoxInput` recebe os eventos quando ele tem o foco e as informações sobre cada evento são gravadas na caixa de texto chamada `TextBoxOutput` na ordem em que os eventos são gerados. O aplicativo também inclui um conjunto de caixas de seleção que podem ser usadas para filtrar os eventos a serem relatados.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- [Entrada do usuário nos Windows Forms](user-input-in-windows-forms.md)
