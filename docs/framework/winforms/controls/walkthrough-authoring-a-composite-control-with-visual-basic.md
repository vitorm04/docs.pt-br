---
title: 'Passo a passo: Criar um controle composto com o Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: 6404e5933f886578b4ad8afd0d3da324541fc3f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299976"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="ebfa2-102">Passo a passo: Criar um controle composto com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebfa2-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="ebfa2-103">Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="ebfa2-104">Basicamente, um controle de composição é um componente com uma representação visual.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="ebfa2-105">Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="ebfa2-106">Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="ebfa2-107">Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="ebfa2-108">Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebfa2-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ebfa2-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ebfa2-111">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ebfa2-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ebfa2-112">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="ebfa2-112">Creating the Project</span></span>  
 <span data-ttu-id="ebfa2-113">Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="ebfa2-114">Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock</span><span class="sxs-lookup"><span data-stu-id="ebfa2-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1. <span data-ttu-id="ebfa2-115">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="ebfa2-116">Na lista de projetos do Visual Basic, selecione a **biblioteca de controle do Windows** modelo de projeto, digite `ctlClockLib` no **nome** caixa e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-116">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ebfa2-117">O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="ebfa2-118">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="ebfa2-119">Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="ebfa2-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3. <span data-ttu-id="ebfa2-120">No Gerenciador de Soluções, clique com o botão direito do mouse em **UserControl1.vb** e, em seguida, clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="ebfa2-121">Altere o nome de arquivo para `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="ebfa2-122">Clique no botão **Sim** quando solicitado se deseja renomear todas as referências ao elemento de código “UserControl1”.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebfa2-123">Por padrão, um controle de composição herda o <xref:System.Windows.Forms.UserControl> classe fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="ebfa2-124">O <xref:System.Windows.Forms.UserControl> classe fornece a funcionalidade requerida por todos os controles compostos e implementa propriedades e métodos padrão.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4. <span data-ttu-id="ebfa2-125">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="ebfa2-126">Adicionando controles e componentes do Windows ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="ebfa2-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="ebfa2-127">Uma interface visual é uma parte essencial do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="ebfa2-128">Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="ebfa2-129">Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="ebfa2-130">Para adicionar um Rótulo e um Temporizador ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="ebfa2-130">To add a Label and a Timer to your composite control</span></span>  
  
1. <span data-ttu-id="ebfa2-131">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.vb** e, em seguida, clique em **Exibir Designer**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2. <span data-ttu-id="ebfa2-132">Na Caixa de Ferramentas, expanda o nó **Controles Comuns** e clique duas vezes em **Rótulo**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="ebfa2-133">Um <xref:System.Windows.Forms.Label> controle chamado `Label1` é adicionado ao controle na superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3. <span data-ttu-id="ebfa2-134">No designer, clique em **Label1**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="ebfa2-135">Na janela Propriedades, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="ebfa2-136">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ebfa2-136">Property</span></span>|<span data-ttu-id="ebfa2-137">Altere para</span><span class="sxs-lookup"><span data-stu-id="ebfa2-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="ebfa2-138">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="ebfa2-139">**Texto**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="ebfa2-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="ebfa2-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-141">**Font.Size**</span></span>|`14`|  
  
4. <span data-ttu-id="ebfa2-142">Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="ebfa2-143">Porque um <xref:System.Windows.Forms.Timer> é um componente, ele não tem representação visual em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="ebfa2-144">Portanto, ele não é exibido com os controles na superfície do designer, mas no Designer de Componentes (uma bandeja na parte inferior da superfície do designer).</span><span class="sxs-lookup"><span data-stu-id="ebfa2-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5. <span data-ttu-id="ebfa2-145">No Designer de componente, clique em **Timer1**e, em seguida, defina o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade a ser `1000` e o <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade `True`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="ebfa2-146">O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a frequência de tiques do componente de temporizador.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="ebfa2-147">A cada tique de `Timer1`, ele executa o código no evento `Timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="ebfa2-148">O intervalo representa o número de milissegundos entre os tiques.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6. <span data-ttu-id="ebfa2-149">No Designer de Componentes, clique duas vezes em **Timer1** para acessar o evento `Timer1_Tick` de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7. <span data-ttu-id="ebfa2-150">Modifique o código para que ele fique parecido com o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="ebfa2-151">Lembre-se de alterar o modificador de acesso de `Private` para `Protected`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="ebfa2-152">Esse código fará com que a hora atual seja mostrada em `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="ebfa2-153">Como o intervalo de `Timer1` foi definido como `1000`, esse evento ocorrerá a cada vários milhares de milissegundos, atualizando a hora atual a cada segundo.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8. <span data-ttu-id="ebfa2-154">Modifique o método para que ele seja substituível.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-154">Modify the method to be overridable.</span></span> <span data-ttu-id="ebfa2-155">Para obter mais informações, consulte a seção “Herdando de um controle de usuário” abaixo.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="ebfa2-156">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="ebfa2-157">Adicionando propriedades ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="ebfa2-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="ebfa2-158">O controle do relógio agora encapsula uma <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.Timer> componente, cada um com seu próprio conjunto de propriedades inerentes.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="ebfa2-159">Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="ebfa2-160">No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="ebfa2-161">Para adicionar uma propriedade ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="ebfa2-161">To add a property to your composite control</span></span>  
  
1. <span data-ttu-id="ebfa2-162">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.vb** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="ebfa2-163">O Editor de Código do controle é aberto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-163">The Code Editor for your control opens.</span></span>  
  
2. <span data-ttu-id="ebfa2-164">Localize a instrução `Public Class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="ebfa2-165">Abaixo dela, digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="ebfa2-166">Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3. <span data-ttu-id="ebfa2-167">Insira o código a seguir abaixo das declarações de variáveis da etapa 2.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     <span data-ttu-id="ebfa2-168">O código anterior cria duas propriedades personalizadas, `ClockForeColor` e `ClockBackColor`, disponíveis para os próximos usuários desse controle com a invocação da instrução `Property`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="ebfa2-169">As instruções `Get` e `Set` fornecem armazenamento e recuperação do valor da propriedade, bem como o código para implementar a funcionalidade apropriada para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4. <span data-ttu-id="ebfa2-170">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="ebfa2-171">Testando o controle</span><span class="sxs-lookup"><span data-stu-id="ebfa2-171">Testing the Control</span></span>  
 <span data-ttu-id="ebfa2-172">Controles não são projetos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="ebfa2-173">Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="ebfa2-174">Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="ebfa2-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="ebfa2-175">Para testar o controle</span><span class="sxs-lookup"><span data-stu-id="ebfa2-175">To test your control</span></span>  
  
