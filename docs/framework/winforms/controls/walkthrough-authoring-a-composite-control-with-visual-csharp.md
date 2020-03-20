---
title: 'Instruções passo a passo: criando um controle composto com o Visual C#'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546718"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="01392-102">Passo a passo: Autor de um Controle Composto com C\#</span><span class="sxs-lookup"><span data-stu-id="01392-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="01392-103">Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas.</span><span class="sxs-lookup"><span data-stu-id="01392-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="01392-104">Basicamente, um controle de composição é um componente com uma representação visual.</span><span class="sxs-lookup"><span data-stu-id="01392-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="01392-105">Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor.</span><span class="sxs-lookup"><span data-stu-id="01392-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="01392-106">Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles.</span><span class="sxs-lookup"><span data-stu-id="01392-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="01392-107">Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="01392-108">Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.</span><span class="sxs-lookup"><span data-stu-id="01392-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="01392-109">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="01392-109">Create the Project</span></span>

<span data-ttu-id="01392-110">Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="01392-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="01392-111">Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock</span><span class="sxs-lookup"><span data-stu-id="01392-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="01392-112">No Visual Studio, crie um novo projeto **da Biblioteca de Controle de Formulários do Windows** e nomeie-o **ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="01392-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="01392-113">O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão.</span><span class="sxs-lookup"><span data-stu-id="01392-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="01392-114">O namespace raiz é usado para qualificar os nomes dos componentes no assembly.</span><span class="sxs-lookup"><span data-stu-id="01392-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="01392-115">Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="01392-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="01392-116">No **Solution Explorer**, clique com o botão direito do **UserControl1.cs**e clique em **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="01392-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="01392-117">Altere o nome de arquivo para `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="01392-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="01392-118">Clique no botão **Sim** quando for perguntado se deseja renomear todas as referências ao elemento de código "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="01392-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="01392-119">Por padrão, um controle composto <xref:System.Windows.Forms.UserControl> herda da classe fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="01392-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="01392-120">A <xref:System.Windows.Forms.UserControl> classe fornece a funcionalidade exigida por todos os controles compostos e implementa métodos e propriedades padrão.</span><span class="sxs-lookup"><span data-stu-id="01392-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="01392-121">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="01392-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="01392-122">Adicionar controles e componentes do Windows ao controle composto</span><span class="sxs-lookup"><span data-stu-id="01392-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="01392-123">Uma interface visual é uma parte essencial do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="01392-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="01392-124">Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="01392-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="01392-125">Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="01392-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="01392-126">Para adicionar um Rótulo e um Temporizador ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="01392-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="01392-127">No **Solution Explorer,** clique com o botão **direito do ctlClock.cs**e clique em Exibir **Designer**.</span><span class="sxs-lookup"><span data-stu-id="01392-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="01392-128">Na **caixa de ferramentas,** expanda o nó **Controles comuns** e clique duas vezes em **Etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="01392-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="01392-129">Um <xref:System.Windows.Forms.Label> controle `label1` nomeado é adicionado ao seu controle na superfície do designer.</span><span class="sxs-lookup"><span data-stu-id="01392-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="01392-130">No designer, clique **em label1**.</span><span class="sxs-lookup"><span data-stu-id="01392-130">In the designer, click **label1**.</span></span> <span data-ttu-id="01392-131">Na janela Propriedades, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="01392-132">Propriedade</span><span class="sxs-lookup"><span data-stu-id="01392-132">Property</span></span>|<span data-ttu-id="01392-133">Altere para</span><span class="sxs-lookup"><span data-stu-id="01392-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="01392-134">**Nome**</span><span class="sxs-lookup"><span data-stu-id="01392-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="01392-135">**Texto**</span><span class="sxs-lookup"><span data-stu-id="01392-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="01392-136">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="01392-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="01392-137">**Fonte.Tamanho**</span><span class="sxs-lookup"><span data-stu-id="01392-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="01392-138">Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.</span><span class="sxs-lookup"><span data-stu-id="01392-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="01392-139">Porque <xref:System.Windows.Forms.Timer> a é um componente, ele não tem representação visual no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="01392-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="01392-140">Portanto, ele não aparece com os controles na superfície do designer, mas sim no **Component Designer** (uma bandeja na parte inferior da superfície do designer).</span><span class="sxs-lookup"><span data-stu-id="01392-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="01392-141">No **Designer de componentes,** clique em <xref:System.Windows.Forms.Timer.Interval%2A> **timer1**e, em seguida, defina a propriedade para e a `1000` <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="01392-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="01392-142">A <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a <xref:System.Windows.Forms.Timer> frequência com que o componente marca.</span><span class="sxs-lookup"><span data-stu-id="01392-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="01392-143">A cada tique de `timer1`, ele executa o código no evento `timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="01392-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="01392-144">O intervalo representa o número de milissegundos entre os tiques.</span><span class="sxs-lookup"><span data-stu-id="01392-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="01392-145">No **Component Designer**, **temporizador** de `timer1_Tick` dois `ctlClock`cliques1 para ir ao evento para .</span><span class="sxs-lookup"><span data-stu-id="01392-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="01392-146">Modifique o código para que ele fique parecido com o exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="01392-147">Lembre-se de alterar o modificador de acesso de `private` para `protected`.</span><span class="sxs-lookup"><span data-stu-id="01392-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="01392-148">Esse código fará com que a hora atual seja mostrada em `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="01392-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="01392-149">Como o intervalo de `timer1` foi definido como `1000`, esse evento ocorrerá a cada vários milhares de milissegundos, atualizando a hora atual a cada segundo.</span><span class="sxs-lookup"><span data-stu-id="01392-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="01392-150">Modifique o método para que ele seja substituível pela palavra-chave `virtual`.</span><span class="sxs-lookup"><span data-stu-id="01392-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="01392-151">Para obter mais informações, consulte a seção “Herdando de um controle de usuário” abaixo.</span><span class="sxs-lookup"><span data-stu-id="01392-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="01392-152">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="01392-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="01392-153">Adicionar propriedades ao controle composto</span><span class="sxs-lookup"><span data-stu-id="01392-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="01392-154">Seu controle de relógio <xref:System.Windows.Forms.Label> agora encapsula <xref:System.Windows.Forms.Timer> um controle e um componente, cada um com seu próprio conjunto de propriedades inerentes.</span><span class="sxs-lookup"><span data-stu-id="01392-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="01392-155">Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados.</span><span class="sxs-lookup"><span data-stu-id="01392-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="01392-156">No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.</span><span class="sxs-lookup"><span data-stu-id="01392-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="01392-157">Para adicionar uma propriedade ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="01392-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="01392-158">No **Solution Explorer,** clique com o botão **direito do ctlClock.cs**e clique em **'Exibir código '**.</span><span class="sxs-lookup"><span data-stu-id="01392-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="01392-159">O **Editor de Códigos** para o seu controle é aberto.</span><span class="sxs-lookup"><span data-stu-id="01392-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="01392-160">Localize a instrução `public partial class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="01392-161">Sob a chave de abertura (`{)`, digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="01392-162">Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.</span><span class="sxs-lookup"><span data-stu-id="01392-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="01392-163">Digite ou cole o seguinte código abaixo das declarações variáveis da etapa 2.</span><span class="sxs-lookup"><span data-stu-id="01392-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="01392-164">O código anterior cria duas propriedades personalizadas, `ClockForeColor` e `ClockBackColor`, disponíveis para os próximos usuários desse controle.</span><span class="sxs-lookup"><span data-stu-id="01392-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="01392-165">As instruções `get` e `set` fornecem armazenamento e recuperação do valor da propriedade, bem como o código para implementar a funcionalidade apropriada para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="01392-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="01392-166">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="01392-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="01392-167">Teste o Controle</span><span class="sxs-lookup"><span data-stu-id="01392-167">Test the Control</span></span>

