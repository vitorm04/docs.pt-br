---
title: 'Instruções passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 297a7080b0c34fa10f976cbbbfb48d8c35786aca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458086"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Walkthrough: serializar coleções de tipos padrão

Seus controles personalizados às vezes exporão uma coleção como uma propriedade. Este tutorial demonstra como usar a classe <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> para controlar como uma coleção é serializada em tempo de design. Aplicar o valor de <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> à sua propriedade de coleção garante que a propriedade será serializada.

Para copiar o código neste tópico como uma lista única, consulte [Como serializar coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Prerequisites

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-a-control-with-a-serializable-collection"></a>Criar um controle com uma coleção serializável

A primeira etapa é criar um controle que tem uma coleção serializável como uma propriedade. Você pode editar o conteúdo dessa coleção usando o **Editor de Coleção**, acessível por meio da janela **Propriedades**.

1. No Visual Studio, crie um projeto de biblioteca de controle do Windows e nomeie-o **SerializationDemoControlLib**.

2. Renomeie `UserControl1` como `SerializationDemoControl`. Para obter mais informações, consulte [renomear uma refatoração de símbolo de código](/visualstudio/ide/reference/rename).

3. Na janela **Propriedades** , defina o valor da propriedade <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> como **10**.

4. Coloque um controle de <xref:System.Windows.Forms.TextBox> na `SerializationDemoControl`.

5. Selecione o controle <xref:System.Windows.Forms.TextBox>. Na janela **Propriedades**, defina as propriedades a seguir.

    |propriedade|Altere para|
    |--------------|---------------|
    |**Multilinha**|`true`|
    |**Encaixar**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. No **Editor de Códigos**, declare um campo de matriz de cadeia de caracteres chamado `stringsValue` em `SerializationDemoControl`.

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. Defina a propriedade `Strings` no `SerializationDemoControl`.

   > [!NOTE]
   > O valor de <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> é usado para habilitar a serialização da coleção.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Pressione **F5** para compilar o projeto e executar o controle no **contêiner de teste do UserControl**.

9. Localize a propriedade **Strings** no <xref:System.Windows.Forms.PropertyGrid> do contêiner de **teste UserControl**. Selecione a propriedade **cadeias de caracteres** e, em seguida, selecione as reticências (![botão de reticências (...) no botão janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png)) para abrir o **Editor de coleção de cadeias de caracteres**.

10. Insira várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**. Separe-os pressionando a tecla **Enter** no final de cada cadeia de caracteres. Clique em **OK** quando terminar de inserir cadeias de caracteres.

   > [!NOTE]
   > As cadeias de caracteres digitadas aparecem na <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.

## <a name="serialize-a-collection-property"></a>Serializar uma propriedade de coleção

Para testar o comportamento de serialização do seu controle, coloque-o em um formulário e altere o conteúdo da coleção com o **Editor de Coleção**. Você pode ver o estado da coleção serializada examinando um arquivo de designer especial no qual o **Designer de formulários do Windows** emite código.

1. Adicione um projeto de Aplicativos do Windows à solução. Nomeie o projeto `SerializationDemoControlTest`.

2. Na **Caixa de Ferramentas**, localize a guia chamada **Componentes da SerializationDemoControlLib**. Nessa guia, você encontrará o `SerializationDemoControl`. Para mais informações, consulte [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. Coloque um `SerializationDemoControl` em seu formulário.

4. Localize a propriedade `Strings` na janela **Propriedades**. Clique na propriedade `Strings` e, em seguida, clique nas reticências (![botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) para abrir o **Editor de coleção de cadeia de caracteres**.

5. Digite várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**. Separe-os pressionando **Enter** no final de cada cadeia de caracteres. Clique em **OK** quando terminar de inserir cadeias de caracteres.

    > [!NOTE]
    > As cadeias de caracteres digitadas aparecem na <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.

6. Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.

7. Abra o nó **Form1**. Abaixo está um arquivo chamado **Form1.Designer.cs** ou **Form1.Designer.vb**. Este é o arquivo no qual o **Designer de Formulários do Windows** emite um código que representa o estado de tempo de design do formulário e seus controles filho. Abra esse arquivo no **Editor de Códigos**.

8. Abra a região chamada **Código gerado pelo Windows Form Designer** e localize a seção rotulada como **serializationDemoControl1**. Sob esse rótulo está o código que representa o estado serializado do seu controle. As cadeias de caracteres que você digitou na etapa 5 aparecem em uma atribuição para a propriedade `Strings`. Os exemplos de código a C# seguir no e Visual Basic, mostram um código semelhante ao que você verá se tiver digitado as cadeias de caracteres "vermelho", "laranja" e "amarelo".

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. No **Editor de código**, altere o valor do <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na propriedade `Strings` para <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Recompile a solução e repita as etapas 3 e 4.

> [!NOTE]
> Neste caso, o **Designer de Formulários do Windows** não emite nenhuma atribuição para a propriedade `Strings`.

## <a name="next-steps"></a>Próximas etapas

Se você souber como serializar uma coleção de tipos padrão, considere integrar seus controles personalizados mais profundamente no ambiente de tempo de design. Os tópicos a seguir descrevem como aprimorar a integração do tempo de design de seus controles personalizados:

- [Arquitetura de tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Atributos em controles dos Windows Forms](attributes-in-windows-forms-controls.md)

- [Visão geral da serialização do designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Instruções passo a passo: criando um controle do Windows Forms que aproveita os recursos de tempo de design do Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
