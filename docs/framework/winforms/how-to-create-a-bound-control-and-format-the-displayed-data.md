---
title: Como criar um controle associado e formatar os dados exibidos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6088048ed27b2021e297494275f4e80f7c0cb681
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="fbcbb-102">Como criar um controle associado e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="fbcbb-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="fbcbb-103">Com a associação de dados do Windows Forms, você pode formatar os dados exibidos em um controle associado a dados usando a caixa de diálogo **Formatação e associação avançada**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbcbb-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fbcbb-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fbcbb-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="fbcbb-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="fbcbb-107">Associar um controle e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="fbcbb-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="fbcbb-108">Conecte-se a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="fbcbb-109">Para obter mais informações, consulte [Conectando a uma fonte de dados](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="fbcbb-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="fbcbb-110">No formulário, selecione o controle e abra a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="fbcbb-111">Expanda a propriedade **(DataBindings)** e, na caixa **(Advanced)**, clique no botão de reticências (![captura de tela do VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para exibir a caixa de diálogo **Formatação e associação avançada**, que tem uma lista completa de propriedades do controle.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="fbcbb-112">Selecione a propriedade que você deseja associar e, em seguida, clique na seta **Associação**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="fbcbb-113">Uma lista de fontes de dados disponíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="fbcbb-114">Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="fbcbb-115">Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="fbcbb-116">Clique no nome de um elemento que receberá a associação.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="fbcbb-117">Na caixa **Tipo de formato**, clique no formato que você deseja aplicar aos dados exibidos no controle.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="fbcbb-118">Em cada caso, você pode especificar o valor exibido no controle se a fonte de dados contém <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="fbcbb-119">Caso contrário, as opções variam um pouco, dependendo do tipo de formato escolhido.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="fbcbb-120">A tabela a seguir mostra os tipos e opções de formato.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="fbcbb-121">Tipo de formato</span><span class="sxs-lookup"><span data-stu-id="fbcbb-121">Format type</span></span>|<span data-ttu-id="fbcbb-122">Opção de formatação</span><span class="sxs-lookup"><span data-stu-id="fbcbb-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="fbcbb-123">Sem Formatação</span><span class="sxs-lookup"><span data-stu-id="fbcbb-123">No Formatting</span></span>|<span data-ttu-id="fbcbb-124">Nenhuma opção.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-124">No options.</span></span>|  
    |<span data-ttu-id="fbcbb-125">Numeric</span><span class="sxs-lookup"><span data-stu-id="fbcbb-125">Numeric</span></span>|<span data-ttu-id="fbcbb-126">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="fbcbb-127">Moeda</span><span class="sxs-lookup"><span data-stu-id="fbcbb-127">Currency</span></span>|<span data-ttu-id="fbcbb-128">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="fbcbb-129">Date Time</span><span class="sxs-lookup"><span data-stu-id="fbcbb-129">Date Time</span></span>|<span data-ttu-id="fbcbb-130">Selecione como a data e a hora devem ser exibidas selecionando um dos itens na caixa de seleção **Tipo**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="fbcbb-131">Científico</span><span class="sxs-lookup"><span data-stu-id="fbcbb-131">Scientific</span></span>|<span data-ttu-id="fbcbb-132">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="fbcbb-133">Personalizado</span><span class="sxs-lookup"><span data-stu-id="fbcbb-133">Custom</span></span>|<span data-ttu-id="fbcbb-134">Especifique uma cadeia de caracteres de formato personalizada usando.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="fbcbb-135">Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="fbcbb-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="fbcbb-136">**Observação:** não há garantias de que as cadeias de caracteres de formato personalizadas realização a viagem de ida e volta entre a fonte de dados e o controle associado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="fbcbb-137">Identificar o <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> evento para a associação e aplicar formatação personalizada no código de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="fbcbb-138">Clique em **OK** para fechar a caixa de diálogo **Formatação e associação avançada** e retornar para a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="fbcbb-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcbb-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbcbb-139">See Also</span></span>  
 [<span data-ttu-id="fbcbb-140">Como criar um controle associado simples em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="fbcbb-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="fbcbb-141">Validação da entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fbcbb-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="fbcbb-142">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fbcbb-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
