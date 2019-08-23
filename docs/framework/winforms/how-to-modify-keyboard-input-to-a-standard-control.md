---
title: 'Como: modificar a entrada do teclado para um controle padrão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964285"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Como: modificar a entrada do teclado para um controle padrão
O Windows Forms fornece a capacidade de consumir e modificar as entradas do teclado. Consumir uma tecla significa tratá-la dentro de um método ou manipulador de eventos para que outros métodos e eventos mais adiante na fila de mensagens não recebam o valor da tecla. Modificar uma tecla significa modificar o valor de uma tecla para que os métodos e manipuladores de eventos mais adiante na fila de mensagens recebam um valor de tecla diferente. Este tópico mostra como realizar essas tarefas.  
  
### <a name="to-consume-a-key"></a>Consumir uma tecla  
  
- Em um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos, defina <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> a propriedade da <xref:System.Windows.Forms.KeyPressEventArgs> classe como `true`.  
  
     -ou-  
  
     Em um <xref:System.Windows.Forms.Control.KeyDown> manipulador de eventos, defina <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> a propriedade da <xref:System.Windows.Forms.KeyEventArgs> classe como `true`.  
  
    > [!NOTE]
    > Definir a <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.Control.KeyDown> Propriedade no manipulador de eventos não impede que os <xref:System.Windows.Forms.Control.KeyPress> eventos <xref:System.Windows.Forms.Control.KeyUp> e sejam gerados para o pressionamento de teclas atual. Use a <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> propriedade para essa finalidade.  
  
     O exemplo a seguir é um trecho de `switch` uma instrução que examina a <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> Propriedade do <xref:System.Windows.Forms.KeyPressEventArgs> recebido por um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos. Esse código consome as teclas dos caracteres “A” e “a”.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Modificar uma tecla de caractere padrão  
  
- Em um <xref:System.Windows.Forms.Control.KeyPress> manipulador de eventos, defina <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> a propriedade da <xref:System.Windows.Forms.KeyPressEventArgs> classe como o valor da nova chave de caractere.  
  
     O exemplo a seguir é um trecho de uma instrução `switch` que modifica “B” para “A” e “b” para “a”. Observe que a <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> propriedade <xref:System.Windows.Forms.KeyPressEventArgs> do parâmetro é definida como `false`, de forma que o novo valor de chave seja propagado para outros métodos e eventos na fila de mensagens.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Modificar uma tecla não caractere  
  
- Substitua um <xref:System.Windows.Forms.Control> método que processa mensagens do Windows, detecte a mensagem WM_KEYDOWN ou WM_SYSKEYDOWN e <xref:System.Windows.Forms.Message.WParam%2A> defina a propriedade <xref:System.Windows.Forms.Message> do parâmetro para <xref:System.Windows.Forms.Keys> o valor que representa a nova chave não caractere.  
  
     O exemplo de código a seguir demonstra como substituir <xref:System.Windows.Forms.Control.PreProcessMessage%2A> o método de um controle para detectar as teclas F1 por F9 e modificar qualquer pressionamento de tecla F3 para F1. Para obter mais informações <xref:System.Windows.Forms.Control> sobre os métodos que você pode substituir para interceptar mensagens do teclado, consulte [entrada do usuário em um aplicativo Windows Forms](user-input-in-a-windows-forms-application.md) e [como funciona a entrada do teclado](how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir é o aplicativo completo para os exemplos de código nas seções anteriores. O aplicativo usa um controle personalizado derivado da <xref:System.Windows.Forms.TextBox> classe para consumir e modificar a entrada do teclado.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- [Entrada do teclado em um aplicativo dos Windows Forms](keyboard-input-in-a-windows-forms-application.md)
- [Entrada do usuário em um aplicativo dos Windows Forms](user-input-in-a-windows-forms-application.md)
- [Como a entrada do teclado funciona](how-keyboard-input-works.md)
