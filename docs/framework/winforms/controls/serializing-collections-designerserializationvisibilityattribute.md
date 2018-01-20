---
title: "Instruções passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0267020f7e7a52e92b05a0bda0ee397e5c3393fc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="5034d-102">Instruções passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="5034d-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="5034d-103">Seus controles personalizados às vezes exporão uma coleção como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="5034d-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="5034d-104">Este passo a passo demonstra como usar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> classe para controlar como uma coleção é serializada em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="5034d-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="5034d-105">Aplicar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor para a propriedade de coleção garante que a propriedade será serializada.</span><span class="sxs-lookup"><span data-stu-id="5034d-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="5034d-106">Para copiar o código neste tópico como uma lista única, consulte [Como serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span><span class="sxs-lookup"><span data-stu-id="5034d-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5034d-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="5034d-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5034d-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5034d-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5034d-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5034d-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5034d-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5034d-110">Prerequisites</span></span>  
 <span data-ttu-id="5034d-111">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="5034d-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="5034d-112">Permissões suficientes para poder criar e executar projetos de aplicativos do Windows Forms no computador em que o Visual Studio está instalado.</span><span class="sxs-lookup"><span data-stu-id="5034d-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="5034d-113">Criando um controle que tem uma coleção serializável</span><span class="sxs-lookup"><span data-stu-id="5034d-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="5034d-114">A primeira etapa é criar um controle que tem uma coleção serializável como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="5034d-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="5034d-115">Você pode editar o conteúdo dessa coleção usando o **Editor de Coleção**, acessível por meio da janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5034d-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="5034d-116">Para criar um controle com uma coleção serializável</span><span class="sxs-lookup"><span data-stu-id="5034d-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="5034d-117">Crie um projeto de Biblioteca de Controle do Windows chamado `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="5034d-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="5034d-118">Para obter mais informações, consulte [Modelo de Biblioteca de Controle do Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="5034d-118">For more information, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="5034d-119">Renomeie `UserControl1` como `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="5034d-120">Para obter mais informações, consulte [Como renomear identificadores](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span><span class="sxs-lookup"><span data-stu-id="5034d-120">For more information, see [How to: Rename Identifiers](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span></span>  
  
3.  <span data-ttu-id="5034d-121">No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> propriedade `10`.</span><span class="sxs-lookup"><span data-stu-id="5034d-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="5034d-122">Coloque um <xref:System.Windows.Forms.TextBox> controlar o `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="5034d-123">Selecione o <xref:System.Windows.Forms.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5034d-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="5034d-124">Na janela **Propriedades**, defina as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="5034d-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="5034d-125">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5034d-125">Property</span></span>|<span data-ttu-id="5034d-126">Altere para</span><span class="sxs-lookup"><span data-stu-id="5034d-126">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="5034d-127">**Multilinha**</span><span class="sxs-lookup"><span data-stu-id="5034d-127">**Multiline**</span></span>|`true`|  
    |<span data-ttu-id="5034d-128">**Encaixar**</span><span class="sxs-lookup"><span data-stu-id="5034d-128">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |<span data-ttu-id="5034d-129">**ScrollBars**</span><span class="sxs-lookup"><span data-stu-id="5034d-129">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |<span data-ttu-id="5034d-130">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="5034d-130">**ReadOnly**</span></span>|`true`|  
  
6.  <span data-ttu-id="5034d-131">No **Editor de Códigos**, declare um campo de matriz de cadeia de caracteres chamado `stringsValue` em `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="5034d-132">Defina a propriedade `Strings` no `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5034d-133">O <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor é usado para habilitar a serialização da coleção.</span><span class="sxs-lookup"><span data-stu-id="5034d-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="5034d-134">Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="5034d-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="5034d-135">Localizar o `Strings` propriedade o <xref:System.Windows.Forms.PropertyGrid> do **contêiner de teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="5034d-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="5034d-136">Clique na propriedade `Strings` e, em seguida, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de conjunto de cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="5034d-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="5034d-137">Insira várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**.</span><span class="sxs-lookup"><span data-stu-id="5034d-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="5034d-138">Separe-os pressionando a tecla ENTER no final de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5034d-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="5034d-139">Clique em **OK** quando terminar de inserir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5034d-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5034d-140">As cadeias de caracteres que você digitou aparecem no <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="5034d-141">Serializando uma propriedade de coleção</span><span class="sxs-lookup"><span data-stu-id="5034d-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="5034d-142">Para testar o comportamento de serialização do seu controle, coloque-o em um formulário e altere o conteúdo da coleção com o **Editor de Coleção**.</span><span class="sxs-lookup"><span data-stu-id="5034d-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="5034d-143">Você pode ver o estado da coleção serializada examinando um arquivo especial do designer, no qual o **Designer de Formulários do Windows** emite código.</span><span class="sxs-lookup"><span data-stu-id="5034d-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="5034d-144">Para serializar uma coleção</span><span class="sxs-lookup"><span data-stu-id="5034d-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="5034d-145">Adicione um projeto de Aplicativos do Windows à solução.</span><span class="sxs-lookup"><span data-stu-id="5034d-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="5034d-146">Nomeie o projeto `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="5034d-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="5034d-147">Na **Caixa de Ferramentas**, localize a guia chamada **Componentes da SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="5034d-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="5034d-148">Nessa guia, você encontrará o `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="5034d-149">Para mais informações, consulte [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="5034d-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="5034d-150">Coloque um `SerializationDemoControl` em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="5034d-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="5034d-151">Localize a propriedade `Strings` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5034d-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="5034d-152">Clique na propriedade `Strings` e, em seguida, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de conjunto de cadeia de caracteres**.</span><span class="sxs-lookup"><span data-stu-id="5034d-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="5034d-153">Digite várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**.</span><span class="sxs-lookup"><span data-stu-id="5034d-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="5034d-154">Separe-os pressionando a tecla ENTER no final de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5034d-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="5034d-155">Clique em **OK** quando terminar de inserir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5034d-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5034d-156">As cadeias de caracteres que você digitou aparecem no <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5034d-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="5034d-157">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="5034d-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="5034d-158">Abra o nó **Form1**.</span><span class="sxs-lookup"><span data-stu-id="5034d-158">Open the **Form1** node.</span></span> <span data-ttu-id="5034d-159">Abaixo está um arquivo chamado **Form1.Designer.cs** ou **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="5034d-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="5034d-160">Este é o arquivo no qual o **Designer de Formulários do Windows** emite um código que representa o estado de tempo de design do formulário e seus controles filho.</span><span class="sxs-lookup"><span data-stu-id="5034d-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="5034d-161">Abra esse arquivo no **Editor de Códigos**.</span><span class="sxs-lookup"><span data-stu-id="5034d-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="5034d-162">Abra a região chamada **Código gerado pelo Windows Form Designer** e localize a seção rotulada como **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="5034d-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="5034d-163">Sob esse rótulo está o código que representa o estado serializado do seu controle.</span><span class="sxs-lookup"><span data-stu-id="5034d-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="5034d-164">As cadeias de caracteres que você digitou na etapa 5 aparecem em uma atribuição para a propriedade `Strings`.</span><span class="sxs-lookup"><span data-stu-id="5034d-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="5034d-165">Os seguintes exemplos de código em c# e Visual Basic, mostrar código semelhante ao que será exibido se você digitou a cadeias de caracteres "vermelho", "laranja" e "amarelo".</span><span class="sxs-lookup"><span data-stu-id="5034d-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="5034d-166">No **Editor de códigos**, alterar o valor da <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> no `Strings` propriedade <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="5034d-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="5034d-167">Recompile a solução e repita as etapas 3 e 4.</span><span class="sxs-lookup"><span data-stu-id="5034d-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5034d-168">Neste caso, o **Designer de Formulários do Windows** não emite nenhuma atribuição para a propriedade `Strings`.</span><span class="sxs-lookup"><span data-stu-id="5034d-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5034d-169">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5034d-169">Next Steps</span></span>  
 <span data-ttu-id="5034d-170">Se você souber como serializar uma coleção de tipos padrão, considere integrar seus controles personalizados mais profundamente no ambiente de tempo de design.</span><span class="sxs-lookup"><span data-stu-id="5034d-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="5034d-171">Os tópicos a seguir descrevem como aprimorar a integração do tempo de design de seus controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="5034d-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="5034d-172">Arquitetura de tempo de design</span><span class="sxs-lookup"><span data-stu-id="5034d-172">Design-Time Architecture</span></span>](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [<span data-ttu-id="5034d-173">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5034d-173">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="5034d-174">Visão geral da serialização do designer</span><span class="sxs-lookup"><span data-stu-id="5034d-174">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [<span data-ttu-id="5034d-175">Instruções passo a passo: criando um controle do Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5034d-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="5034d-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5034d-176">See Also</span></span>  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [<span data-ttu-id="5034d-177">Visão geral da serialização do designer</span><span class="sxs-lookup"><span data-stu-id="5034d-177">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [<span data-ttu-id="5034d-178">Como serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="5034d-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [<span data-ttu-id="5034d-179">Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="5034d-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
