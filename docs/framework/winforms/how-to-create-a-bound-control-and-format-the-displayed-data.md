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
ms.openlocfilehash: 33d5491feccacba7f7b010b57e890ff7543a46f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="cf500-102">Como criar um controle associado e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="cf500-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="cf500-103">Com a associação de dados do Windows Forms, você pode formatar os dados exibidos em um controle associado a dados usando a caixa de diálogo **Formatação e associação avançada**.</span><span class="sxs-lookup"><span data-stu-id="cf500-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf500-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="cf500-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cf500-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="cf500-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cf500-106">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cf500-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="cf500-107">Associar um controle e formatar os dados exibidos</span><span class="sxs-lookup"><span data-stu-id="cf500-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="cf500-108">Conecte-se a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cf500-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="cf500-109">Para obter mais informações, consulte [Conectando a uma fonte de dados](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="cf500-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="cf500-110">No formulário, selecione o controle e abra a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="cf500-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="cf500-111">Expanda a propriedade **(DataBindings)** e, na caixa **(Advanced)**, clique no botão de reticências (![captura de tela do VisualStudioEllipsesButton](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para exibir a caixa de diálogo **Formatação e associação avançada**, que tem uma lista completa de propriedades do controle.</span><span class="sxs-lookup"><span data-stu-id="cf500-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="cf500-112">Selecione a propriedade que você deseja associar e, em seguida, clique na seta **Associação**.</span><span class="sxs-lookup"><span data-stu-id="cf500-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="cf500-113">Uma lista de fontes de dados disponíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="cf500-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="cf500-114">Expanda a fonte de dados a que deseja associar até encontrar o elemento de dados individual desejado.</span><span class="sxs-lookup"><span data-stu-id="cf500-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="cf500-115">Por exemplo, se você estiver associando a um valor de coluna na tabela do conjunto de dados, expanda o nome do conjunto de dados e o nome da tabela para exibir os nomes das colunas.</span><span class="sxs-lookup"><span data-stu-id="cf500-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="cf500-116">Clique no nome de um elemento que receberá a associação.</span><span class="sxs-lookup"><span data-stu-id="cf500-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="cf500-117">Na caixa **Tipo de formato**, clique no formato que você deseja aplicar aos dados exibidos no controle.</span><span class="sxs-lookup"><span data-stu-id="cf500-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="cf500-118">Em cada caso, você pode especificar o valor exibido no controle se a fonte de dados contém <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="cf500-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="cf500-119">Caso contrário, as opções variam um pouco, dependendo do tipo de formato escolhido.</span><span class="sxs-lookup"><span data-stu-id="cf500-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="cf500-120">A tabela a seguir mostra os tipos e opções de formato.</span><span class="sxs-lookup"><span data-stu-id="cf500-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="cf500-121">Tipo de formato</span><span class="sxs-lookup"><span data-stu-id="cf500-121">Format type</span></span>|<span data-ttu-id="cf500-122">Opção de formatação</span><span class="sxs-lookup"><span data-stu-id="cf500-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="cf500-123">Sem Formatação</span><span class="sxs-lookup"><span data-stu-id="cf500-123">No Formatting</span></span>|<span data-ttu-id="cf500-124">Nenhuma opção.</span><span class="sxs-lookup"><span data-stu-id="cf500-124">No options.</span></span>|  
    |<span data-ttu-id="cf500-125">Numeric</span><span class="sxs-lookup"><span data-stu-id="cf500-125">Numeric</span></span>|<span data-ttu-id="cf500-126">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="cf500-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="cf500-127">Moeda</span><span class="sxs-lookup"><span data-stu-id="cf500-127">Currency</span></span>|<span data-ttu-id="cf500-128">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="cf500-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="cf500-129">Date Time</span><span class="sxs-lookup"><span data-stu-id="cf500-129">Date Time</span></span>|<span data-ttu-id="cf500-130">Selecione como a data e a hora devem ser exibidas selecionando um dos itens na caixa de seleção **Tipo**.</span><span class="sxs-lookup"><span data-stu-id="cf500-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="cf500-131">Científico</span><span class="sxs-lookup"><span data-stu-id="cf500-131">Scientific</span></span>|<span data-ttu-id="cf500-132">Especifique o número de casas decimais usando o controle superior/inferior **Casas decimais**.</span><span class="sxs-lookup"><span data-stu-id="cf500-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="cf500-133">Personalizado</span><span class="sxs-lookup"><span data-stu-id="cf500-133">Custom</span></span>|<span data-ttu-id="cf500-134">Especifique uma cadeia de caracteres de formato personalizada usando.</span><span class="sxs-lookup"><span data-stu-id="cf500-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="cf500-135">Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="cf500-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="cf500-136">**Observação:** não há garantias de que as cadeias de caracteres de formato personalizadas realização a viagem de ida e volta entre a fonte de dados e o controle associado com êxito.</span><span class="sxs-lookup"><span data-stu-id="cf500-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="cf500-137">Identificar o <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> evento para a associação e aplicar formatação personalizada no código de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="cf500-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="cf500-138">Clique em **OK** para fechar a caixa de diálogo **Formatação e associação avançada** e retornar para a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="cf500-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf500-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf500-139">See Also</span></span>  
 [<span data-ttu-id="cf500-140">Como criar um controle associado simples em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="cf500-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="cf500-141">Validação da entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf500-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="cf500-142">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf500-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