1. <span data-ttu-id="ebfa2-176">Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2. <span data-ttu-id="ebfa2-177">Na grade de propriedades do contêiner de teste, selecione a propriedade `ClockBackColor` e, em seguida, clique na seta suspensa para exibir a paleta de cores.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3. <span data-ttu-id="ebfa2-178">Escolha uma cor clicando nela.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="ebfa2-179">A cor da tela de fundo do controle é alterada para a cor selecionada.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-179">The background color of your control changes to the color you selected.</span></span>  
  
4. <span data-ttu-id="ebfa2-180">Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5. <span data-ttu-id="ebfa2-181">Clique em **Fechar** para fechar o **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="ebfa2-182">Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="ebfa2-183">Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="ebfa2-184">Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="ebfa2-185">Herdando de um controle de composição</span><span class="sxs-lookup"><span data-stu-id="ebfa2-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="ebfa2-186">Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="ebfa2-187">O controle de composição agora pode ser usado como base para a criação de outros controles.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="ebfa2-188">O processo de derivação de classe de uma classe base é chamado *herança*.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="ebfa2-189">Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="ebfa2-190">Esse controle será derivado de seu controle pai, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="ebfa2-191">Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="ebfa2-192">A primeira etapa na criação de um controle herdado é derivá-lo de seu pai.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="ebfa2-193">Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="ebfa2-194">Para criar o controle herdado</span><span class="sxs-lookup"><span data-stu-id="ebfa2-194">To create the inherited control</span></span>  
  
1. <span data-ttu-id="ebfa2-195">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib**, aponte para **Adicionar** e, em seguida, clique em **Controle de Usuário**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="ebfa2-196">A caixa de diálogo **Adicionar Novo Item** é aberta.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-196">The **Add New Item** dialog box opens.</span></span>  
  
2. <span data-ttu-id="ebfa2-197">Selecione o modelo **Controle de Usuário Herdado**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-197">Select the **Inherited User Control** template.</span></span>  
  
3. <span data-ttu-id="ebfa2-198">Na caixa **Nome**, digite `ctlAlarmClock.vb` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="ebfa2-199">A caixa de diálogo **Seletor de Herança** é exibida.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4. <span data-ttu-id="ebfa2-200">Em **Nome do Componente**, clique duas vezes em **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5. <span data-ttu-id="ebfa2-201">No Gerenciador de Soluções, procure os projetos atuais.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebfa2-202">Um arquivo chamado **ctlAlarmClock.vb** foi adicionado ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="ebfa2-203">Adicionando as propriedades de alarme</span><span class="sxs-lookup"><span data-stu-id="ebfa2-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="ebfa2-204">As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="ebfa2-205">Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="ebfa2-206">Para adicionar propriedades ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="ebfa2-206">To add properties to your composite control</span></span>  
  
