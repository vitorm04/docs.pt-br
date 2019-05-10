---
title: 'Como: criar formulários pai MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 2aa4261d6354f744f000f36a87e70a39f5c004ea
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211384"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="2be2a-102">Como: criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="2be2a-102">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2be2a-103">Este tópico usa o controle <xref:System.Windows.Forms.MainMenu>, que foi substituído pelo controle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2be2a-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="2be2a-104">O controle <xref:System.Windows.Forms.MainMenu> é mantido para compatibilidade com versões anteriores e uso futuro, se você desejar.</span><span class="sxs-lookup"><span data-stu-id="2be2a-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="2be2a-105">Para obter informações sobre como criar um MDI pai formulário usando um <xref:System.Windows.Forms.MenuStrip>, consulte [como: Criar uma lista de janelas MDI com MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2be2a-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="2be2a-106">A base de um aplicativo de interface MDI é o formulário MDI pai.</span><span class="sxs-lookup"><span data-stu-id="2be2a-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="2be2a-107">Este é o formulário que contém as janelas MDI filhas, que as subjanelas nas quais o usuário interage com o aplicativo MDI.</span><span class="sxs-lookup"><span data-stu-id="2be2a-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="2be2a-108">Criar um formulário MDI pai é fácil, tanto no Designer de Formulários do Windows e por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="2be2a-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="2be2a-109">Criar um formulário pai MDI em tempo de design</span><span class="sxs-lookup"><span data-stu-id="2be2a-109">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="2be2a-110">Crie um projeto de aplicativo do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2be2a-110">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="2be2a-111">No **propriedades** janela, defina o <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade **true**.</span><span class="sxs-lookup"><span data-stu-id="2be2a-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="2be2a-112">Isso designa o formulário como um recipiente MDI para janelas filho.</span><span class="sxs-lookup"><span data-stu-id="2be2a-112">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2be2a-113">Ao configurar propriedades na janela **Propriedades**, você também pode definir a propriedade `WindowState` para **Maximized**, se desejar, pois é mais fácil manipular janelas filho MDI quando o formulário pai está maximizado.</span><span class="sxs-lookup"><span data-stu-id="2be2a-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="2be2a-114">Além disso, esteja ciente de que a borda do formulário MDI pai selecionará a cor do sistema (definida no Painel de Controle do Sistema do Windows), em vez da cor de fundo definida usando a propriedade <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2be2a-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="2be2a-115">Na **Caixa de Ferramentas**, arraste um controle **MenuStrip** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="2be2a-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="2be2a-116">Crie um item de menu de nível superior com a propriedade **Text** definida para **&File** com itens de submenu chamados **&New** e **&Close**.</span><span class="sxs-lookup"><span data-stu-id="2be2a-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="2be2a-117">Crie também um item de menu de nível superior chamado **&Window**.</span><span class="sxs-lookup"><span data-stu-id="2be2a-117">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="2be2a-118">O primeiro menu criará e ocultará itens do menu no tempo de execução e o segundo menu irá controlar as janelas MDI filhas abertas.</span><span class="sxs-lookup"><span data-stu-id="2be2a-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="2be2a-119">Neste ponto, você já terá criado uma janela MDI pai.</span><span class="sxs-lookup"><span data-stu-id="2be2a-119">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="2be2a-120">Pressione **F5** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2be2a-120">Press **F5** to run the application.</span></span> <span data-ttu-id="2be2a-121">Para obter informações sobre como criar janelas que operam no formulário pai MDI filho MDI, consulte [como: Criar formulários filho MDI](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2be2a-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2be2a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2be2a-122">See also</span></span>

- [<span data-ttu-id="2be2a-123">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="2be2a-123">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="2be2a-124">Como: Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="2be2a-124">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="2be2a-125">Como: Determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="2be2a-125">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="2be2a-126">Como: Enviar dados para o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="2be2a-126">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="2be2a-127">Como: Organizar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="2be2a-127">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
