---
title: Como organizar formulários filho MDI
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: d5c0d24ff8a7188a669c218ce8b0dc66ffa56c47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521021"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="63f32-102">Como organizar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="63f32-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="63f32-103">Muitas vezes, os aplicativos terão comandos de menu para ações como Lado a lado, Em cascata e Organizar, que controlam o layout dos formulários MDI filhos abertos.</span><span class="sxs-lookup"><span data-stu-id="63f32-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="63f32-104">Você pode usar o método <xref:System.Windows.Forms.Form.LayoutMdi%2A> com um dos valores de enumeração <xref:System.Windows.Forms.MdiLayout> para reorganizar os formulários MDI filhos em um formulário MDI pai.</span><span class="sxs-lookup"><span data-stu-id="63f32-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="63f32-105">Os valores de enumeração <xref:System.Windows.Forms.MdiLayout> exibem formulários filhos em cascata, lado a lado horizontal ou verticalmente, ou como ícones de formulários filhos organizados na parte inferior do formulário MDI.</span><span class="sxs-lookup"><span data-stu-id="63f32-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="63f32-106">Esses valores possuem o mesmo efeito que os comandos do Windows **Janelas em cascata**, **Mostrar janelas lado a lado**, **Mostrar janelas empilhadas** e **Mostrar a área de trabalho**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="63f32-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="63f32-107">Geralmente, esses métodos são usados como manipuladores de evento chamados por um evento <xref:System.Windows.Forms.Control.Click> do item do menu.</span><span class="sxs-lookup"><span data-stu-id="63f32-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="63f32-108">Dessa forma, um item de menu com o texto "Em cascata" pode ter o efeito desejado em janelas MDI filhas.</span><span class="sxs-lookup"><span data-stu-id="63f32-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="63f32-109">Para organizar formulários filhos</span><span class="sxs-lookup"><span data-stu-id="63f32-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="63f32-110">Em um método, use o método <xref:System.Windows.Forms.Form.LayoutMdi%2A> para definir a enumeração <xref:System.Windows.Forms.MdiLayout> para o formulário MDI pai.</span><span class="sxs-lookup"><span data-stu-id="63f32-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="63f32-111">O exemplo a seguir usa o valor de enumeração <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> para as janelas filhas do formulário MDI pai (`Form1`).</span><span class="sxs-lookup"><span data-stu-id="63f32-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="63f32-112">A enumeração é usada no código durante o manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento o **janelas em cascata** item de menu.</span><span class="sxs-lookup"><span data-stu-id="63f32-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="63f32-113">Você também pode colocar as janelas lado a lado e organizá-las como ícones alterando o valor de enumeração <xref:System.Windows.Forms.MdiLayout> usado.</span><span class="sxs-lookup"><span data-stu-id="63f32-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="63f32-114">Se você estiver usando o Visual C#, coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="63f32-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="63f32-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63f32-115">See Also</span></span>  
 [<span data-ttu-id="63f32-116">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="63f32-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="63f32-117">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="63f32-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="63f32-118">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="63f32-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="63f32-119">Como determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="63f32-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="63f32-120">Como Enviar Dados para o Filho MDI Ativo</span><span class="sxs-lookup"><span data-stu-id="63f32-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