1. <span data-ttu-id="ebfa2-207">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="ebfa2-208">Localize a declaração de classe do controle ctlAlarmClock, que aparece como `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="ebfa2-209">Na declaração de classe, insira o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-209">In the class declaration, insert the following code.</span></span>  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="ebfa2-210">Fazendo adições à interface gráfica do controle</span><span class="sxs-lookup"><span data-stu-id="ebfa2-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="ebfa2-211">O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="ebfa2-212">Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="ebfa2-213">Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="ebfa2-214">Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="ebfa2-215">Para adicionar o controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="ebfa2-215">To add the label control</span></span>  
  
1. <span data-ttu-id="ebfa2-216">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Designer**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="ebfa2-217">O designer de `ctlAlarmClock` é aberto na janela principal.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2. <span data-ttu-id="ebfa2-218">Clique em `lblDisplay` (a parte de exibição do controle) e exiba a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebfa2-219">Embora todas as propriedades sejam exibidas, elas ficam esmaecidas.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="ebfa2-220">Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="ebfa2-221">Por padrão, os controles contidos em um controle de composição são `Private` e suas propriedades não são acessíveis por nenhum meio.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebfa2-222">Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `Public` ou `Protected`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="ebfa2-223">Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3. <span data-ttu-id="ebfa2-224">Adicionar um <xref:System.Windows.Forms.Label> controle ao controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4. <span data-ttu-id="ebfa2-225">Usando o mouse, arraste o <xref:System.Windows.Forms.Label> controle imediatamente abaixo da caixa de exibição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="ebfa2-226">Na janela Propriedades, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="ebfa2-227">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ebfa2-227">Property</span></span>|<span data-ttu-id="ebfa2-228">Configuração</span><span class="sxs-lookup"><span data-stu-id="ebfa2-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="ebfa2-229">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="ebfa2-230">**Texto**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-230">**Text**</span></span>|<span data-ttu-id="ebfa2-231">**Alarme!**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="ebfa2-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="ebfa2-233">**Visível**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="ebfa2-234">Adicionando a funcionalidade de alarme</span><span class="sxs-lookup"><span data-stu-id="ebfa2-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="ebfa2-235">Nos procedimentos anteriores, você adicionou propriedades e um controle que habilitarão a funcionalidade de alarme do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="ebfa2-236">Neste procedimento, você adicionará um código para comparar a hora atual com a hora do alarme e, se forem iguais, elas soarão e piscarão um alarme.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="ebfa2-237">Ao substituir o método `Timer1_Tick` de `ctlClock` e adicionar um código adicional a ele, você estenderá a funcionalidade de `ctlAlarmClock` ao mesmo tempo que reterá todas as funcionalidades inerentes de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="ebfa2-238">Para substituir o método Timer1_Tick de ctlClock</span><span class="sxs-lookup"><span data-stu-id="ebfa2-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1. <span data-ttu-id="ebfa2-239">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock.vb** e, em seguida, clique em **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="ebfa2-240">Localize a instrução `Private blnAlarmSet As Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="ebfa2-241">Imediatamente abaixo dela, adicione a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3. <span data-ttu-id="ebfa2-242">Localize a instrução `End Class` na parte inferior da página.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="ebfa2-243">Logo antes da instrução `End Class`, adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-243">Just before the `End Class` statement, add the following code.</span></span>  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     <span data-ttu-id="ebfa2-244">A adição desse código realiza várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="ebfa2-245">A instrução `Overrides` direciona o controle a usar esse método em vez do método herdado do controle base.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="ebfa2-246">Quando esse método é chamado, ele chama o método que substitui ao invocar a instrução `MyBase.Timer1_Tick`, garantindo que toda a funcionalidade incorporada no controle original seja reproduzida nesse controle.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="ebfa2-247">Em seguida, ele executa um código adicional para incorporar a funcionalidade de alarme.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="ebfa2-248">Um controle de rótulo intermitente será exibido quando o alarme for acionado e um alarme sonoro audível será ouvido.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebfa2-249">Como você está substituindo um manipulador de eventos herdado, você não precisa especificar o evento com a palavra-chave `Handles`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="ebfa2-250">O evento já está vinculado.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-250">The event is already hooked up.</span></span> <span data-ttu-id="ebfa2-251">O que você está substituindo é a implementação do manipulador.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="ebfa2-252">O controle do despertador está quase concluído.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="ebfa2-253">A única coisa que resta é implementar uma maneira de desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="ebfa2-254">Para fazer isso, você adicionará um código ao método `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="ebfa2-255">Para implementar o método de desligamento</span><span class="sxs-lookup"><span data-stu-id="ebfa2-255">To implement the shutoff method</span></span>  
  
