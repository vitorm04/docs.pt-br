---
title: "Como exibir uma página da Web a partir de um controle LinkLabel dos Windows Forms (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38ef165dc655fedbf682a21220d6a76532b18f6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="a456a-102">Como exibir uma página da Web a partir de um controle LinkLabel dos Windows Forms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a456a-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="a456a-103">Este exemplo exibe uma página da Web no navegador padrão, quando um usuário clica em um Windows Forms <xref:System.Windows.Forms.LinkLabel> controle.</span><span class="sxs-lookup"><span data-stu-id="a456a-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a456a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a456a-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a456a-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a456a-105">Compiling the Code</span></span>  
 <span data-ttu-id="a456a-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a456a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a456a-107">Um formulário do Windows chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a456a-107">A Windows Form named `Form1`.</span></span>  
  
-   <span data-ttu-id="a456a-108">Um <xref:System.Windows.Forms.LinkLabel> controle chamado `LinkLabel1`.</span><span class="sxs-lookup"><span data-stu-id="a456a-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
-   <span data-ttu-id="a456a-109">Uma conexão de Internet ativa.</span><span class="sxs-lookup"><span data-stu-id="a456a-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a456a-110">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a456a-110">.NET Framework Security</span></span>  
 <span data-ttu-id="a456a-111">A chamada para o <xref:System.Diagnostics.Process.Start%2A> método requer confiança total.</span><span class="sxs-lookup"><span data-stu-id="a456a-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="a456a-112">Para obter mais informações, consulte <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="a456a-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a456a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a456a-113">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="a456a-114">Controle LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a456a-114">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
