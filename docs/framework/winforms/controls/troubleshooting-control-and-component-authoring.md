---
title: Solucionando problemas de criação do controle e do componente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9ee9df41e6f0a4e37164760a2e40740e31530121
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459065"
---
# <a name="troubleshoot-control-and-component-authoring"></a><span data-ttu-id="79bb7-102">Solucionar problemas de criação de controle e de componente</span><span class="sxs-lookup"><span data-stu-id="79bb7-102">Troubleshoot Control and Component Authoring</span></span>

<span data-ttu-id="79bb7-103">Este tópico lista os seguintes problemas comuns que surgem ao desenvolver componentes e controles:</span><span class="sxs-lookup"><span data-stu-id="79bb7-103">This topic lists the following common problems that arise when developing components and controls:</span></span>

- <span data-ttu-id="79bb7-104">Não é possível adicionar o controle à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="79bb7-104">Cannot Add Control to Toolbox</span></span>

- <span data-ttu-id="79bb7-105">Não é possível depurar o componente nem o controle de usuário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79bb7-105">Cannot Debug the Windows Forms User Control or Component</span></span>

- <span data-ttu-id="79bb7-106">O evento é gerado duas vezes no componente ou no controle herdado</span><span class="sxs-lookup"><span data-stu-id="79bb7-106">Event Is Raised Twice in Inherited Control or Component</span></span>

- <span data-ttu-id="79bb7-107">Erro de tempo de design: "Falha em criar o componente '*Nome do Componente*'"</span><span class="sxs-lookup"><span data-stu-id="79bb7-107">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>

- <span data-ttu-id="79bb7-108">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="79bb7-108">STAThreadAttribute</span></span>

- <span data-ttu-id="79bb7-109">O ícone do componente não aparece na caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="79bb7-109">Component Icon Does Not Appear in Toolbox</span></span>

## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="79bb7-110">Não é possível adicionar o controle à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="79bb7-110">Cannot Add Control to Toolbox</span></span>

<span data-ttu-id="79bb7-111">Se você quiser adicionar um controle personalizado criado em outro projeto ou um controle de terceiros à **Caixa de Ferramentas**, faça isso manualmente.</span><span class="sxs-lookup"><span data-stu-id="79bb7-111">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="79bb7-112">Se o projeto atual contiver seu controle ou componente, ele deverá aparecer na **Caixa de Ferramentas** automaticamente.</span><span class="sxs-lookup"><span data-stu-id="79bb7-112">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="79bb7-113">Para mais informações, consulte [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="79bb7-113">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="79bb7-114">Para adicionar um controle à Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="79bb7-114">To add a control to the Toolbox</span></span>

1. <span data-ttu-id="79bb7-115">Clique com o botão direito do mouse em **Caixa de Ferramentas** e selecione **Escolher Itens** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="79bb7-115">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>

2. <span data-ttu-id="79bb7-116">Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, adicione o componente:</span><span class="sxs-lookup"><span data-stu-id="79bb7-116">In the **Choose Toolbox Items** dialog box, add the component:</span></span>

    - <span data-ttu-id="79bb7-117">Se você quiser adicionar um controle ou um componente do .NET Framework, clique na guia **Componentes do .NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-117">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>

         <span data-ttu-id="79bb7-118">– ou –</span><span class="sxs-lookup"><span data-stu-id="79bb7-118">– or –</span></span>

    - <span data-ttu-id="79bb7-119">Se você quiser adicionar um componente COM ou um controle ActiveX, clique na guia **Componentes COM**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-119">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>

3. <span data-ttu-id="79bb7-120">Se o controle estiver listado na caixa de diálogo, confirme que ele está selecionado e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-120">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>

     <span data-ttu-id="79bb7-121">O controle é adicionado à **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-121">The control is added to the **Toolbox**.</span></span>

4. <span data-ttu-id="79bb7-122">Se seu controle não estiver listado na caixa de diálogo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="79bb7-122">If your control is not listed in the dialog box, do the following:</span></span>

    1. <span data-ttu-id="79bb7-123">Clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-123">Click the **Browse** button.</span></span>

    2. <span data-ttu-id="79bb7-124">Navegue até a pasta que contém o arquivo .dll com o controle.</span><span class="sxs-lookup"><span data-stu-id="79bb7-124">Browse to the folder that contains the .dll file that contains your control.</span></span>

    3. <span data-ttu-id="79bb7-125">Selecione o arquivo .dll e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-125">Select the .dll file and click **Open**.</span></span>

         <span data-ttu-id="79bb7-126">Seu controle aparece na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="79bb7-126">Your control appears in the dialog box.</span></span>

    4. <span data-ttu-id="79bb7-127">Confirme que o controle está selecionado e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-127">Confirm that your control is selected, and then click **OK**.</span></span>

         <span data-ttu-id="79bb7-128">Seu controle é adicionado à **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-128">Your control is added to the **Toolbox**.</span></span>

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="79bb7-129">Não é possível depurar o componente nem o controle de usuário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="79bb7-129">Cannot Debug the Windows Forms User Control or Component</span></span>

<span data-ttu-id="79bb7-130">Se o seu controle derivar da classe <xref:System.Windows.Forms.UserControl>, você poderá depurar seu comportamento de tempo de execução com o contêiner de teste.</span><span class="sxs-lookup"><span data-stu-id="79bb7-130">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="79bb7-131">Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).</span><span class="sxs-lookup"><span data-stu-id="79bb7-131">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="79bb7-132">Outros controles e componentes personalizados não são projetos autônomos.</span><span class="sxs-lookup"><span data-stu-id="79bb7-132">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="79bb7-133">Eles devem ser hospedados por um aplicativo como um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="79bb7-133">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="79bb7-134">Para depurar um controle ou um componente, adicione-o a um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="79bb7-134">To debug a control or component, you must add it to a Windows Forms project.</span></span>

### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="79bb7-135">Para depurar um controle ou um componente</span><span class="sxs-lookup"><span data-stu-id="79bb7-135">To debug a control or component</span></span>

1. <span data-ttu-id="79bb7-136">No menu **Compilar**, clique em **Compilar Solução** para compilar sua solução.</span><span class="sxs-lookup"><span data-stu-id="79bb7-136">From the **Build** menu, click **Build Solution** to build your solution.</span></span>

2. <span data-ttu-id="79bb7-137">No menu **Arquivo**, escolha **Adicionar** e, em seguida, **Novo Projeto** para adicionar um projeto de teste ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79bb7-137">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>

3. <span data-ttu-id="79bb7-138">Na caixa de diálogo **Adicionar Novo Projeto**, escolha **Aplicativos do Windows** para o tipo de projeto.</span><span class="sxs-lookup"><span data-stu-id="79bb7-138">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>

4. <span data-ttu-id="79bb7-139">Em **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** para o novo projeto.</span><span class="sxs-lookup"><span data-stu-id="79bb7-139">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="79bb7-140">No menu de atalho, clique em **Adicionar Referência** para adicionar uma referência ao projeto que contém o controle ou o componente.</span><span class="sxs-lookup"><span data-stu-id="79bb7-140">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>

5. <span data-ttu-id="79bb7-141">Crie uma instância do seu controle ou componente no projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="79bb7-141">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="79bb7-142">Se o componente estiver na **Toolbox**, você poderá arrastá-lo para a superfície do designer ou criar a instância programaticamente, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="79bb7-142">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   <span data-ttu-id="79bb7-143">Agora você pode depurar seu componente ou controle como de costume.</span><span class="sxs-lookup"><span data-stu-id="79bb7-143">You can now debug your control or component as usual.</span></span>

<span data-ttu-id="79bb7-144">Para obter mais informações sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugger-feature-tour) e [Passo a passo: depurando personalizar controles personalizados do Windows Forms no tempo de design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="79bb7-144">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="79bb7-145">O evento é gerado duas vezes no componente ou no controle herdado</span><span class="sxs-lookup"><span data-stu-id="79bb7-145">Event Is Raised Twice in Inherited Control or Component</span></span>

<span data-ttu-id="79bb7-146">Isso provavelmente é devido a uma cláusula `Handles` duplicada.</span><span class="sxs-lookup"><span data-stu-id="79bb7-146">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="79bb7-147">Para obter mais informações, consulte [Solução de problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="79bb7-147">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="79bb7-148">Erro de tempo de design: "Falha em criar o componente 'Nome do Componente'"</span><span class="sxs-lookup"><span data-stu-id="79bb7-148">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>

<span data-ttu-id="79bb7-149">Seu componente ou controle deve fornecer um construtor sem parâmetros com nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="79bb7-149">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="79bb7-150">Quando o ambiente de design cria uma instância do seu componente ou controle, ele não tenta fornecer nenhum parâmetro para as sobrecargas do construtor que aceitam parâmetros.</span><span class="sxs-lookup"><span data-stu-id="79bb7-150">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>

## <a name="stathreadattribute"></a><span data-ttu-id="79bb7-151">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="79bb7-151">STAThreadAttribute</span></span>

<span data-ttu-id="79bb7-152">O <xref:System.STAThreadAttribute> informa o Common Language Runtime (CLR) que Windows Forms usa o modelo de apartamento de thread único.</span><span class="sxs-lookup"><span data-stu-id="79bb7-152">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="79bb7-153">Você poderá perceber um comportamento não intencional se não aplicar esse atributo ao método `Main` do aplicativo do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="79bb7-153">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="79bb7-154">Por exemplo, imagens de plano de fundo podem não aparecer para controles como <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="79bb7-154">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="79bb7-155">Alguns controles também podem exigir esse atributo para um comportamento correto de Preenchimento Automático e do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="79bb7-155">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>

## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="79bb7-156">O ícone do componente não aparece na caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="79bb7-156">Component Icon Does Not Appear in Toolbox</span></span>

<span data-ttu-id="79bb7-157">Quando você usa <xref:System.Drawing.ToolboxBitmapAttribute> para associar um ícone ao seu componente personalizado, o bitmap não aparece na caixa de ferramentas para componentes gerados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="79bb7-157">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="79bb7-158">Para ver o bitmap, recarregue o controle usando a caixa de diálogo **Escolher Itens da Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="79bb7-158">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="79bb7-159">Para obter mais informações, consulte [Como fornecer um bitmap da caixa de ferramentas para um controle](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="79bb7-159">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79bb7-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79bb7-160">See also</span></span>

- [<span data-ttu-id="79bb7-161">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="79bb7-161">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="79bb7-162">Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="79bb7-162">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="79bb7-163">Como testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="79bb7-163">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="79bb7-164">Passo a passo: depurando controles personalizados dos Windows Forms em tempo de Design</span><span class="sxs-lookup"><span data-stu-id="79bb7-164">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
