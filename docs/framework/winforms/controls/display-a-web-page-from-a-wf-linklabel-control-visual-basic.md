---
title: Como exibir uma página da Web a partir de um controle LinkLabel dos Windows Forms (Visual Basic)
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
ms.openlocfilehash: a9964c8d333ea87dd995ec9111acc1a8ac1e79b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524177"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="51cb7-102">Como exibir uma página da Web a partir de um controle LinkLabel dos Windows Forms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51cb7-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="51cb7-103">Este exemplo exibe uma página da Web no navegador padrão, quando um usuário clica em um Windows Forms <xref:System.Windows.Forms.LinkLabel> controle.</span><span class="sxs-lookup"><span data-stu-id="51cb7-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cb7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51cb7-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="51cb7-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="51cb7-105">Compiling the Code</span></span>  
 <span data-ttu-id="51cb7-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="51cb7-106">This example requires:</span></span>  
  
-   <span data-ttu-id="51cb7-107">Um formulário do Windows chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="51cb7-107">A Windows Form named `Form1`.</span></span>  
  
-   <span data-ttu-id="51cb7-108">Um controle <xref:System.Windows.Forms.LinkLabel> chamado `LinkLabel1`.</span><span class="sxs-lookup"><span data-stu-id="51cb7-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
-   <span data-ttu-id="51cb7-109">Uma conexão de Internet ativa.</span><span class="sxs-lookup"><span data-stu-id="51cb7-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="51cb7-110">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="51cb7-110">.NET Framework Security</span></span>  
 <span data-ttu-id="51cb7-111">A chamada para o <xref:System.Diagnostics.Process.Start%2A> método requer confiança total.</span><span class="sxs-lookup"><span data-stu-id="51cb7-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="51cb7-112">Para obter mais informações, consulte <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="51cb7-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51cb7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51cb7-113">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="51cb7-114">Controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="51cb7-114">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
