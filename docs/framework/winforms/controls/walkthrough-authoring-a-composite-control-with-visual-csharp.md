---
title: "Instruções passo a passo: criando um controle composto com o Visual C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d96705ed3f18c76a64c344ddec7a1cd4315e2e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="8397b-102">Instruções passo a passo: criando um controle composto com o Visual C#</span><span class="sxs-lookup"><span data-stu-id="8397b-102">Walkthrough: Authoring a Composite Control with Visual C#</span></span> #
<span data-ttu-id="8397b-103">Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas.</span><span class="sxs-lookup"><span data-stu-id="8397b-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="8397b-104">Basicamente, um controle de composição é um componente com uma representação visual.</span><span class="sxs-lookup"><span data-stu-id="8397b-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="8397b-105">Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor.</span><span class="sxs-lookup"><span data-stu-id="8397b-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="8397b-106">Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles.</span><span class="sxs-lookup"><span data-stu-id="8397b-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="8397b-107">Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="8397b-108">Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.</span><span class="sxs-lookup"><span data-stu-id="8397b-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8397b-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="8397b-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8397b-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="8397b-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8397b-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8397b-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8397b-112">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="8397b-112">Creating the Project</span></span>  
 <span data-ttu-id="8397b-113">Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="8397b-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="8397b-114">Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock</span><span class="sxs-lookup"><span data-stu-id="8397b-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="8397b-115">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="8397b-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="8397b-116">Na lista de projetos do [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], selecione o modelo de projeto **Biblioteca de Controles dos Windows Forms**, digite `ctlClockLib` na caixa **Nome** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="8397b-116">From the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8397b-117">O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="8397b-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="8397b-118">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="8397b-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="8397b-119">Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="8397b-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="8397b-120">No Gerenciador de Soluções, clique com o botão direito do mouse em **UserControl1.cs** e, em seguida, clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="8397b-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="8397b-121">Altere o nome de arquivo para `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="8397b-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="8397b-122">Clique no botão **Sim** quando solicitado se deseja renomear todas as referências ao elemento de código “UserControl1”.</span><span class="sxs-lookup"><span data-stu-id="8397b-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8397b-123">Por padrão, um controle composto herda o <xref:System.Windows.Forms.UserControl> classe fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="8397b-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="8397b-124">O <xref:System.Windows.Forms.UserControl> classe fornece funcionalidade requerida por todos os controles compostos e implementa os métodos padrão e propriedades.</span><span class="sxs-lookup"><span data-stu-id="8397b-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="8397b-125">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="8397b-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="8397b-126">Adicionando controles e componentes do Windows ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="8397b-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="8397b-127">Uma interface visual é uma parte essencial do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="8397b-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="8397b-128">Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="8397b-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="8397b-129">Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="8397b-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="8397b-130">Para adicionar um Rótulo e um Temporizador ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="8397b-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="8397b-131">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.cs** e, em seguida, clique em **Exibir Designer**.</span><span class="sxs-lookup"><span data-stu-id="8397b-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="8397b-132">Na **Caixa de Ferramentas**, expanda o nó **Controles Comuns** e clique duas vezes em **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="8397b-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="8397b-133">Um <xref:System.Windows.Forms.Label> controle chamado `label1` é adicionado ao seu controle na superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="8397b-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="8397b-134">No designer, clique em **label1**.</span><span class="sxs-lookup"><span data-stu-id="8397b-134">In the designer, click **label1**.</span></span> <span data-ttu-id="8397b-135">Na janela Propriedades, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="8397b-136">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8397b-136">Property</span></span>|<span data-ttu-id="8397b-137">Altere para</span><span class="sxs-lookup"><span data-stu-id="8397b-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="8397b-138">**Nome**</span><span class="sxs-lookup"><span data-stu-id="8397b-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="8397b-139">**Texto**</span><span class="sxs-lookup"><span data-stu-id="8397b-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="8397b-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="8397b-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="8397b-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="8397b-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="8397b-142">Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.</span><span class="sxs-lookup"><span data-stu-id="8397b-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="8397b-143">Porque um <xref:System.Windows.Forms.Timer> é um componente, ele não tem representação visual em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8397b-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="8397b-144">Portanto, ele não é exibido com os controles na superfície do designer, mas no **Designer de Componentes** (uma bandeja na parte inferior da superfície do designer).</span><span class="sxs-lookup"><span data-stu-id="8397b-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="8397b-145">No **Component Designer**, clique em **timer1**e, em seguida, defina o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade `1000` e o <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="8397b-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="8397b-146">O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a frequência com que o <xref:System.Windows.Forms.Timer> tiques do componente.</span><span class="sxs-lookup"><span data-stu-id="8397b-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="8397b-147">A cada tique de `timer1`, ele executa o código no evento `timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="8397b-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="8397b-148">O intervalo representa o número de milissegundos entre os tiques.</span><span class="sxs-lookup"><span data-stu-id="8397b-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="8397b-149">No **Designer de Componentes**, clique duas vezes em **timer1** para acessar o evento `timer1_Tick` de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="8397b-150">Modifique o código para que ele fique parecido com o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="8397b-151">Lembre-se de alterar o modificador de acesso de `private` para `protected`.</span><span class="sxs-lookup"><span data-stu-id="8397b-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="8397b-152">Esse código fará com que a hora atual seja mostrada em `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="8397b-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="8397b-153">Como o intervalo de `timer1` foi definido como `1000`, esse evento ocorrerá a cada vários milhares de milissegundos, atualizando a hora atual a cada segundo.</span><span class="sxs-lookup"><span data-stu-id="8397b-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="8397b-154">Modifique o método para que ele seja substituível pela palavra-chave `virtual`.</span><span class="sxs-lookup"><span data-stu-id="8397b-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="8397b-155">Para obter mais informações, consulte a seção “Herdando de um controle de usuário” abaixo.</span><span class="sxs-lookup"><span data-stu-id="8397b-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="8397b-156">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="8397b-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="8397b-157">Adicionando propriedades ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="8397b-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="8397b-158">O controle de relógio agora encapsula uma <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.Timer> componente, cada um com seu próprio conjunto de propriedades inerentes.</span><span class="sxs-lookup"><span data-stu-id="8397b-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="8397b-159">Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados.</span><span class="sxs-lookup"><span data-stu-id="8397b-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="8397b-160">No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.</span><span class="sxs-lookup"><span data-stu-id="8397b-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="8397b-161">Para adicionar uma propriedade ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="8397b-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="8397b-162">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.cs** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="8397b-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="8397b-163">O **Editor de Código** do controle é aberto.</span><span class="sxs-lookup"><span data-stu-id="8397b-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="8397b-164">Localize a instrução `public partial class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="8397b-165">Sob a chave de abertura (`{)`, digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="8397b-166">Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.</span><span class="sxs-lookup"><span data-stu-id="8397b-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="8397b-167">Digite o código a seguir abaixo das declarações de variáveis da etapa 2.</span><span class="sxs-lookup"><span data-stu-id="8397b-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     <span data-ttu-id="8397b-168">O código anterior cria duas propriedades personalizadas, `ClockForeColor` e `ClockBackColor`, disponíveis para os próximos usuários desse controle.</span><span class="sxs-lookup"><span data-stu-id="8397b-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="8397b-169">As instruções `get` e `set` fornecem armazenamento e recuperação do valor da propriedade, bem como o código para implementar a funcionalidade apropriada para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="8397b-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="8397b-170">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="8397b-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="8397b-171">Testando o controle</span><span class="sxs-lookup"><span data-stu-id="8397b-171">Testing the Control</span></span>  
 <span data-ttu-id="8397b-172">Controles não são aplicativos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="8397b-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="8397b-173">Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="8397b-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="8397b-174">Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).</span><span class="sxs-lookup"><span data-stu-id="8397b-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="8397b-175">Para testar o controle</span><span class="sxs-lookup"><span data-stu-id="8397b-175">To test your control</span></span>  
  
