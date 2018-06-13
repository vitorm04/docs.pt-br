---
title: Como criar um Windows Form redimensionável para entrada de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: a7768b3c6be10373e742cbeea0028d1aee0b261d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531785"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Como criar um Windows Form redimensionável para entrada de dados
Um bom layout responde bem a alterações nas dimensões de seu formulário pai. Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para organizar o layout do formulário para redimensionar e posicionar os controles de forma consistente, como alterar dimensões do formulário. O <xref:System.Windows.Forms.TableLayoutPanel> controle também é útil quando altera o conteúdo de seus controles causa alterações no layout. O processo abordado neste procedimento pode ser realizado no ambiente do Visual Studio.  Consulte também [Instruções passo a passo: criando um Windows Form redimensionável para entrada de dados](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar um <xref:System.Windows.Forms.TableLayoutPanel> controle para criar um layout que responde bem quando o usuário o redimensiona o formulário. Ele também demonstra um layout que responde bem à localização.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Como criar um layout dos Windows Forms que responda bem à localização](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers (Experiência do usuário do Microsoft Windows, diretrizes oficiais para desenvolvedores e designers da interface do usuário). Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
