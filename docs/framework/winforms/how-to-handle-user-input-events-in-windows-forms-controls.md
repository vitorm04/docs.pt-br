---
title: 'Como: Tratar eventos de entrada do usuário em controles dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: e4fa03a07e97fe1d860b281b8e5cece0c41d6c27
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56331955"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Como: Tratar eventos de entrada do usuário em controles dos Windows Forms
Este exemplo demonstra como lidar com a maioria dos teclado, mouse, foco e eventos de validação que podem ocorrer em um controle Windows Forms. A caixa de texto denominada `TextBoxInput` recebe os eventos quando ele tem o foco e informações sobre cada evento são gravadas na caixa de texto chamada `TextBoxOutput` na ordem em que os eventos são gerados. O aplicativo também inclui um conjunto de caixas de seleção que pode ser usado para filtrar quais eventos de relatório.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também
- [Entrada do usuário nos Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
