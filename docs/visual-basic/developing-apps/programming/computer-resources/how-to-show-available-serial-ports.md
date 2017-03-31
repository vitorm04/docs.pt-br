---
title: "Como mostrar portas seriais disponíveis no Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cc316600acd5f551dad8fbd4b7260c512231da5e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Como mostrar portas seriais disponíveis no Visual Basic
Este tópico descreve como usar `My.Computer.Ports` para mostrar as portas seriais disponíveis do computador no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Para permitir que um usuário selecione qual porta usar, os nomes das portas seriais são colocados em um controle <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo faz um loop em todas as cadeias de caracteres que a propriedade `My.Computer.Ports.SerialPortNames` retorna. Essas cadeias de caracteres são os nomes das portas seriais disponíveis no computador.  
  
 Normalmente, um usuário seleciona qual porta serial o aplicativo deve usar na lista de portas disponíveis. Neste exemplo, os nomes das portas seriais são armazenados em um controle <xref:System.Windows.Forms.ListBox>. Para saber mais, veja [Controle ListBox](http://msdn.microsoft.com/library/b0172473-c5f2-411e-aaa4-c8f17cb5eed4).  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No selecionador de trecho de código, ele está localizado em **Conectividade e Redes**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência de projeto ao System.Windows.Forms.dll.  
  
-   Acesso aos membros do namespace <xref:System.Windows.Forms>. Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Que seu formulário tenha um controle <xref:System.Windows.Forms.ListBox> denominado `ListBox1`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Você não precisa usar o controle <xref:System.Windows.Forms.ListBox> para exibir os nomes das portas seriais disponíveis. Em vez disso, você pode usar um <xref:System.Windows.Forms.ComboBox> ou outro controle. Se o aplicativo não precisa de uma resposta do usuário, você pode usar um controle <xref:System.Windows.Forms.TextBox> para exibir as informações.  
  
> [!NOTE]
>  Os nomes das portas retornados por `My.Computer.Ports.SerialPortNames` podem estar incorretos quando executados no Windows 98. Para evitar erros de aplicativo, use o tratamento de exceções, como a instrução `Try...Catch...Finally` ou a instrução `Using`, ao usar os nomes de portas para abrir portas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Como discar modems conectados às portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [Como enviar cadeias de caracteres para portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [Como Receber Cadeias de Caracteres de Portas Seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
