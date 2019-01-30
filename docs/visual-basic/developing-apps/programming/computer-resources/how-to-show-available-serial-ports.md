---
title: 'Como: Mostrar portas seriais disponíveis no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 58f4d629500223ccc6690912b5e261eebc17c6b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603801"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Como: Mostrar portas seriais disponíveis no Visual Basic
Este tópico descreve como usar `My.Computer.Ports` para mostrar as portas seriais do computador disponíveis em Visual Basic.  
  
 Para permitir que um usuário selecione qual porta usar, os nomes das portas seriais são colocados em um controle <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo faz um loop em todas as cadeias de caracteres que a propriedade `My.Computer.Ports.SerialPortNames` retorna. Essas cadeias de caracteres são os nomes das portas seriais disponíveis no computador.  
  
 Normalmente, um usuário seleciona qual porta serial o aplicativo deve usar na lista de portas disponíveis. Neste exemplo, os nomes das portas seriais são armazenados em um controle <xref:System.Windows.Forms.ListBox>. Para saber mais, veja [Controle ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 Este exemplo de código também está disponível como um snippet de código do IntelliSense. No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**. Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência de projeto ao System.Windows.Forms.dll.  
  
-   Acesso aos membros do namespace <xref:System.Windows.Forms>. Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Que seu formulário tenha um controle <xref:System.Windows.Forms.ListBox> chamado `ListBox1`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Você não precisa usar o controle <xref:System.Windows.Forms.ListBox> para exibir os nomes das portas seriais disponíveis. Em vez disso, você pode usar um <xref:System.Windows.Forms.ComboBox> ou outro controle. Se o aplicativo não precisa de uma resposta do usuário, você pode usar um controle <xref:System.Windows.Forms.TextBox> para exibir as informações.  
  
> [!NOTE]
>  Os nomes das portas retornados por `My.Computer.Ports.SerialPortNames` podem estar incorretos quando executados no Windows 98. Para evitar erros de aplicativo, use o tratamento de exceções, como a instrução `Try...Catch...Finally` ou a instrução `Using`, ao usar os nomes de portas para abrir portas.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Como: Discar modems anexados a portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Como: Enviar cadeias de caracteres para portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Como: Receber cadeias de caracteres de portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
