---
title: 'Passo a passo: Serializando coleções de tipos padrão com a DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
ms.openlocfilehash: c8321f98b25026e32e7c69f7029f2c589d0567f7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211593"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="dbe47-102">Passo a passo: Serializando coleções de tipos padrão com a DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="dbe47-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>

<span data-ttu-id="dbe47-103">Seus controles personalizados às vezes exporão uma coleção como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="dbe47-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="dbe47-104">Este passo a passo demonstra como usar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> classe para controlar como uma coleção é serializada em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="dbe47-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="dbe47-105">Aplicando o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor à sua propriedade de coleção garante que a propriedade será serializada.</span><span class="sxs-lookup"><span data-stu-id="dbe47-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="dbe47-106">Para copiar o código deste tópico como uma única listagem, confira [Como: Serializar coleções de tipos padrão com DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="dbe47-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbe47-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dbe47-107">Prerequisites</span></span>

<span data-ttu-id="dbe47-108">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="dbe47-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="dbe47-109">Criar um controle com uma coleção serializável</span><span class="sxs-lookup"><span data-stu-id="dbe47-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="dbe47-110">A primeira etapa é criar um controle que tem uma coleção serializável como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="dbe47-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="dbe47-111">Você pode editar o conteúdo dessa coleção usando o **Editor de Coleção**, acessível por meio da janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="dbe47-112">No Visual Studio, crie um projeto de biblioteca de controle do Windows chamado `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-112">In Visual Studio, create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="dbe47-113">Para obter mais informações, consulte [Modelo de Biblioteca de Controle do Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dbe47-113">For more information, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="dbe47-114">Renomeie `UserControl1` como `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-114">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="dbe47-115">Para obter mais informações, consulte [um símbolo de código refatoração Renomear](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="dbe47-115">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="dbe47-116">No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> propriedade `10`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-116">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>

4. <span data-ttu-id="dbe47-117">Coloque um <xref:System.Windows.Forms.TextBox> no controlar o `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-117">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="dbe47-118">Selecione o <xref:System.Windows.Forms.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="dbe47-118">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="dbe47-119">Na janela **Propriedades**, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="dbe47-119">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="dbe47-120">Propriedade</span><span class="sxs-lookup"><span data-stu-id="dbe47-120">Property</span></span>|<span data-ttu-id="dbe47-121">Altere para</span><span class="sxs-lookup"><span data-stu-id="dbe47-121">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="dbe47-122">**Multilinha**</span><span class="sxs-lookup"><span data-stu-id="dbe47-122">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="dbe47-123">**Encaixar**</span><span class="sxs-lookup"><span data-stu-id="dbe47-123">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="dbe47-124">**ScrollBars**</span><span class="sxs-lookup"><span data-stu-id="dbe47-124">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="dbe47-125">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="dbe47-125">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="dbe47-126">No **Editor de Códigos**, declare um campo de matriz de cadeia de caracteres chamado `stringsValue` em `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-126">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="dbe47-127">Defina a propriedade `Strings` no `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-127">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="dbe47-128">O <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor é usado para habilitar a serialização da coleção.</span><span class="sxs-lookup"><span data-stu-id="dbe47-128">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="dbe47-129">Pressione **F5** para compilar o projeto e execute seu controle na **contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-129">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="dbe47-130">Localizar o `Strings` propriedade no <xref:System.Windows.Forms.PropertyGrid> da **contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-130">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="dbe47-131">Clique na propriedade `Strings` e, em seguida, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de conjunto de cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-131">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="dbe47-132">Insira várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-132">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="dbe47-133">Separá-los pressionando as **Enter** chave no final de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe47-133">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="dbe47-134">Clique em **OK** quando terminar de inserir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe47-134">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="dbe47-135">As cadeias de caracteres que você digitou aparecem na <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-135">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serializing-a-collection-property"></a><span data-ttu-id="dbe47-136">Serializando uma propriedade de coleção</span><span class="sxs-lookup"><span data-stu-id="dbe47-136">Serializing a Collection Property</span></span>

<span data-ttu-id="dbe47-137">Para testar o comportamento de serialização do seu controle, coloque-o em um formulário e altere o conteúdo da coleção com o **Editor de Coleção**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-137">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="dbe47-138">Você pode ver o estado da coleção serializada examinando um arquivo especial do designer no qual o **Designer de formulários do Windows** emite código.</span><span class="sxs-lookup"><span data-stu-id="dbe47-138">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

### <a name="to-serialize-a-collection"></a><span data-ttu-id="dbe47-139">Para serializar uma coleção</span><span class="sxs-lookup"><span data-stu-id="dbe47-139">To serialize a collection</span></span>

1. <span data-ttu-id="dbe47-140">Adicione um projeto de Aplicativos do Windows à solução.</span><span class="sxs-lookup"><span data-stu-id="dbe47-140">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="dbe47-141">Nomeie o projeto `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-141">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="dbe47-142">Na **Caixa de Ferramentas**, localize a guia chamada **Componentes da SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-142">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="dbe47-143">Nessa guia, você encontrará o `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-143">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="dbe47-144">Para obter mais informações, confira [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="dbe47-144">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="dbe47-145">Coloque um `SerializationDemoControl` em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="dbe47-145">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="dbe47-146">Localize a propriedade `Strings` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-146">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="dbe47-147">Clique na propriedade `Strings` e, em seguida, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de conjunto de cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-147">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="dbe47-148">Digite várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-148">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="dbe47-149">Separe-os pressionando a tecla ENTER no final de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe47-149">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="dbe47-150">Clique em **OK** quando terminar de inserir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe47-150">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="dbe47-151">As cadeias de caracteres que você digitou aparecem na <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-151">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

1. <span data-ttu-id="dbe47-152">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-152">In **Solution Explorer**, click the **Show All Files** button.</span></span>

2. <span data-ttu-id="dbe47-153">Abra o nó **Form1**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-153">Open the **Form1** node.</span></span> <span data-ttu-id="dbe47-154">Abaixo está um arquivo chamado **Form1.Designer.cs** ou **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-154">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="dbe47-155">Este é o arquivo no qual o **Designer de Formulários do Windows** emite um código que representa o estado de tempo de design do formulário e seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="dbe47-155">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="dbe47-156">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-156">Open this file in the **Code Editor**.</span></span>

3. <span data-ttu-id="dbe47-157">Abra a região chamada **Código gerado pelo Windows Form Designer** e localize a seção rotulada como **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-157">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="dbe47-158">Sob esse rótulo está o código que representa o estado serializado do seu controle.</span><span class="sxs-lookup"><span data-stu-id="dbe47-158">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="dbe47-159">As cadeias de caracteres que você digitou na etapa 5 aparecem em uma atribuição para a propriedade `Strings`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-159">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="dbe47-160">Os exemplos de código a seguir em c# e Visual Basic, mostrar o código semelhante ao que você verá se tiver digitado as cadeias de caracteres "vermelho", "orange" e "yellow".</span><span class="sxs-lookup"><span data-stu-id="dbe47-160">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

4. <span data-ttu-id="dbe47-161">No **Editor de códigos**, altere o valor da <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> no `Strings` propriedade para <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="dbe47-161">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

5. <span data-ttu-id="dbe47-162">Recompile a solução e repita as etapas 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="dbe47-162">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="dbe47-163">Neste caso, o **Designer de Formulários do Windows** não emite nenhuma atribuição para a propriedade `Strings`.</span><span class="sxs-lookup"><span data-stu-id="dbe47-163">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dbe47-164">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="dbe47-164">Next Steps</span></span>

<span data-ttu-id="dbe47-165">Se você souber como serializar uma coleção de tipos padrão, considere integrar seus controles personalizados mais profundamente no ambiente de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="dbe47-165">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="dbe47-166">Os tópicos a seguir descrevem como aprimorar a integração do tempo de design de seus controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="dbe47-166">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="dbe47-167">[Arquitetura de tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="dbe47-167">[Design-Time Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="dbe47-168">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dbe47-168">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="dbe47-169">[Visão geral da serialização do designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="dbe47-169">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="dbe47-170">Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dbe47-170">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="dbe47-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbe47-171">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- <span data-ttu-id="dbe47-172">[Visão geral da serialização do designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="dbe47-172">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>
- <span data-ttu-id="dbe47-173">[Como: Serializar coleções de tipos padrão com DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="dbe47-173">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
- [<span data-ttu-id="dbe47-174">Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="dbe47-174">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
