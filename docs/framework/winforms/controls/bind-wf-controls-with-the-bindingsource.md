---
title: 'Como: Associar controles dos Windows Forms com o componente BindingSource usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 1a9baa5a602edd0ef91ef7dff5cdc42832bd7532
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633295"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="0c995-102">Como: Associar controles dos Windows Forms com o componente BindingSource usando o Designer</span><span class="sxs-lookup"><span data-stu-id="0c995-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="0c995-103">Depois de adicionar controles ao formulário e determinar a interface do usuário para seu aplicativo, você pode associar os controles a uma fonte de dados, para que os usuários possam alterar e salvar dados relacionados ao aplicativo no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0c995-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="0c995-104">Associação de um controle ou uma série de controles nos Windows Forms é feito com mais facilidade usando o <xref:System.Windows.Forms.BindingSource> controle como uma ponte entre os controles no formulário e a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0c995-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="0c995-105">Um ou mais controles em um formulário podem ser associados a dados; no procedimento a seguir, um <xref:System.Windows.Forms.TextBox> controle é associado a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0c995-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="0c995-106">Para concluir o procedimento, presume-se que você associará a uma fonte de dados derivada de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0c995-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="0c995-107">Para obter mais informações sobre como criar fontes de dados de outros armazenamentos de dados, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="0c995-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c995-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="0c995-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0c995-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="0c995-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0c995-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0c995-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="0c995-111">Associar um controle no tempo de design</span><span class="sxs-lookup"><span data-stu-id="0c995-111">To bind a control at design time</span></span>  
  
1.  <span data-ttu-id="0c995-112">Arraste um <xref:System.Windows.Forms.TextBox> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="0c995-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2.  <span data-ttu-id="0c995-113">Na janela **Propriedades**:</span><span class="sxs-lookup"><span data-stu-id="0c995-113">In the **Properties** window:</span></span>  
  
    1.  <span data-ttu-id="0c995-114">Expanda o nó **(DataBindings)**.</span><span class="sxs-lookup"><span data-stu-id="0c995-114">Expand the **(DataBindings)** node.</span></span>  
  
    2.  <span data-ttu-id="0c995-115">Clique na seta ao lado de <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0c995-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="0c995-116">O editor de tipo de interface do usuário **DataSource** abre.</span><span class="sxs-lookup"><span data-stu-id="0c995-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="0c995-117">Se uma fonte de dados tiver sido configurada anteriormente para o projeto ou formulário, ela será exibida.</span><span class="sxs-lookup"><span data-stu-id="0c995-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3.  <span data-ttu-id="0c995-118">Clique em **Adicionar fonte de dados do projeto** para conectar aos dados e criar uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0c995-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4.  <span data-ttu-id="0c995-119">Na página de boas-vindas do **Assistente de Configuração de Fonte de Dados**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0c995-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0c995-120">Na página **Escolher um tipo de fonte de dados**, selecione **Banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="0c995-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6.  <span data-ttu-id="0c995-121">Na página **Escolha sua conexão de dados**, selecione uma conexão de dados da lista de conexões disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0c995-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="0c995-122">Se a conexão de dados desejada não estiver disponível, selecione **Nova Conexão** para criar uma nova conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="0c995-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7.  <span data-ttu-id="0c995-123">Selecione **Sim, salvar a conexão** para salvar a cadeia de conexão no arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c995-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8.  <span data-ttu-id="0c995-124">Selecione os objetos de banco de dados para trazer para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c995-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="0c995-125">Nesse caso, selecione um campo em uma tabela que você gostaria de <xref:System.Windows.Forms.TextBox> para exibir.</span><span class="sxs-lookup"><span data-stu-id="0c995-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="0c995-126">Substitua o nome do conjunto de dados padrão, se quiser.</span><span class="sxs-lookup"><span data-stu-id="0c995-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="0c995-127">Clique em **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="0c995-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="0c995-128">No **propriedades** janela, clique na seta ao lado de <xref:System.Windows.Forms.TextBox.Text%2A> propriedade novamente.</span><span class="sxs-lookup"><span data-stu-id="0c995-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="0c995-129">No **fonte de dados** editor de tipo de interface do usuário, selecione o nome do campo a ser associado a <xref:System.Windows.Forms.TextBox> para.</span><span class="sxs-lookup"><span data-stu-id="0c995-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="0c995-130">O **fonte de dados** editor fecha e o conjunto de dados de tipo de interface do usuário <xref:System.Windows.Forms.BindingSource> e adaptador de tabela específica para que a conexão de dados são adicionados ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="0c995-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c995-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c995-131">See also</span></span>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="0c995-132">Adicionar novas fontes de dados</span><span class="sxs-lookup"><span data-stu-id="0c995-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- [<span data-ttu-id="0c995-133">Janela Fontes de Dados</span><span class="sxs-lookup"><span data-stu-id="0c995-133">Data Sources Window</span></span>](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