1. <span data-ttu-id="ebfa2-256">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock.vb** e, em seguida, clique em **Exibir Designer**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2. <span data-ttu-id="ebfa2-257">No designer, clique duas vezes em **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="ebfa2-258">O **Editor de Código** é aberto na linha `Private Sub lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3. <span data-ttu-id="ebfa2-259">Modifique esse método para que ele fique parecido com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4. <span data-ttu-id="ebfa2-260">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="ebfa2-261">Usando o controle herdado em um formulário</span><span class="sxs-lookup"><span data-stu-id="ebfa2-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="ebfa2-262">Você pode testar seu controle herdado da mesma maneira que você testou o controle de classe base, `ctlClock`: Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="ebfa2-263">Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="ebfa2-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="ebfa2-264">Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="ebfa2-265">Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="ebfa2-266">Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="ebfa2-267">Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="ebfa2-268">Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="ebfa2-269">Para criar e adicionar o controle a um formulário de teste</span><span class="sxs-lookup"><span data-stu-id="ebfa2-269">To build and add your control to a test form</span></span>  
  
1. <span data-ttu-id="ebfa2-270">No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib** e, em seguida, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2. <span data-ttu-id="ebfa2-271">No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3. <span data-ttu-id="ebfa2-272">Adicione um novo projeto **Aplicativo do Windows** à solução e nomeie-o `Test`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="ebfa2-273">O projeto **Teste** é adicionado ao Gerenciador de Soluções.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4. <span data-ttu-id="ebfa2-274">No Gerenciador de Soluções, clique com o botão direito do mouse no nó de projeto `Test` e, em seguida, clique em **Adicionar Referência** para exibir a caixa de diálogo **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5. <span data-ttu-id="ebfa2-275">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="ebfa2-276">O projeto **ctlClockLib** estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="ebfa2-277">Clique duas vezes em **ctlClockLib** para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6. <span data-ttu-id="ebfa2-278">No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7. <span data-ttu-id="ebfa2-279">Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8. <span data-ttu-id="ebfa2-280">Clique duas vezes em **ctlAlarmClock** para adicionar uma instância de `ctlAlarmClock` ao formulário.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="ebfa2-281">No **caixa de ferramentas**, localize e clique duas vezes em **DateTimePicker** para adicionar um <xref:System.Windows.Forms.DateTimePicker> controle ao seu formulário e, em seguida, adicione um <xref:System.Windows.Forms.Label> controle clicando duas vezes em **rótulo**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="ebfa2-282">Use o mouse para posicionar os controles em um local conveniente do formulário.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="ebfa2-283">Defina as propriedades desses controles conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="ebfa2-284">Controle</span><span class="sxs-lookup"><span data-stu-id="ebfa2-284">Control</span></span>|<span data-ttu-id="ebfa2-285">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ebfa2-285">Property</span></span>|<span data-ttu-id="ebfa2-286">Valor</span><span class="sxs-lookup"><span data-stu-id="ebfa2-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="ebfa2-287">**Texto**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="ebfa2-288">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="ebfa2-289">**Nome**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="ebfa2-290">**Formatar**</span><span class="sxs-lookup"><span data-stu-id="ebfa2-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="ebfa2-291">No designer, clique duas vezes em **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="ebfa2-292">O **Editor de Códigos** é aberto para `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="ebfa2-293">Modifique o código para que ele fique parecido com o mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="ebfa2-294">No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="ebfa2-295">No menu **Depuração**, clique em **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="ebfa2-296">O programa de teste é iniciado.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-296">The test program starts.</span></span> <span data-ttu-id="ebfa2-297">Observe que a hora atual é atualizada na `ctlAlarmClock` controle e que a hora de início é mostrada no <xref:System.Windows.Forms.DateTimePicker> controle.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="ebfa2-298">Clique o <xref:System.Windows.Forms.DateTimePicker> onde os minutos da hora são exibidos.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="ebfa2-299">Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="ebfa2-300">A hora da configuração do alarme é mostrada em `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="ebfa2-301">Aguarde até que a hora exibida atinja a hora de configuração do alarme.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="ebfa2-302">Quando a hora exibida atingir a hora na qual o alarme está definido, o alarme sonoro soará e `lblAlarm` piscará.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="ebfa2-303">Desligue o alarme clicando em `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="ebfa2-304">Agora você pode redefinir o alarme.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="ebfa2-305">Este passo a passo abordou alguns dos principais conceitos.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="ebfa2-306">Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="ebfa2-307">Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="ebfa2-308">Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.</span><span class="sxs-lookup"><span data-stu-id="ebfa2-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfa2-309">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebfa2-309">See also</span></span>

- [<span data-ttu-id="ebfa2-310">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="ebfa2-310">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="ebfa2-311">Como: Criar controles compostos</span><span class="sxs-lookup"><span data-stu-id="ebfa2-311">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="ebfa2-312">Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha</span><span class="sxs-lookup"><span data-stu-id="ebfa2-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
