---
title: 'Como: criar um controle associado e formatar os dados exibidos'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: b5ad85a9477ca32cd28f246abe4ece3cace43182
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666778"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="36181-102">Como: criar um controle associado e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="36181-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="36181-103">Com a associação de dados do Windows Forms, você pode formatar os dados exibidos em um controle associado a dados usando a caixa de diálogo **Formatação e associação avançada**.</span><span class="sxs-lookup"><span data-stu-id="36181-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>

### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="36181-104">Associar um controle e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="36181-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="36181-105">Conecte-se a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="36181-105">Connect to a data source.</span></span>

     <span data-ttu-id="36181-106">Para obter mais informações, consulte [Conectando a uma fonte de dados](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="36181-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="36181-107">No formulário, selecione o controle e abra a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="36181-107">In the form, select the control, and then open the Properties window.</span></span>

3. <span data-ttu-id="36181-108">Expanda a propriedade **(DataBindings)** e, em seguida, na caixa **(avançado)** , clique no botão![de reticências (o botão de reticências (...) na](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)janela Propriedades do Visual Studio.) para exibir a **formatação e avançado** Caixa de diálogo de associação, que tem uma lista completa de propriedades para esse controle.</span><span class="sxs-lookup"><span data-stu-id="36181-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="36181-109">Selecione a propriedade que você deseja associar e, em seguida, clique na seta **Associação**.</span><span class="sxs-lookup"><span data-stu-id="36181-109">Select the property you want to bind, and then click the **Binding** arrow.</span></span>

     <span data-ttu-id="36181-110">Uma lista de fontes de dados disponíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="36181-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="36181-111">Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.</span><span class="sxs-lookup"><span data-stu-id="36181-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="36181-112">Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.</span><span class="sxs-lookup"><span data-stu-id="36181-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="36181-113">Clique no nome de um elemento que receberá a associação.</span><span class="sxs-lookup"><span data-stu-id="36181-113">Click the name of an element to bind to.</span></span>

7. <span data-ttu-id="36181-114">Na caixa **Tipo de formato**, clique no formato que você deseja aplicar aos dados exibidos no controle.</span><span class="sxs-lookup"><span data-stu-id="36181-114">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="36181-115">Em todos os casos, você pode especificar o valor exibido no controle se a fonte de dados <xref:System.DBNull>contiver.</span><span class="sxs-lookup"><span data-stu-id="36181-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="36181-116">Caso contrário, as opções variam um pouco, dependendo do tipo de formato escolhido.</span><span class="sxs-lookup"><span data-stu-id="36181-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="36181-117">A tabela a seguir mostra os tipos e opções de formato.</span><span class="sxs-lookup"><span data-stu-id="36181-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="36181-118">Tipo de formato</span><span class="sxs-lookup"><span data-stu-id="36181-118">Format type</span></span>|<span data-ttu-id="36181-119">Opção de formatação</span><span class="sxs-lookup"><span data-stu-id="36181-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="36181-120">Sem Formatação</span><span class="sxs-lookup"><span data-stu-id="36181-120">No Formatting</span></span>|<span data-ttu-id="36181-121">Nenhuma opção.</span><span class="sxs-lookup"><span data-stu-id="36181-121">No options.</span></span>|
    |<span data-ttu-id="36181-122">Numeric</span><span class="sxs-lookup"><span data-stu-id="36181-122">Numeric</span></span>|<span data-ttu-id="36181-123">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="36181-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="36181-124">Moeda</span><span class="sxs-lookup"><span data-stu-id="36181-124">Currency</span></span>|<span data-ttu-id="36181-125">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="36181-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="36181-126">Date Time</span><span class="sxs-lookup"><span data-stu-id="36181-126">Date Time</span></span>|<span data-ttu-id="36181-127">Selecione como a data e a hora devem ser exibidas selecionando um dos itens na caixa de seleção **Tipo**.</span><span class="sxs-lookup"><span data-stu-id="36181-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="36181-128">Científico</span><span class="sxs-lookup"><span data-stu-id="36181-128">Scientific</span></span>|<span data-ttu-id="36181-129">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="36181-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="36181-130">Personalizado</span><span class="sxs-lookup"><span data-stu-id="36181-130">Custom</span></span>|<span data-ttu-id="36181-131">Especifique uma cadeia de caracteres de formato personalizada usando.</span><span class="sxs-lookup"><span data-stu-id="36181-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="36181-132">Para obter mais informações, consulte [Tipos de formatação](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="36181-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="36181-133">**Observação:**  Cadeias de caracteres de formato personalizado não têm garantia de ida e volta com êxito entre a fonte de dados e o controle ligado.</span><span class="sxs-lookup"><span data-stu-id="36181-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="36181-134">Em vez disso <xref:System.Windows.Forms.Binding.Parse> , <xref:System.Windows.Forms.Binding.Format> manipule o evento ou para a associação e aplique a formatação personalizada no código de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="36181-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="36181-135">Clique em **OK** para fechar a caixa de diálogo **Formatação e associação avançada** e retornar para a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="36181-135">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="36181-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36181-136">See also</span></span>

- [<span data-ttu-id="36181-137">Como: Criar um controle de associação simples em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="36181-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="36181-138">Validação da entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36181-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="36181-139">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36181-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
