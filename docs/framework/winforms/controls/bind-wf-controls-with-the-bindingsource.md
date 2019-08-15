---
title: 'Como: Associar controles do Windows Forms ao componente BindingSource usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040027"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="3504b-102">Como: Associar controles do Windows Forms ao componente BindingSource usando o designer</span><span class="sxs-lookup"><span data-stu-id="3504b-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="3504b-103">Depois de adicionar controles ao formulário e determinar a interface do usuário para seu aplicativo, você pode associar os controles a uma fonte de dados, para que os usuários possam alterar e salvar dados relacionados ao aplicativo no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3504b-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>

 <span data-ttu-id="3504b-104">Associar um controle ou uma série de controles em Windows Forms é facilmente feito usando o <xref:System.Windows.Forms.BindingSource> controle como uma ponte entre os controles no formulário e a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3504b-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>

 <span data-ttu-id="3504b-105">Um ou mais controles em um formulário podem ser associados a dados; no procedimento a seguir, um <xref:System.Windows.Forms.TextBox> controle está associado a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3504b-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>

 <span data-ttu-id="3504b-106">Para concluir o procedimento, presume-se que você associará a uma fonte de dados derivada de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3504b-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="3504b-107">Para obter mais informações sobre como criar fontes de dados de outros armazenamentos de dados, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="3504b-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>

## <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="3504b-108">Associar um controle no tempo de design</span><span class="sxs-lookup"><span data-stu-id="3504b-108">To bind a control at design time</span></span>

1. <span data-ttu-id="3504b-109">Arraste um <xref:System.Windows.Forms.TextBox> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="3504b-109">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>

2. <span data-ttu-id="3504b-110">Na janela **Propriedades**:</span><span class="sxs-lookup"><span data-stu-id="3504b-110">In the **Properties** window:</span></span>

    1. <span data-ttu-id="3504b-111">Expanda o nó **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="3504b-111">Expand the **(DataBindings)** node.</span></span>

    2. <span data-ttu-id="3504b-112">Clique na seta ao lado da <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3504b-112">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

         <span data-ttu-id="3504b-113">O editor de tipo de interface do usuário **DataSource** abre.</span><span class="sxs-lookup"><span data-stu-id="3504b-113">The **DataSource** UI type editor opens.</span></span>

         <span data-ttu-id="3504b-114">Se uma fonte de dados tiver sido configurada anteriormente para o projeto ou formulário, ela será exibida.</span><span class="sxs-lookup"><span data-stu-id="3504b-114">If a data source has previously been configured for the project or form, it will appear.</span></span>

3. <span data-ttu-id="3504b-115">Clique em **Adicionar fonte de dados do projeto** para conectar aos dados e criar uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3504b-115">Click **Add Project Data Source** to connect to data and create a data source.</span></span>

4. <span data-ttu-id="3504b-116">Na página de boas-vindas do **Assistente de Configuração de Fonte de Dados**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3504b-116">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>

5. <span data-ttu-id="3504b-117">Na página **Escolher um tipo de fonte de dados**, selecione **Banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="3504b-117">On the **Choose a Data Source Type** page, select **Database**.</span></span>

6. <span data-ttu-id="3504b-118">Na página **Escolha sua conexão de dados**, selecione uma conexão de dados da lista de conexões disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3504b-118">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="3504b-119">Se a conexão de dados desejada não estiver disponível, selecione **Nova Conexão** para criar uma nova conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="3504b-119">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>

7. <span data-ttu-id="3504b-120">Selecione **Sim, salvar a conexão** para salvar a cadeia de conexão no arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3504b-120">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>

8. <span data-ttu-id="3504b-121">Selecione os objetos de banco de dados para trazer para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3504b-121">Select the database objects to bring into your application.</span></span> <span data-ttu-id="3504b-122">Nesse caso, selecione um campo em uma tabela que você deseja que o <xref:System.Windows.Forms.TextBox> exiba.</span><span class="sxs-lookup"><span data-stu-id="3504b-122">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>

9. <span data-ttu-id="3504b-123">Substitua o nome do conjunto de dados padrão, se quiser.</span><span class="sxs-lookup"><span data-stu-id="3504b-123">Replace the default dataset name if you want.</span></span>

10. <span data-ttu-id="3504b-124">Clique em **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="3504b-124">Click **Finish**.</span></span>

11. <span data-ttu-id="3504b-125">Na janela **Propriedades** , clique na seta ao lado da <xref:System.Windows.Forms.TextBox.Text%2A> Propriedade novamente.</span><span class="sxs-lookup"><span data-stu-id="3504b-125">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="3504b-126">No editor de tipo de interface do usuário do **DataSource** , selecione o nome do campo <xref:System.Windows.Forms.TextBox> ao qual associar o.</span><span class="sxs-lookup"><span data-stu-id="3504b-126">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>

     <span data-ttu-id="3504b-127">O editor de tipo de interface do usuário da **fonte** de <xref:System.Windows.Forms.BindingSource> dados é fechado e o conjunto e o adaptador de tabela específico para essa conexão de dados são adicionados ao formulário.</span><span class="sxs-lookup"><span data-stu-id="3504b-127">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>

## <a name="see-also"></a><span data-ttu-id="3504b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3504b-128">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="3504b-129">Adicionar novas fontes de dados</span><span class="sxs-lookup"><span data-stu-id="3504b-129">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="3504b-130">[Janela Fontes de Dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3504b-130">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
