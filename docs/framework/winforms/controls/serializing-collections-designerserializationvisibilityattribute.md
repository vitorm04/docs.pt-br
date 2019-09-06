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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4fd1f1dc0c2c0ad9ae2009ed592e48b8eeaa2783
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373680"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a><span data-ttu-id="209f7-102">Passo a passo: Serializar coleções de tipos padrão</span><span class="sxs-lookup"><span data-stu-id="209f7-102">Walkthrough: Serialize collections of standard types</span></span>

<span data-ttu-id="209f7-103">Seus controles personalizados às vezes exporão uma coleção como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="209f7-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="209f7-104">Este tutorial demonstra como usar a <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> classe para controlar como uma coleção é serializada em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="209f7-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="209f7-105">Aplicar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor à sua propriedade de coleção garante que a propriedade será serializada.</span><span class="sxs-lookup"><span data-stu-id="209f7-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="209f7-106">Para copiar o código deste tópico como uma única listagem, confira [Como: Serialize coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="209f7-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="209f7-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="209f7-107">Prerequisites</span></span>

<span data-ttu-id="209f7-108">É necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="209f7-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="209f7-109">Criar um controle com uma coleção serializável</span><span class="sxs-lookup"><span data-stu-id="209f7-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="209f7-110">A primeira etapa é criar um controle que tem uma coleção serializável como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="209f7-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="209f7-111">Você pode editar o conteúdo dessa coleção usando o **Editor de Coleção**, acessível por meio da janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="209f7-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="209f7-112">No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="209f7-112">In Visual Studio, create a Windows Control Library project, and name it **SerializationDemoControlLib**.</span></span>

