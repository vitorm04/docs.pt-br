---
title: 'Como: criar um controle associado e formatar os dados exibidos'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 22ffdfcc1068dd546c8c07a481c9e21fb1faab80
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003724"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="232d2-102">Como: criar um controle associado e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="232d2-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="232d2-103">Com a associação de dados do Windows Forms, você pode formatar os dados exibidos em um controle associado a dados usando a caixa de diálogo **Formatação e associação avançada**.</span><span class="sxs-lookup"><span data-stu-id="232d2-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="232d2-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="232d2-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="232d2-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="232d2-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="232d2-106">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="232d2-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="232d2-107">Associar um controle e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="232d2-107">To bind a control and format the displayed data</span></span>  
  
1. <span data-ttu-id="232d2-108">Conecte-se a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="232d2-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="232d2-109">Para obter mais informações, consulte [Conectando a uma fonte de dados](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="232d2-109">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2. <span data-ttu-id="232d2-110">No formulário, selecione o controle e abra a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="232d2-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="232d2-111">Expanda o **(DataBindings)** propriedade e, em seguida, no **(Avançado)** , clique no botão de reticências (![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) Para exibir o **formatação e associação avançada** caixa de diálogo que tem uma lista completa de propriedades para o controle.</span><span class="sxs-lookup"><span data-stu-id="232d2-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4. <span data-ttu-id="232d2-112">Selecione a propriedade que você deseja associar e, em seguida, clique na seta **Associação**.</span><span class="sxs-lookup"><span data-stu-id="232d2-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="232d2-113">Uma lista de fontes de dados disponíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="232d2-113">A list of available data sources is displayed.</span></span>  
  
5. <span data-ttu-id="232d2-114">Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.</span><span class="sxs-lookup"><span data-stu-id="232d2-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="232d2-115">Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.</span><span class="sxs-lookup"><span data-stu-id="232d2-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6. <span data-ttu-id="232d2-116">Clique no nome de um elemento que receberá a associação.</span><span class="sxs-lookup"><span data-stu-id="232d2-116">Click the name of an element to bind to.</span></span>  
  
7. <span data-ttu-id="232d2-117">Na caixa **Tipo de formato**, clique no formato que você deseja aplicar aos dados exibidos no controle.</span><span class="sxs-lookup"><span data-stu-id="232d2-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="232d2-118">Em todos os casos, você pode especificar o valor exibido no controle se a fonte de dados contiver <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="232d2-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="232d2-119">Caso contrário, as opções variam um pouco, dependendo do tipo de formato escolhido.</span><span class="sxs-lookup"><span data-stu-id="232d2-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="232d2-120">A tabela a seguir mostra os tipos e opções de formato.</span><span class="sxs-lookup"><span data-stu-id="232d2-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="232d2-121">Tipo de formato</span><span class="sxs-lookup"><span data-stu-id="232d2-121">Format type</span></span>|<span data-ttu-id="232d2-122">Opção de formatação</span><span class="sxs-lookup"><span data-stu-id="232d2-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="232d2-123">Sem Formatação</span><span class="sxs-lookup"><span data-stu-id="232d2-123">No Formatting</span></span>|<span data-ttu-id="232d2-124">Nenhuma opção.</span><span class="sxs-lookup"><span data-stu-id="232d2-124">No options.</span></span>|  
    |<span data-ttu-id="232d2-125">Numeric</span><span class="sxs-lookup"><span data-stu-id="232d2-125">Numeric</span></span>|<span data-ttu-id="232d2-126">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="232d2-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="232d2-127">Moeda</span><span class="sxs-lookup"><span data-stu-id="232d2-127">Currency</span></span>|<span data-ttu-id="232d2-128">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="232d2-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="232d2-129">Date Time</span><span class="sxs-lookup"><span data-stu-id="232d2-129">Date Time</span></span>|<span data-ttu-id="232d2-130">Selecione como a data e a hora devem ser exibidas selecionando um dos itens na caixa de seleção **Tipo**.</span><span class="sxs-lookup"><span data-stu-id="232d2-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="232d2-131">Científico</span><span class="sxs-lookup"><span data-stu-id="232d2-131">Scientific</span></span>|<span data-ttu-id="232d2-132">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="232d2-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="232d2-133">Personalizado</span><span class="sxs-lookup"><span data-stu-id="232d2-133">Custom</span></span>|<span data-ttu-id="232d2-134">Especifique uma cadeia de caracteres de formato personalizada usando.</span><span class="sxs-lookup"><span data-stu-id="232d2-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="232d2-135">Para obter mais informações, consulte [Tipos de formatação](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="232d2-135">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="232d2-136">**Observação:**  Cadeias de caracteres de formato personalizado não têm garantia com êxito de ida e volta entre a fonte de dados e o controle associado.</span><span class="sxs-lookup"><span data-stu-id="232d2-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="232d2-137">Em vez disso, lidar com o <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> evento para a associação e aplicar formatação personalizada no código de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="232d2-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8. <span data-ttu-id="232d2-138">Clique em **OK** para fechar a caixa de diálogo **Formatação e associação avançada** e retornar para a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="232d2-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232d2-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="232d2-139">See also</span></span>

- [<span data-ttu-id="232d2-140">Como: Criar um controle associado simples em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="232d2-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="232d2-141">Validação da entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="232d2-141">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="232d2-142">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="232d2-142">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
