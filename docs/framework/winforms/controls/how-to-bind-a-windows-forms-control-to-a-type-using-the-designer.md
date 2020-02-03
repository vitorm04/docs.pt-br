---
title: Associar o controle a um tipo usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742022"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="f828a-102">Como associar um controle dos Windows Forms a um tipo usando o designer</span><span class="sxs-lookup"><span data-stu-id="f828a-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>

<span data-ttu-id="f828a-103">Quando estiver compilando controles que interagem com os dados, pode ser necessário associar um controle a um tipo, em vez de um objeto.</span><span class="sxs-lookup"><span data-stu-id="f828a-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="f828a-104">Geralmente é necessário associar um controle a um tipo no tempo de design, quando os dados podem não estar disponíveis, mas ainda é recomendável fazer com que os controles associados a dados exibam dados da interface pública de um tipo.</span><span class="sxs-lookup"><span data-stu-id="f828a-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="f828a-105">Os procedimentos a seguir demonstram como criar um novo <xref:System.Windows.Forms.BindingSource> associado a um tipo e como associar uma das propriedades do tipo à propriedade <xref:System.Windows.Forms.TextBox.Text%2A> de um <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f828a-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>

### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="f828a-106">Associar o BindingSource a um tipo</span><span class="sxs-lookup"><span data-stu-id="f828a-106">To bind the BindingSource to a type</span></span>

1. <span data-ttu-id="f828a-107">Criar um projeto de Windows Forms **(arquivo** > **novo** **projeto** de >  > **Visual C#**  ou **Visual Basic** > área de **trabalho clássica** > Windows Forms **aplicativo**).</span><span class="sxs-lookup"><span data-stu-id="f828a-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="f828a-108">No modo **design** , arraste um componente <xref:System.Windows.Forms.BindingSource> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="f828a-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>

3. <span data-ttu-id="f828a-109">Na janela **Propriedades** , clique na seta da propriedade <xref:System.Windows.Forms.BindingSource.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="f828a-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>

4. <span data-ttu-id="f828a-110">No **Editor de tipo de interface do usuário de DataSource**, clique em **Adicionar fonte de dados do projeto**.</span><span class="sxs-lookup"><span data-stu-id="f828a-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>

5. <span data-ttu-id="f828a-111">Na página **Escolher um tipo de fonte de dados**, selecione **Objeto** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f828a-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>

6. <span data-ttu-id="f828a-112">Selecione o tipo para associar a:</span><span class="sxs-lookup"><span data-stu-id="f828a-112">Select the type to bind to:</span></span>

    - <span data-ttu-id="f828a-113">Se o tipo ao qual você deseja associar está no projeto atual ou o assembly que contém o tipo já foi adicionado como uma referência, expanda os nós para localizar o tipo desejado e, em seguida, selecione-o.</span><span class="sxs-lookup"><span data-stu-id="f828a-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>

      <span data-ttu-id="f828a-114">\-ou-</span><span class="sxs-lookup"><span data-stu-id="f828a-114">\-or-</span></span>

    - <span data-ttu-id="f828a-115">Se o tipo ao qual você deseja associar estiver em outro assembly, não atualmente na lista de referências, clique em **Adicionar referência**e, em seguida, clique na guia **projetos** . Selecione o projeto que contém o objeto comercial desejado e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f828a-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="f828a-116">Este projeto será exibido na lista de assemblies, portanto é possível expandir os nós para encontrar o tipo desejado e, em seguida, selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="f828a-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>

      > [!NOTE]
      > <span data-ttu-id="f828a-117">Se você desejar associar a um tipo em uma estrutura ou assembly Microsoft, desmarque a caixa de seleção **Ocultar assemblies que começam com Microsoft ou System**.</span><span class="sxs-lookup"><span data-stu-id="f828a-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>

7. <span data-ttu-id="f828a-118">Clique em **Avançar**e em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="f828a-118">Click **Next**, and then click **Finish**.</span></span>

### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="f828a-119">Associar o controle ao BindingSource</span><span class="sxs-lookup"><span data-stu-id="f828a-119">To bind the control to the BindingSource</span></span>

1. <span data-ttu-id="f828a-120">Adicione um <xref:System.Windows.Forms.TextBox> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="f828a-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>

2. <span data-ttu-id="f828a-121">Na janela **Propriedades**, expanda o nó **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="f828a-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>

3. <span data-ttu-id="f828a-122">Clique na seta ao lado da propriedade <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="f828a-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

4. <span data-ttu-id="f828a-123">No **Editor de tipo de interface do usuário do DataSource**, expanda o nó para o <xref:System.Windows.Forms.BindingSource> adicionado anteriormente e selecione a propriedade do tipo vinculado que você deseja associar à propriedade <xref:System.Windows.Forms.TextBox.Text%2A> da <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f828a-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f828a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f828a-124">See also</span></span>

- [<span data-ttu-id="f828a-125">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="f828a-125">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="f828a-126">Como associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="f828a-126">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
- [<span data-ttu-id="f828a-127">Associar controles a dados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f828a-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