1.  <span data-ttu-id="8397b-176">Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="8397b-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="8397b-177">Na grade de propriedades do contêiner de teste, localize a propriedade `ClockBackColor` e, em seguida, selecione a propriedade para exibir a paleta de cores.</span><span class="sxs-lookup"><span data-stu-id="8397b-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="8397b-178">Escolha uma cor clicando nela.</span><span class="sxs-lookup"><span data-stu-id="8397b-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="8397b-179">A cor da tela de fundo do controle é alterada para a cor selecionada.</span><span class="sxs-lookup"><span data-stu-id="8397b-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="8397b-180">Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.</span><span class="sxs-lookup"><span data-stu-id="8397b-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="8397b-181">Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="8397b-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="8397b-182">Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="8397b-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="8397b-183">Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.</span><span class="sxs-lookup"><span data-stu-id="8397b-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="8397b-184">Herdando de um controle de composição</span><span class="sxs-lookup"><span data-stu-id="8397b-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="8397b-185">Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="8397b-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="8397b-186">O controle de composição agora pode ser usado como base para a criação de outros controles.</span><span class="sxs-lookup"><span data-stu-id="8397b-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="8397b-187">O processo de derivação de classe de uma classe base é chamado *herança*.</span><span class="sxs-lookup"><span data-stu-id="8397b-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="8397b-188">Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="8397b-189">Esse controle será derivado de seu controle pai, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="8397b-190">Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.</span><span class="sxs-lookup"><span data-stu-id="8397b-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="8397b-191">A primeira etapa na criação de um controle herdado é derivá-lo de seu pai.</span><span class="sxs-lookup"><span data-stu-id="8397b-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="8397b-192">Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.</span><span class="sxs-lookup"><span data-stu-id="8397b-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="8397b-193">Para criar o controle herdado</span><span class="sxs-lookup"><span data-stu-id="8397b-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="8397b-194">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib**, aponte para **Adicionar** e, em seguida, clique em **Controle de Usuário**.</span><span class="sxs-lookup"><span data-stu-id="8397b-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="8397b-195">A caixa de diálogo **Adicionar Novo Item** é aberta.</span><span class="sxs-lookup"><span data-stu-id="8397b-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="8397b-196">Selecione o modelo **Controle de Usuário Herdado**.</span><span class="sxs-lookup"><span data-stu-id="8397b-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="8397b-197">Na caixa **Nome**, digite `ctlAlarmClock.cs` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8397b-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="8397b-198">A caixa de diálogo **Seletor de Herança** é exibida.</span><span class="sxs-lookup"><span data-stu-id="8397b-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="8397b-199">Em **Nome do Componente**, clique duas vezes em **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="8397b-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="8397b-200">No Gerenciador de Soluções, procure os projetos atuais.</span><span class="sxs-lookup"><span data-stu-id="8397b-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8397b-201">Um arquivo chamado **ctlAlarmClock.cs** foi adicionado ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="8397b-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="8397b-202">Adicionando as propriedades de alarme</span><span class="sxs-lookup"><span data-stu-id="8397b-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="8397b-203">As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="8397b-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="8397b-204">Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.</span><span class="sxs-lookup"><span data-stu-id="8397b-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="8397b-205">Para adicionar propriedades ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="8397b-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="8397b-206">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="8397b-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="8397b-207">Localize a instrução `public class`.</span><span class="sxs-lookup"><span data-stu-id="8397b-207">Locate the `public class` statement.</span></span> <span data-ttu-id="8397b-208">Observe que o controle herda de `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="8397b-209">Sob a chave de abertura (instrução `{)`, digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="8397b-210">Fazendo adições à interface gráfica do controle</span><span class="sxs-lookup"><span data-stu-id="8397b-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="8397b-211">O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado.</span><span class="sxs-lookup"><span data-stu-id="8397b-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="8397b-212">Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas.</span><span class="sxs-lookup"><span data-stu-id="8397b-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="8397b-213">Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição.</span><span class="sxs-lookup"><span data-stu-id="8397b-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="8397b-214">Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.</span><span class="sxs-lookup"><span data-stu-id="8397b-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="8397b-215">Para adicionar o controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="8397b-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="8397b-216">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Designer**.</span><span class="sxs-lookup"><span data-stu-id="8397b-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="8397b-217">O designer de `ctlAlarmClock` é aberto na janela principal.</span><span class="sxs-lookup"><span data-stu-id="8397b-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="8397b-218">Clique na parte de exibição do controle e exiba a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="8397b-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8397b-219">Embora todas as propriedades sejam exibidas, elas ficam esmaecidas.</span><span class="sxs-lookup"><span data-stu-id="8397b-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="8397b-220">Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="8397b-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="8397b-221">Por padrão, os controles contidos em um controle de composição são `private` e suas propriedades não são acessíveis por nenhum meio.</span><span class="sxs-lookup"><span data-stu-id="8397b-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8397b-222">Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `public` ou `protected`.</span><span class="sxs-lookup"><span data-stu-id="8397b-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="8397b-223">Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.</span><span class="sxs-lookup"><span data-stu-id="8397b-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="8397b-224">Adicionar um <xref:System.Windows.Forms.Label> controle para o controle composto.</span><span class="sxs-lookup"><span data-stu-id="8397b-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="8397b-225">Usando o mouse, arraste o <xref:System.Windows.Forms.Label> controle imediatamente abaixo da caixa de exibição.</span><span class="sxs-lookup"><span data-stu-id="8397b-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="8397b-226">Na janela Propriedades, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="8397b-227">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8397b-227">Property</span></span>|<span data-ttu-id="8397b-228">Configuração</span><span class="sxs-lookup"><span data-stu-id="8397b-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="8397b-229">**Nome**</span><span class="sxs-lookup"><span data-stu-id="8397b-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="8397b-230">**Texto**</span><span class="sxs-lookup"><span data-stu-id="8397b-230">**Text**</span></span>|<span data-ttu-id="8397b-231">**Alarme!**</span><span class="sxs-lookup"><span data-stu-id="8397b-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="8397b-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="8397b-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="8397b-233">**Visível**</span><span class="sxs-lookup"><span data-stu-id="8397b-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="8397b-234">Adicionando a funcionalidade de alarme</span><span class="sxs-lookup"><span data-stu-id="8397b-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="8397b-235">Nos procedimentos anteriores, você adicionou propriedades e um controle que habilitarão a funcionalidade de alarme do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="8397b-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="8397b-236">Neste procedimento, você adicionará um código para comparar a hora atual com a hora do alarme e, se forem iguais, elas piscarão um alarme.</span><span class="sxs-lookup"><span data-stu-id="8397b-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="8397b-237">Ao substituir o método `timer1_Tick` de `ctlClock` e adicionar um código adicional a ele, você estenderá a funcionalidade de `ctlAlarmClock` ao mesmo tempo que reterá todas as funcionalidades inerentes de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="8397b-238">Para substituir o método timer1_Tick de ctlClock</span><span class="sxs-lookup"><span data-stu-id="8397b-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="8397b-239">No **Editor de códigos**, localize a instrução `private bool blnAlarmSet;`.</span><span class="sxs-lookup"><span data-stu-id="8397b-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="8397b-240">Imediatamente abaixo dela, adicione a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="8397b-241">No **Editor de códigos**, localize a chave de fechamento (`})` no final da classe.</span><span class="sxs-lookup"><span data-stu-id="8397b-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="8397b-242">Antes da chave, adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-242">Just before the brace, add the following code.</span></span>  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="8397b-243">A adição desse código realiza várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="8397b-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="8397b-244">A instrução `override` direciona o controle a usar esse método em vez do método herdado do controle base.</span><span class="sxs-lookup"><span data-stu-id="8397b-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="8397b-245">Quando esse método é chamado, ele chama o método que substitui ao invocar a instrução `base.timer1_Tick`, garantindo que toda a funcionalidade incorporada no controle original seja reproduzida nesse controle.</span><span class="sxs-lookup"><span data-stu-id="8397b-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="8397b-246">Em seguida, ele executa um código adicional para incorporar a funcionalidade de alarme.</span><span class="sxs-lookup"><span data-stu-id="8397b-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="8397b-247">Um controle de rótulo intermitente será exibido quando o alarme for acionado.</span><span class="sxs-lookup"><span data-stu-id="8397b-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="8397b-248">O controle do despertador está quase concluído.</span><span class="sxs-lookup"><span data-stu-id="8397b-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="8397b-249">A única coisa que resta é implementar uma maneira de desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="8397b-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="8397b-250">Para fazer isso, você adicionará um código ao método `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="8397b-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="8397b-251">Para implementar o método de desligamento</span><span class="sxs-lookup"><span data-stu-id="8397b-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="8397b-252">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock.cs** e, em seguida, clique em **Exibir Designer**.</span><span class="sxs-lookup"><span data-stu-id="8397b-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="8397b-253">O designer será aberto.</span><span class="sxs-lookup"><span data-stu-id="8397b-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="8397b-254">Adicione um botão no controle.</span><span class="sxs-lookup"><span data-stu-id="8397b-254">Add a button to the control.</span></span> <span data-ttu-id="8397b-255">Defina as propriedades do botão da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8397b-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="8397b-256">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8397b-256">Property</span></span>|<span data-ttu-id="8397b-257">Valor</span><span class="sxs-lookup"><span data-stu-id="8397b-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="8397b-258">**Nome**</span><span class="sxs-lookup"><span data-stu-id="8397b-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="8397b-259">**Texto**</span><span class="sxs-lookup"><span data-stu-id="8397b-259">**Text**</span></span>|<span data-ttu-id="8397b-260">**Desabilitar o alarme**</span><span class="sxs-lookup"><span data-stu-id="8397b-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="8397b-261">No designer, clique duas vezes em **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="8397b-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="8397b-262">O **Editor de Código** é aberto na linha `private void btnAlarmOff_Click`.</span><span class="sxs-lookup"><span data-stu-id="8397b-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="8397b-263">Modifique esse método para que ele fique parecido com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="8397b-264">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="8397b-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="8397b-265">Usando o controle herdado em um formulário</span><span class="sxs-lookup"><span data-stu-id="8397b-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="8397b-266">É possível testar o controle herdado da mesma maneira que você testou o controle de classe base, `ctlClock`: pressione F5 para compilar o projeto e execute o controle no **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="8397b-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="8397b-267">Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).</span><span class="sxs-lookup"><span data-stu-id="8397b-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="8397b-268">Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário.</span><span class="sxs-lookup"><span data-stu-id="8397b-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="8397b-269">Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner.</span><span class="sxs-lookup"><span data-stu-id="8397b-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="8397b-270">Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="8397b-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="8397b-271">Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="8397b-272">Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.</span><span class="sxs-lookup"><span data-stu-id="8397b-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="8397b-273">Para criar e adicionar o controle a um formulário de teste</span><span class="sxs-lookup"><span data-stu-id="8397b-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="8397b-274">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib** e, em seguida, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="8397b-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="8397b-275">Adicione um novo projeto **Aplicativo do Windows** à solução e nomeie-o `Test`.</span><span class="sxs-lookup"><span data-stu-id="8397b-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="8397b-276">Em Gerenciador de Soluções, clique com o botão direito do mouse no nó **Referências** para seu projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="8397b-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="8397b-277">Clique em **Adicionar referência** para exibir a caixa de diálogo **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="8397b-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="8397b-278">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="8397b-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="8397b-279">O projeto `ctlClockLib` estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="8397b-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="8397b-280">Clique duas vezes no projeto para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="8397b-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="8397b-281">No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="8397b-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="8397b-282">Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="8397b-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="8397b-283">Clique duas vezes em **ctlAlarmClock** para adicionar uma cópia de `ctlAlarmClock` ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="8397b-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="8397b-284">No **caixa de ferramentas**, localize e clique duas vezes em **DateTimePicker** para adicionar um <xref:System.Windows.Forms.DateTimePicker> o controle para o formulário e, em seguida, adicione um <xref:System.Windows.Forms.Label> controle clicando duas vezes em **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="8397b-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="8397b-285">Use o mouse para posicionar os controles em um local conveniente do formulário.</span><span class="sxs-lookup"><span data-stu-id="8397b-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="8397b-286">Defina as propriedades desses controles conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="8397b-287">Controle</span><span class="sxs-lookup"><span data-stu-id="8397b-287">Control</span></span>|<span data-ttu-id="8397b-288">Propriedade</span><span class="sxs-lookup"><span data-stu-id="8397b-288">Property</span></span>|<span data-ttu-id="8397b-289">Valor</span><span class="sxs-lookup"><span data-stu-id="8397b-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="8397b-290">**Texto**</span><span class="sxs-lookup"><span data-stu-id="8397b-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="8397b-291">**Nome**</span><span class="sxs-lookup"><span data-stu-id="8397b-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="8397b-292">**Nome**</span><span class="sxs-lookup"><span data-stu-id="8397b-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="8397b-293">**Formatar**</span><span class="sxs-lookup"><span data-stu-id="8397b-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="8397b-294">No designer, clique duas vezes em **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="8397b-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="8397b-295">O **Editor de Códigos** é aberto para `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="8397b-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="8397b-296">Modifique o código para que ele fique parecido com o mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="8397b-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="8397b-297">No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="8397b-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="8397b-298">No menu **Depuração**, clique em **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="8397b-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="8397b-299">O programa de teste é iniciado.</span><span class="sxs-lookup"><span data-stu-id="8397b-299">The test program starts.</span></span> <span data-ttu-id="8397b-300">Observe que a hora atual é atualizada no `ctlAlarmClock` controle e que a hora de início é mostrada no <xref:System.Windows.Forms.DateTimePicker> controle.</span><span class="sxs-lookup"><span data-stu-id="8397b-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="8397b-301">Clique o <xref:System.Windows.Forms.DateTimePicker> onde os minutos da hora são exibidos.</span><span class="sxs-lookup"><span data-stu-id="8397b-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="8397b-302">Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="8397b-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="8397b-303">A hora da configuração do alarme é mostrada em `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="8397b-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="8397b-304">Aguarde até que a hora exibida atinja a hora de configuração do alarme.</span><span class="sxs-lookup"><span data-stu-id="8397b-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="8397b-305">Quando a hora exibida atingir a hora na qual o alarme está definido, o `lblAlarm` piscará.</span><span class="sxs-lookup"><span data-stu-id="8397b-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="8397b-306">Desligue o alarme clicando em `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="8397b-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="8397b-307">Agora você pode redefinir o alarme.</span><span class="sxs-lookup"><span data-stu-id="8397b-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="8397b-308">Este passo a passo abordou alguns dos principais conceitos.</span><span class="sxs-lookup"><span data-stu-id="8397b-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="8397b-309">Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição.</span><span class="sxs-lookup"><span data-stu-id="8397b-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="8397b-310">Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="8397b-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="8397b-311">Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.</span><span class="sxs-lookup"><span data-stu-id="8397b-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8397b-312">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8397b-312">See Also</span></span>  
 [<span data-ttu-id="8397b-313">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="8397b-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="8397b-314">Programação com componentes</span><span class="sxs-lookup"><span data-stu-id="8397b-314">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="8397b-315">Instruções passo a passo para criação de componentes</span><span class="sxs-lookup"><span data-stu-id="8397b-315">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="8397b-316">Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="8397b-316">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="8397b-317">Passo a passo: herdando um controle dos Windows Forms com Visual C#</span><span class="sxs-lookup"><span data-stu-id="8397b-317">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
