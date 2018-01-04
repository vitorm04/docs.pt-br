---
title: "Como manipular a entrada do teclado no nível do formulário"
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
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c2650457d9ab6a5c5deb7b0fc5a9303d0465916
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Como manipular a entrada do teclado no nível do formulário
Os Windows Forms proporcionam a capacidade de manipular mensagens de teclado no nível do formulário, antes que as mensagens cheguem a um controle. Este tópico mostra como realizar essa tarefa.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Como manipular uma mensagem do teclado no nível do formulário  
  
-   Lidar com o <xref:System.Windows.Forms.Control.KeyPress> ou <xref:System.Windows.Forms.Control.KeyDown> eventos do formulário de inicialização e conjunto de <xref:System.Windows.Forms.Form.KeyPreview%2A> propriedade a fim de `true` para que as mensagens do teclado são recebidas pelo formulário antes que elas atinjam os controles no formulário. O seguinte código exemplo manipula o <xref:System.Windows.Forms.Control.KeyPress> evento detectando todas as teclas numéricas e consumindo '1', '4' e '7'.  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir é o aplicativo completo para o exemplo acima. O aplicativo inclui um <xref:System.Windows.Forms.TextBox> juntamente com vários outros controles que permitem que você mova o foco do <xref:System.Windows.Forms.TextBox>. O <xref:System.Windows.Forms.Control.KeyPress> eventos da janela principal <xref:System.Windows.Forms.Form> consome '1', '4' e '7' e o <xref:System.Windows.Forms.Control.KeyPress> evento o <xref:System.Windows.Forms.TextBox> consome '2', '5' e '8' e exibe as teclas restantes. Comparar o <xref:System.Windows.Forms.MessageBox> saída quando você pressiona uma tecla de número enquanto o <xref:System.Windows.Forms.TextBox> tem foco com a <xref:System.Windows.Forms.MessageBox> quando você pressiona uma tecla de número enquanto o foco está em um dos outros controles de saída.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 [Entrada do teclado em um aplicativo dos Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
