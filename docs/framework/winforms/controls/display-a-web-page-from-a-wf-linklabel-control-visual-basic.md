---
title: Exibir página da Web do controle LinkLabel (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 75373d55b7bc5ef11e39d5b9546996cb1c4f6f7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745917"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Como exibir uma página da Web a partir de um controle LinkLabel dos Windows Forms (Visual Basic)
Este exemplo exibe uma página da Web no navegador padrão quando um usuário clica em um Windows Forms <xref:System.Windows.Forms.LinkLabel> controle.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um formulário do Windows chamado `Form1`.  
  
- Um controle <xref:System.Windows.Forms.LinkLabel> chamado `LinkLabel1`.  
  
- Uma conexão ativa com a Internet.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A chamada para o método <xref:System.Diagnostics.Process.Start%2A> requer confiança total. Para obter mais informações, consulte <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.LinkLabel>
- [Controle LinkLabel](linklabel-control-windows-forms.md)