<span data-ttu-id="01392-168">Controles não são aplicativos autônomos; eles devem ser hospedados em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="01392-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="01392-169">Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="01392-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="01392-170">Para obter mais informações, consulte [Como testar o comportamento em tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="01392-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="01392-171">Para testar o controle</span><span class="sxs-lookup"><span data-stu-id="01392-171">To test your control</span></span>

1. <span data-ttu-id="01392-172">Pressione **F5** para construir o projeto e execute seu controle no **contêiner de teste UserControl**.</span><span class="sxs-lookup"><span data-stu-id="01392-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="01392-173">Na grade de propriedades do contêiner de teste, localize a propriedade `ClockBackColor` e, em seguida, selecione a propriedade para exibir a paleta de cores.</span><span class="sxs-lookup"><span data-stu-id="01392-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="01392-174">Escolha uma cor clicando nela.</span><span class="sxs-lookup"><span data-stu-id="01392-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="01392-175">A cor da tela de fundo do controle é alterada para a cor selecionada.</span><span class="sxs-lookup"><span data-stu-id="01392-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="01392-176">Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.</span><span class="sxs-lookup"><span data-stu-id="01392-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="01392-177">Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="01392-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="01392-178">Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="01392-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="01392-179">Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.</span><span class="sxs-lookup"><span data-stu-id="01392-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="01392-180">Herdar de um controle composto</span><span class="sxs-lookup"><span data-stu-id="01392-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="01392-181">Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="01392-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="01392-182">O controle de composição agora pode ser usado como base para a criação de outros controles.</span><span class="sxs-lookup"><span data-stu-id="01392-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="01392-183">O processo de derivação de classe de uma classe base é chamado *herança*.</span><span class="sxs-lookup"><span data-stu-id="01392-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="01392-184">Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="01392-185">Esse controle será derivado de seu controle pai, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="01392-186">Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.</span><span class="sxs-lookup"><span data-stu-id="01392-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="01392-187">A primeira etapa na criação de um controle herdado é derivá-lo de seu pai.</span><span class="sxs-lookup"><span data-stu-id="01392-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="01392-188">Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.</span><span class="sxs-lookup"><span data-stu-id="01392-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="01392-189">Para criar o controle herdado</span><span class="sxs-lookup"><span data-stu-id="01392-189">To create the inherited control</span></span>

1. <span data-ttu-id="01392-190">No **Solution Explorer**, clique com o botão direito do mouse **ctlClockLib,** aponte para **Adicionar**e clique em Controle **do Usuário**.</span><span class="sxs-lookup"><span data-stu-id="01392-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="01392-191">A caixa de diálogo **Adicionar Novo Item** é aberta.</span><span class="sxs-lookup"><span data-stu-id="01392-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="01392-192">Selecione o modelo **Controle de Usuário Herdado**.</span><span class="sxs-lookup"><span data-stu-id="01392-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="01392-193">Na caixa **Nome**, digite `ctlAlarmClock.cs` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="01392-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="01392-194">A caixa de diálogo **Seletor de Herança** é exibida.</span><span class="sxs-lookup"><span data-stu-id="01392-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="01392-195">Em **Nome do Componente**, clique duas vezes em **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="01392-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="01392-196">No **Solution Explorer,** navegue pelos projetos atuais.</span><span class="sxs-lookup"><span data-stu-id="01392-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01392-197">Um arquivo chamado **ctlAlarmClock.cs** foi adicionado ao projeto atual.</span><span class="sxs-lookup"><span data-stu-id="01392-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="01392-198">Adicione as propriedades do alarme</span><span class="sxs-lookup"><span data-stu-id="01392-198">Add the Alarm Properties</span></span>

<span data-ttu-id="01392-199">As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="01392-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="01392-200">Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.</span><span class="sxs-lookup"><span data-stu-id="01392-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="01392-201">Para adicionar propriedades ao controle de composição</span><span class="sxs-lookup"><span data-stu-id="01392-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="01392-202">No **Solution Explorer,** clique com o botão direito do **mouse ctlAlarmClock**e clique **em Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="01392-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="01392-203">Localize a instrução `public class`.</span><span class="sxs-lookup"><span data-stu-id="01392-203">Locate the `public class` statement.</span></span> <span data-ttu-id="01392-204">Observe que o controle herda de `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="01392-205">Sob a chave de abertura (instrução `{)`, digite o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="01392-206">Adicionar à Interface Gráfica do Controle</span><span class="sxs-lookup"><span data-stu-id="01392-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="01392-207">O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado.</span><span class="sxs-lookup"><span data-stu-id="01392-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="01392-208">Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas.</span><span class="sxs-lookup"><span data-stu-id="01392-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="01392-209">Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição.</span><span class="sxs-lookup"><span data-stu-id="01392-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="01392-210">Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.</span><span class="sxs-lookup"><span data-stu-id="01392-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="01392-211">Para adicionar o controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="01392-211">To add the label control</span></span>

1. <span data-ttu-id="01392-212">No **Solution Explorer**, clique com o botão direito do mouse **ctlAlarmClock**e clique em Exibir **Designer**.</span><span class="sxs-lookup"><span data-stu-id="01392-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="01392-213">O designer de `ctlAlarmClock` é aberto na janela principal.</span><span class="sxs-lookup"><span data-stu-id="01392-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="01392-214">Clique na parte de exibição do controle e exiba a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="01392-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01392-215">Embora todas as propriedades sejam exibidas, elas ficam esmaecidas.</span><span class="sxs-lookup"><span data-stu-id="01392-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="01392-216">Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="01392-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="01392-217">Por padrão, os controles contidos em um controle de composição são `private` e suas propriedades não são acessíveis por nenhum meio.</span><span class="sxs-lookup"><span data-stu-id="01392-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01392-218">Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `public` ou `protected`.</span><span class="sxs-lookup"><span data-stu-id="01392-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="01392-219">Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.</span><span class="sxs-lookup"><span data-stu-id="01392-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="01392-220">Adicione <xref:System.Windows.Forms.Label> um controle ao seu controle composto.</span><span class="sxs-lookup"><span data-stu-id="01392-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="01392-221">Usando o mouse, <xref:System.Windows.Forms.Label> arraste o controle imediatamente abaixo da caixa de exibição.</span><span class="sxs-lookup"><span data-stu-id="01392-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="01392-222">Na janela Propriedades, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="01392-223">Propriedade</span><span class="sxs-lookup"><span data-stu-id="01392-223">Property</span></span>|<span data-ttu-id="01392-224">Configuração</span><span class="sxs-lookup"><span data-stu-id="01392-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="01392-225">**Nome**</span><span class="sxs-lookup"><span data-stu-id="01392-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="01392-226">**Texto**</span><span class="sxs-lookup"><span data-stu-id="01392-226">**Text**</span></span>|<span data-ttu-id="01392-227">**Alarme!**</span><span class="sxs-lookup"><span data-stu-id="01392-227">**Alarm!**</span></span>|
    |<span data-ttu-id="01392-228">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="01392-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="01392-229">**Visível**</span><span class="sxs-lookup"><span data-stu-id="01392-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="01392-230">Adicione a funcionalidade do alarme</span><span class="sxs-lookup"><span data-stu-id="01392-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="01392-231">Nos procedimentos anteriores, você adicionou propriedades e um controle que habilitarão a funcionalidade de alarme do controle de composição.</span><span class="sxs-lookup"><span data-stu-id="01392-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="01392-232">Neste procedimento, você adicionará um código para comparar a hora atual com a hora do alarme e, se forem iguais, elas piscarão um alarme.</span><span class="sxs-lookup"><span data-stu-id="01392-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="01392-233">Ao substituir o método `timer1_Tick` de `ctlClock` e adicionar um código adicional a ele, você estenderá a funcionalidade de `ctlAlarmClock` ao mesmo tempo que reterá todas as funcionalidades inerentes de `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="01392-234">Para substituir o método timer1_Tick de ctlClock</span><span class="sxs-lookup"><span data-stu-id="01392-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="01392-235">No **Editor de códigos**, localize a instrução `private bool blnAlarmSet;`.</span><span class="sxs-lookup"><span data-stu-id="01392-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="01392-236">Imediatamente abaixo dela, adicione a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="01392-237">No **Editor de códigos**, localize a chave de fechamento (`})` no final da classe.</span><span class="sxs-lookup"><span data-stu-id="01392-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="01392-238">Antes da chave, adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="01392-239">A adição desse código realiza várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="01392-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="01392-240">A instrução `override` direciona o controle a usar esse método em vez do método herdado do controle base.</span><span class="sxs-lookup"><span data-stu-id="01392-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="01392-241">Quando esse método é chamado, ele chama o método que substitui ao invocar a instrução `base.timer1_Tick`, garantindo que toda a funcionalidade incorporada no controle original seja reproduzida nesse controle.</span><span class="sxs-lookup"><span data-stu-id="01392-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="01392-242">Em seguida, ele executa um código adicional para incorporar a funcionalidade de alarme.</span><span class="sxs-lookup"><span data-stu-id="01392-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="01392-243">Um controle de rótulo intermitente será exibido quando o alarme for acionado.</span><span class="sxs-lookup"><span data-stu-id="01392-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="01392-244">O controle do despertador está quase concluído.</span><span class="sxs-lookup"><span data-stu-id="01392-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="01392-245">A única coisa que resta é implementar uma maneira de desligá-lo.</span><span class="sxs-lookup"><span data-stu-id="01392-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="01392-246">Para fazer isso, você adicionará um código ao método `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="01392-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="01392-247">Para implementar o método de desligamento</span><span class="sxs-lookup"><span data-stu-id="01392-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="01392-248">No **Solution Explorer,** clique com o botão **direito do ctlAlarmClock.cs**e clique em Exibir **Designer**.</span><span class="sxs-lookup"><span data-stu-id="01392-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="01392-249">O designer será aberto.</span><span class="sxs-lookup"><span data-stu-id="01392-249">The designer opens.</span></span>

2. <span data-ttu-id="01392-250">Adicione um botão no controle.</span><span class="sxs-lookup"><span data-stu-id="01392-250">Add a button to the control.</span></span> <span data-ttu-id="01392-251">Defina as propriedades do botão da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="01392-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="01392-252">Propriedade</span><span class="sxs-lookup"><span data-stu-id="01392-252">Property</span></span>|<span data-ttu-id="01392-253">Valor</span><span class="sxs-lookup"><span data-stu-id="01392-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="01392-254">**Nome**</span><span class="sxs-lookup"><span data-stu-id="01392-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="01392-255">**Texto**</span><span class="sxs-lookup"><span data-stu-id="01392-255">**Text**</span></span>|<span data-ttu-id="01392-256">**Desabilitar o alarme**</span><span class="sxs-lookup"><span data-stu-id="01392-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="01392-257">No designer, clique duas vezes em **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="01392-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="01392-258">O **Editor de Código** é aberto na linha `private void btnAlarmOff_Click`.</span><span class="sxs-lookup"><span data-stu-id="01392-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="01392-259">Modifique esse método para que ele fique parecido com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="01392-260">No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="01392-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="01392-261">Use o Controle Herdado em um formulário</span><span class="sxs-lookup"><span data-stu-id="01392-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="01392-262">Você pode testar seu controle herdado da mesma `ctlClock`forma que testou o controle de classe base: Pressione **F5** para construir o projeto e executar seu controle no **Contêiner de Teste UserControl**.</span><span class="sxs-lookup"><span data-stu-id="01392-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="01392-263">Para obter mais informações, consulte [Como testar o comportamento em tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="01392-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="01392-264">Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário.</span><span class="sxs-lookup"><span data-stu-id="01392-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="01392-265">Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner.</span><span class="sxs-lookup"><span data-stu-id="01392-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="01392-266">Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="01392-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="01392-267">Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="01392-268">Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.</span><span class="sxs-lookup"><span data-stu-id="01392-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="01392-269">Para criar e adicionar o controle a um formulário de teste</span><span class="sxs-lookup"><span data-stu-id="01392-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="01392-270">No **Solution Explorer**, clique com o botão direito do mouse **ctlClockLib**e clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="01392-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="01392-271">Adicione um novo projeto **de aplicativo de formulários** do Windows à solução e nomeie-o **teste**.</span><span class="sxs-lookup"><span data-stu-id="01392-271">Add a new **Windows Forms Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="01392-272">No **Solution Explorer,** clique com o botão direito do mouse no nó **Referências** para o projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="01392-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="01392-273">Clique em **Adicionar referência** para exibir a caixa de diálogo **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="01392-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="01392-274">Clique na guia rotulada como **Projetos**.</span><span class="sxs-lookup"><span data-stu-id="01392-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="01392-275">O projeto `ctlClockLib` estará listado em **Nome do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="01392-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="01392-276">Clique duas vezes no projeto para adicionar a referência ao projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="01392-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="01392-277">No **Solution Explorer,** clique com o botão direito do **mouse em Teste**e clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="01392-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="01392-278">Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="01392-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="01392-279">Clique duas vezes em **ctlAlarmClock** para adicionar uma cópia de `ctlAlarmClock` ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="01392-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="01392-280">Na **caixa de ferramentas**, localize e clique <xref:System.Windows.Forms.DateTimePicker> duas vezes em **DateTimePicker** para adicionar um controle ao seu formulário e, em seguida, adicione um <xref:System.Windows.Forms.Label> controle clicando duas vezes em **Etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="01392-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="01392-281">Use o mouse para posicionar os controles em um local conveniente do formulário.</span><span class="sxs-lookup"><span data-stu-id="01392-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="01392-282">Defina as propriedades desses controles conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="01392-283">Control</span><span class="sxs-lookup"><span data-stu-id="01392-283">Control</span></span>|<span data-ttu-id="01392-284">Propriedade</span><span class="sxs-lookup"><span data-stu-id="01392-284">Property</span></span>|<span data-ttu-id="01392-285">Valor</span><span class="sxs-lookup"><span data-stu-id="01392-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="01392-286">**Texto**</span><span class="sxs-lookup"><span data-stu-id="01392-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="01392-287">**Nome**</span><span class="sxs-lookup"><span data-stu-id="01392-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="01392-288">**Nome**</span><span class="sxs-lookup"><span data-stu-id="01392-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="01392-289">**Formato**</span><span class="sxs-lookup"><span data-stu-id="01392-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="01392-290">No designer, clique duas vezes em **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="01392-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="01392-291">O **Editor de Códigos** é aberto para `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="01392-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="01392-292">Modifique o código para que ele fique parecido com o mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="01392-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="01392-293">No **Solution Explorer,** clique com o botão direito do **mouse em Teste**e clique em Definir como Projeto **startup**.</span><span class="sxs-lookup"><span data-stu-id="01392-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="01392-294">No menu **Debug,** clique em **Iniciar depuração**.</span><span class="sxs-lookup"><span data-stu-id="01392-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="01392-295">O programa de teste é iniciado.</span><span class="sxs-lookup"><span data-stu-id="01392-295">The test program starts.</span></span> <span data-ttu-id="01392-296">Observe que o tempo atual `ctlAlarmClock` é atualizado no controle, e <xref:System.Windows.Forms.DateTimePicker> que o tempo de partida é mostrado no controle.</span><span class="sxs-lookup"><span data-stu-id="01392-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="01392-297">Clique <xref:System.Windows.Forms.DateTimePicker> no local onde os minutos da hora são exibidos.</span><span class="sxs-lookup"><span data-stu-id="01392-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="01392-298">Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="01392-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="01392-299">A hora da configuração do alarme é mostrada em `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="01392-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="01392-300">Aguarde até que a hora exibida atinja a hora de configuração do alarme.</span><span class="sxs-lookup"><span data-stu-id="01392-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="01392-301">Quando a hora exibida atingir a hora na qual o alarme está definido, o `lblAlarm` piscará.</span><span class="sxs-lookup"><span data-stu-id="01392-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="01392-302">Desligue o alarme clicando em `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="01392-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="01392-303">Agora você pode redefinir o alarme.</span><span class="sxs-lookup"><span data-stu-id="01392-303">You may now reset the alarm.</span></span>

<span data-ttu-id="01392-304">Este artigo abordou uma série de conceitos-chave.</span><span class="sxs-lookup"><span data-stu-id="01392-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="01392-305">Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição.</span><span class="sxs-lookup"><span data-stu-id="01392-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="01392-306">Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="01392-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="01392-307">Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.</span><span class="sxs-lookup"><span data-stu-id="01392-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="01392-308">Confira também</span><span class="sxs-lookup"><span data-stu-id="01392-308">See also</span></span>

- [<span data-ttu-id="01392-309">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="01392-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="01392-310">Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="01392-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="01392-311">Instruções passo a passo: herdando um controle dos Windows Forms com Visual C#</span><span class="sxs-lookup"><span data-stu-id="01392-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
