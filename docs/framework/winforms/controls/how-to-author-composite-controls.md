---
title: Como criar controles compostos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 621d761411d5c33316d80e6dcdc9d0ec675242b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="baa1b-102">Como criar controles compostos</span><span class="sxs-lookup"><span data-stu-id="baa1b-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="baa1b-103">Os controles de composição podem ser usados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="baa1b-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="baa1b-104">É possível criá-los como parte de um projeto de aplicativo da área de trabalho do Windows e usá-los somente em formulários do projeto.</span><span class="sxs-lookup"><span data-stu-id="baa1b-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="baa1b-105">Também é possível criá-los em um projeto da Biblioteca de Controles do Windows, compilar o projeto em um assembly e usar os controles em outros projetos.</span><span class="sxs-lookup"><span data-stu-id="baa1b-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="baa1b-106">É possível até mesmo herdar deles e usar a herança visual para personalizá-los rapidamente para fins especiais.</span><span class="sxs-lookup"><span data-stu-id="baa1b-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baa1b-107">Caso queira criar um controle de composição para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="baa1b-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="baa1b-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="baa1b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="baa1b-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="baa1b-110">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="baa1b-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="baa1b-111">Criar um controle de composição</span><span class="sxs-lookup"><span data-stu-id="baa1b-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="baa1b-112">Abra um novo projeto de **Aplicativos do Windows** chamado `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="baa1b-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="baa1b-113">No menu **Projeto**, clique em **Adicionar Controle de Usuário**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-113">On the **Project**menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="baa1b-114">Na caixa de diálogo **Adicionar Novo Item**, dê ao arquivo de classe (arquivo .vb ou .cs) o nome que você deseja que o controle de composição tenha.</span><span class="sxs-lookup"><span data-stu-id="baa1b-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="baa1b-115">Clique no botão **Adicionar** para criar o arquivo de classe para o controle de composição.</span><span class="sxs-lookup"><span data-stu-id="baa1b-115">Click the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="baa1b-116">Adicione os controles da **Caixa de Ferramentas** à superfície do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="baa1b-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="baa1b-117">Coloque o código em procedimentos de evento, a fim de manipular eventos gerados pelo controle de composição ou por seus controles constituintes.</span><span class="sxs-lookup"><span data-stu-id="baa1b-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="baa1b-118">Feche o designer do controle de composição e salve o arquivo quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="baa1b-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="baa1b-119">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="baa1b-120">O projeto deve ser criado para que os controles personalizados apareçam na **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="baa1b-121">Use a guia **DemoControlHost** da **Caixa de Ferramentas** para adicionar instâncias do controle ao `Form1`.</span><span class="sxs-lookup"><span data-stu-id="baa1b-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="baa1b-122">Criar uma biblioteca de classes de controle</span><span class="sxs-lookup"><span data-stu-id="baa1b-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="baa1b-123">Abra um novo projeto da **Biblioteca de Controles do Windows**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="baa1b-124">Por padrão, o projeto contém um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="baa1b-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="baa1b-125">Adicione controles e código, conforme descrito no procedimento acima.</span><span class="sxs-lookup"><span data-stu-id="baa1b-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="baa1b-126">Escolha um controle que as classes de herança não alterarão e defina a propriedade **Modificadores** desse controle como **Privada**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="baa1b-127">Compile a DLL.</span><span class="sxs-lookup"><span data-stu-id="baa1b-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="baa1b-128">Herdar de um controle de composição em uma biblioteca de classes de controle</span><span class="sxs-lookup"><span data-stu-id="baa1b-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="baa1b-129">No menu **Arquivo**, aponte para **Adicionar** e selecione **Novo Projeto** para adicionar um novo projeto dos **Aplicativos do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="baa1b-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="baa1b-130">No **Gerenciador de Soluções**, clique com o botão direito do mouse na pasta **Referências** do novo projeto e escolha **Adicionar Referência** para abrir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="baa1b-131">Selecione a guia **Projetos** e clique duas vezes no projete de biblioteca de controle.</span><span class="sxs-lookup"><span data-stu-id="baa1b-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="baa1b-132">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="baa1b-133">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto de biblioteca de controle e selecione **Adicionar Novo Item** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="baa1b-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="baa1b-134">Selecione o modelo **Controle de Usuário Herdado** na caixa de diálogo **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="baa1b-135">Na caixa de diálogo **Selecionador de Herança**, clique duas vezes no controle do qual você deseja herdar.</span><span class="sxs-lookup"><span data-stu-id="baa1b-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="baa1b-136">Um novo controle será adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="baa1b-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="baa1b-137">Abra o designer visual do novo controle e adicione outros controles constituintes.</span><span class="sxs-lookup"><span data-stu-id="baa1b-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="baa1b-138">É possível ver os controles constituintes que foram herdados do controle composição na DLL e alterar as propriedades de controles cuja propriedade **Modificadores** for **Pública**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="baa1b-139">Não é possível alterar as propriedades do controle cuja propriedade **Modificadores** for **Privada**.</span><span class="sxs-lookup"><span data-stu-id="baa1b-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa1b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baa1b-140">See Also</span></span>  
 [<span data-ttu-id="baa1b-141">Passo a passo: criando um controle de composição com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="baa1b-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="baa1b-142">Passo a passo: criando um controle de composição com o Visual C#</span><span class="sxs-lookup"><span data-stu-id="baa1b-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="baa1b-143">Passo a passo: herdando um controle dos Windows Forms com Visual Basic</span><span class="sxs-lookup"><span data-stu-id="baa1b-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="baa1b-144">Passo a passo: herdando um controle dos Windows Forms com Visual C#</span><span class="sxs-lookup"><span data-stu-id="baa1b-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="baa1b-145">Recomendações do Tipo de Controle</span><span class="sxs-lookup"><span data-stu-id="baa1b-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="baa1b-146">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="baa1b-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="baa1b-147">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="baa1b-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
