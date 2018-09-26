---
title: Como manipular a entrada do teclado no nível do formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: a75c4f116b32499f9ba33dd863f2a5b6952a3e24
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198027"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Como manipular a entrada do teclado no nível do formulário
Os Windows Forms proporcionam a capacidade de manipular mensagens de teclado no nível do formulário, antes que as mensagens cheguem a um controle. Este tópico mostra como realizar essa tarefa.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Como manipular uma mensagem do teclado no nível do formulário  
  
-   Lidar com o <xref:System.Windows.Forms.Control.KeyPress> ou <xref:System.Windows.Forms.Control.KeyDown> evento do formulário de inicialização e defina as <xref:System.Windows.Forms.Form.KeyPreview%2A> propriedade do formulário para `true` para que as mensagens do teclado são recebidas pelo formulário antes que elas atinjam os controles no formulário. O seguinte código de exemplo manipula o <xref:System.Windows.Forms.Control.KeyPress> eventos, detectando todas as teclas numéricas e consumindo '1', '4' e '7'.  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir é o aplicativo completo para o exemplo acima. O aplicativo inclui um <xref:System.Windows.Forms.TextBox> juntamente com vários outros controles que permitem que você mova o foco do <xref:System.Windows.Forms.TextBox>. O <xref:System.Windows.Forms.Control.KeyPress> eventos da janela principal <xref:System.Windows.Forms.Form> consome '1', '4' e '7' e o <xref:System.Windows.Forms.Control.KeyPress> evento do <xref:System.Windows.Forms.TextBox> consome '2', '5' e '8' e exibe as teclas restantes. Comparar as <xref:System.Windows.Forms.MessageBox> de saída quando você pressiona uma tecla numérica enquanto o <xref:System.Windows.Forms.TextBox> tem o foco com o <xref:System.Windows.Forms.MessageBox> quando você pressiona uma tecla numérica enquanto o foco está em um dos outros controles de saída.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 [Entrada do teclado em um aplicativo dos Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