2. <span data-ttu-id="209f7-113">Renomeie `UserControl1` como `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="209f7-113">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="209f7-114">Para obter mais informações, consulte [renomear uma refatoração de símbolo de código](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="209f7-114">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="209f7-115">Na janela **Propriedades** , defina o valor da <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> Propriedade como **10**.</span><span class="sxs-lookup"><span data-stu-id="209f7-115">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to **10**.</span></span>

4. <span data-ttu-id="209f7-116">Coloque um <xref:System.Windows.Forms.TextBox> controle `SerializationDemoControl`no.</span><span class="sxs-lookup"><span data-stu-id="209f7-116">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="209f7-117">Selecione o controle <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="209f7-117">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="209f7-118">Na janela **Propriedades**, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="209f7-118">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="209f7-119">Propriedade</span><span class="sxs-lookup"><span data-stu-id="209f7-119">Property</span></span>|<span data-ttu-id="209f7-120">Altere para</span><span class="sxs-lookup"><span data-stu-id="209f7-120">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="209f7-121">**Multilinha**</span><span class="sxs-lookup"><span data-stu-id="209f7-121">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="209f7-122">**Encaixar**</span><span class="sxs-lookup"><span data-stu-id="209f7-122">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="209f7-123">**ScrollBars**</span><span class="sxs-lookup"><span data-stu-id="209f7-123">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="209f7-124">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="209f7-124">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="209f7-125">No **Editor de Códigos**, declare um campo de matriz de cadeia de caracteres chamado `stringsValue` em `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="209f7-125">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="209f7-126">Defina a propriedade `Strings` no `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="209f7-126">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="209f7-127">O <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor é usado para habilitar a serialização da coleção.</span><span class="sxs-lookup"><span data-stu-id="209f7-127">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="209f7-128">Pressione **F5** para compilar o projeto e executar o controle no **contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="209f7-128">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="209f7-129">Localize a propriedade **Strings** no <xref:System.Windows.Forms.PropertyGrid> do contêiner de **teste UserControl**.</span><span class="sxs-lookup"><span data-stu-id="209f7-129">Find the **Strings** property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="209f7-130">Selecione a propriedade **cadeias de caracteres** e, em![seguida, selecione as reticências (o botão de reticências (.](./media/visual-studio-ellipsis-button.png)..) no botão janela Propriedades do Visual Studio) para abrir o **Editor de coleção de cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="209f7-130">Select the **Strings** property, then select the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="209f7-131">Insira várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**.</span><span class="sxs-lookup"><span data-stu-id="209f7-131">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="209f7-132">Separe-os pressionando a tecla **Enter** no final de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="209f7-132">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="209f7-133">Clique em **OK** quando terminar de inserir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="209f7-133">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="209f7-134">As cadeias de caracteres digitadas <xref:System.Windows.Forms.TextBox> aparecem no `SerializationDemoControl`do.</span><span class="sxs-lookup"><span data-stu-id="209f7-134">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serialize-a-collection-property"></a><span data-ttu-id="209f7-135">Serializar uma propriedade de coleção</span><span class="sxs-lookup"><span data-stu-id="209f7-135">Serialize a collection property</span></span>

<span data-ttu-id="209f7-136">Para testar o comportamento de serialização do seu controle, coloque-o em um formulário e altere o conteúdo da coleção com o **Editor de Coleção**.</span><span class="sxs-lookup"><span data-stu-id="209f7-136">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="209f7-137">Você pode ver o estado da coleção serializada examinando um arquivo de designer especial no qual o **Designer de formulários do Windows** emite código.</span><span class="sxs-lookup"><span data-stu-id="209f7-137">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

1. <span data-ttu-id="209f7-138">Adicione um projeto de Aplicativos do Windows à solução.</span><span class="sxs-lookup"><span data-stu-id="209f7-138">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="209f7-139">Nomeie o projeto `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="209f7-139">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="209f7-140">Na **Caixa de Ferramentas**, localize a guia chamada **Componentes da SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="209f7-140">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="209f7-141">Nessa guia, você encontrará o `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="209f7-141">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="209f7-142">Para obter mais informações, confira [Passo a passo: Populando automaticamente a caixa de](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)ferramentas com componentes personalizados.</span><span class="sxs-lookup"><span data-stu-id="209f7-142">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="209f7-143">Coloque um `SerializationDemoControl` em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="209f7-143">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="209f7-144">Localize a propriedade `Strings` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="209f7-144">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="209f7-145">Clique na `Strings` Propriedade e, em seguida, clique![nas reticências (o botão de reticências (...) no](./media/visual-studio-ellipsis-button.png)botão janela Propriedades do Visual Studio.) para abrir o **Editor de coleção de cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="209f7-145">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="209f7-146">Digite várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**.</span><span class="sxs-lookup"><span data-stu-id="209f7-146">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="209f7-147">Separe-os pressionando **Enter** no final de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="209f7-147">Separate them by pressing **Enter** at the end of each string.</span></span> <span data-ttu-id="209f7-148">Clique em **OK** quando terminar de inserir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="209f7-148">Click **OK** when you are finished entering strings.</span></span>

    > [!NOTE]
    > <span data-ttu-id="209f7-149">As cadeias de caracteres digitadas <xref:System.Windows.Forms.TextBox> aparecem no `SerializationDemoControl`do.</span><span class="sxs-lookup"><span data-stu-id="209f7-149">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

6. <span data-ttu-id="209f7-150">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="209f7-150">In **Solution Explorer**, click the **Show All Files** button.</span></span>

7. <span data-ttu-id="209f7-151">Abra o nó **Form1**.</span><span class="sxs-lookup"><span data-stu-id="209f7-151">Open the **Form1** node.</span></span> <span data-ttu-id="209f7-152">Abaixo está um arquivo chamado **Form1.Designer.cs** ou **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="209f7-152">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="209f7-153">Este é o arquivo no qual o **Designer de Formulários do Windows** emite um código que representa o estado de tempo de design do formulário e seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="209f7-153">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="209f7-154">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="209f7-154">Open this file in the **Code Editor**.</span></span>

8. <span data-ttu-id="209f7-155">Abra a região chamada **Código gerado pelo Windows Form Designer** e localize a seção rotulada como **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="209f7-155">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="209f7-156">Sob esse rótulo está o código que representa o estado serializado do seu controle.</span><span class="sxs-lookup"><span data-stu-id="209f7-156">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="209f7-157">As cadeias de caracteres que você digitou na etapa 5 aparecem em uma atribuição para a propriedade `Strings`.</span><span class="sxs-lookup"><span data-stu-id="209f7-157">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="209f7-158">Os exemplos de código a C# seguir no e Visual Basic, mostram um código semelhante ao que você verá se tiver digitado as cadeias de caracteres "vermelho", "laranja" e "amarelo".</span><span class="sxs-lookup"><span data-stu-id="209f7-158">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. <span data-ttu-id="209f7-159">No **Editor de código**, altere o valor <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> de na `Strings` propriedade para <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="209f7-159">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. <span data-ttu-id="209f7-160">Recompile a solução e repita as etapas 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="209f7-160">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="209f7-161">Neste caso, o **Designer de Formulários do Windows** não emite nenhuma atribuição para a propriedade `Strings`.</span><span class="sxs-lookup"><span data-stu-id="209f7-161">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="209f7-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="209f7-162">Next steps</span></span>

<span data-ttu-id="209f7-163">Se você souber como serializar uma coleção de tipos padrão, considere integrar seus controles personalizados mais profundamente no ambiente de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="209f7-163">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="209f7-164">Os tópicos a seguir descrevem como aprimorar a integração do tempo de design de seus controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="209f7-164">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="209f7-165">[Arquitetura de tempo de design](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="209f7-165">[Design-Time Architecture](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="209f7-166">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="209f7-166">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="209f7-167">[Visão geral da serialização do designer](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="209f7-167">[Designer Serialization Overview](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="209f7-168">Passo a passo: Criando um controle de Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="209f7-168">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="209f7-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="209f7-169">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="209f7-170">Passo a passo: Populando automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="209f7-170">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
