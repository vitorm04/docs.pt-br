---
title: Como criar controles compostos
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 42ea424507b89576df8099fd4849dd2665135a55
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459430"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="d6795-102">Como: criar controles de composição</span><span class="sxs-lookup"><span data-stu-id="d6795-102">How to: Author composite controls</span></span>

<span data-ttu-id="d6795-103">Os controles de composição podem ser usados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="d6795-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="d6795-104">É possível criá-los como parte de um projeto de aplicativo da área de trabalho do Windows e usá-los somente em formulários do projeto.</span><span class="sxs-lookup"><span data-stu-id="d6795-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="d6795-105">Também é possível criá-los em um projeto da Biblioteca de Controles do Windows, compilar o projeto em um assembly e usar os controles em outros projetos.</span><span class="sxs-lookup"><span data-stu-id="d6795-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="d6795-106">Você pode até mesmo herdar deles e usar a herança visual para personalizá-los rapidamente para fins especiais.</span><span class="sxs-lookup"><span data-stu-id="d6795-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="d6795-107">Criar um controle de composição</span><span class="sxs-lookup"><span data-stu-id="d6795-107">To author a composite control</span></span>

1. <span data-ttu-id="d6795-108">No Visual Studio, crie um novo projeto de **aplicativo do Windows** e nomeie-o **DemoControlHost**.</span><span class="sxs-lookup"><span data-stu-id="d6795-108">In Visual Studio, create a new **Windows Application** project, and name it **DemoControlHost**.</span></span>

2. <span data-ttu-id="d6795-109">No menu **projeto** , clique em **Adicionar controle de usuário**.</span><span class="sxs-lookup"><span data-stu-id="d6795-109">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="d6795-110">Na caixa de diálogo **Adicionar Novo Item**, dê ao arquivo de classe (arquivo .vb ou .cs) o nome que você deseja que o controle de composição tenha.</span><span class="sxs-lookup"><span data-stu-id="d6795-110">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="d6795-111">Selecione o botão **Adicionar** para criar o arquivo de classe para o controle composto.</span><span class="sxs-lookup"><span data-stu-id="d6795-111">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="d6795-112">Adicione os controles da **Caixa de Ferramentas** à superfície do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="d6795-112">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="d6795-113">Coloque o código em procedimentos de evento, a fim de manipular eventos gerados pelo controle de composição ou por seus controles constituintes.</span><span class="sxs-lookup"><span data-stu-id="d6795-113">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="d6795-114">Feche o designer do controle de composição e salve o arquivo quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="d6795-114">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="d6795-115">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="d6795-115">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="d6795-116">O projeto deve ser criado para que os controles personalizados apareçam na **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d6795-116">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="d6795-117">Use a guia **DemoControlHost** da **Caixa de Ferramentas** para adicionar instâncias do controle ao `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d6795-117">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="d6795-118">Criar uma biblioteca de classes de controle</span><span class="sxs-lookup"><span data-stu-id="d6795-118">To author a control class library</span></span>

1. <span data-ttu-id="d6795-119">Abra um novo projeto da **Biblioteca de Controles do Windows**.</span><span class="sxs-lookup"><span data-stu-id="d6795-119">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="d6795-120">Por padrão, o projeto contém um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="d6795-120">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="d6795-121">Adicione controles e código, conforme descrito no procedimento acima.</span><span class="sxs-lookup"><span data-stu-id="d6795-121">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="d6795-122">Escolha um controle que as classes de herança não alterarão e defina a propriedade **Modificadores** desse controle como **Privada**.</span><span class="sxs-lookup"><span data-stu-id="d6795-122">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="d6795-123">Compile a DLL.</span><span class="sxs-lookup"><span data-stu-id="d6795-123">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="d6795-124">Herdar de um controle de composição em uma biblioteca de classes de controle</span><span class="sxs-lookup"><span data-stu-id="d6795-124">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="d6795-125">No menu **Arquivo**, aponte para **Adicionar** e selecione **Novo Projeto** para adicionar um novo projeto dos **Aplicativos do Windows** à solução.</span><span class="sxs-lookup"><span data-stu-id="d6795-125">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="d6795-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse na pasta **Referências** do novo projeto e escolha **Adicionar Referência** para abrir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="d6795-126">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="d6795-127">Selecione a guia **Projetos** e clique duas vezes no projete de biblioteca de controle.</span><span class="sxs-lookup"><span data-stu-id="d6795-127">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="d6795-128">No menu **Compilar**, clique em **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="d6795-128">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="d6795-129">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto de biblioteca de controle e selecione **Adicionar Novo Item** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="d6795-129">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="d6795-130">Selecione o modelo **Controle de Usuário Herdado** na caixa de diálogo **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="d6795-130">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="d6795-131">Na caixa de diálogo **Selecionador de Herança**, clique duas vezes no controle do qual você deseja herdar.</span><span class="sxs-lookup"><span data-stu-id="d6795-131">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="d6795-132">Um novo controle será adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d6795-132">A new control is added to your project.</span></span>

8. <span data-ttu-id="d6795-133">Abra o designer visual do novo controle e adicione outros controles constituintes.</span><span class="sxs-lookup"><span data-stu-id="d6795-133">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="d6795-134">É possível ver os controles constituintes que foram herdados do controle composição na DLL e alterar as propriedades de controles cuja propriedade **Modificadores** for **Pública**.</span><span class="sxs-lookup"><span data-stu-id="d6795-134">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="d6795-135">Não é possível alterar as propriedades do controle cuja propriedade **Modificadores** for **Privada**.</span><span class="sxs-lookup"><span data-stu-id="d6795-135">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6795-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6795-136">See also</span></span>

- [<span data-ttu-id="d6795-137">Walkthrough: Criando um controle composto</span><span class="sxs-lookup"><span data-stu-id="d6795-137">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="d6795-138">Walkthrough: herdar de um controle de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6795-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="d6795-139">Recomendações do Tipo de Controle</span><span class="sxs-lookup"><span data-stu-id="d6795-139">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="d6795-140">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6795-140">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="d6795-141">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="d6795-141">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
