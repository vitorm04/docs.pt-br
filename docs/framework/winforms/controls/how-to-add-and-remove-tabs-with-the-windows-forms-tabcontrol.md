---
title: 'Como: Adicionar e remover guias com o controle TabControl do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 938f1210eaa3479822e752327123737a3286fe9a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624054"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="6bc58-102">Como: Adicionar e remover guias com o controle TabControl do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bc58-102">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="6bc58-103">Por padrão, uma <xref:System.Windows.Forms.TabControl> controle contiver dois <xref:System.Windows.Forms.TabPage> controles.</span><span class="sxs-lookup"><span data-stu-id="6bc58-103">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="6bc58-104">Você pode acessar essas guias por meio de <xref:System.Windows.Forms.TabControl.TabPages%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc58-104">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="6bc58-105">Para adicionar uma guia de forma programática</span><span class="sxs-lookup"><span data-stu-id="6bc58-105">To add a tab programmatically</span></span>  
  
- <span data-ttu-id="6bc58-106">Use o <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> método da <xref:System.Windows.Forms.TabControl.TabPages%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc58-106">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="6bc58-107">Para remover uma guia de forma programática</span><span class="sxs-lookup"><span data-stu-id="6bc58-107">To remove a tab programmatically</span></span>  
  
- <span data-ttu-id="6bc58-108">Para remover guias selecionadas, use o <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> método da <xref:System.Windows.Forms.TabControl.TabPages%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc58-108">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="6bc58-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="6bc58-109">-or-</span></span>  
  
- <span data-ttu-id="6bc58-110">Para remover todas as guias, use o <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> método da <xref:System.Windows.Forms.TabControl.TabPages%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc58-110">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6bc58-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc58-111">See also</span></span>

- [<span data-ttu-id="6bc58-112">Visão geral do controle TabControl</span><span class="sxs-lookup"><span data-stu-id="6bc58-112">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="6bc58-113">Como: Adicionar um controle a uma página da guia</span><span class="sxs-lookup"><span data-stu-id="6bc58-113">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="6bc58-114">Como: Desabilitar páginas de guia</span><span class="sxs-lookup"><span data-stu-id="6bc58-114">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="6bc58-115">Como: Alterar a aparência do TabControl dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bc58-115">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
