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
ms.openlocfilehash: c113dcf814a252808ae3232751028947c26821ba
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614136"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>Passo a passo: Serializando coleções de tipos padrão com a DesignerSerializationVisibilityAttribute

Seus controles personalizados às vezes exporão uma coleção como uma propriedade. Este passo a passo demonstra como usar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> classe para controlar como uma coleção é serializada em tempo de design. Aplicando o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor à sua propriedade de coleção garante que a propriedade será serializada.

 Para copiar o código deste tópico como uma única listagem, confira [Como: Serializar coleções de tipos padrão com DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passo, você precisará de:

- Permissões suficientes para poder criar e executar projetos de aplicativos do Windows Forms no computador em que o Visual Studio está instalado.

## <a name="creating-a-control-that-has-a-serializable-collection"></a>Criando um controle que tem uma coleção serializável
 A primeira etapa é criar um controle que tem uma coleção serializável como uma propriedade. Você pode editar o conteúdo dessa coleção usando o **Editor de Coleção**, acessível por meio da janela **Propriedades**.

### <a name="to-create-a-control-with-a-serializable-collection"></a>Para criar um controle com uma coleção serializável

1. Crie um projeto de Biblioteca de Controle do Windows chamado `SerializationDemoControlLib`. Para obter mais informações, consulte [Modelo de Biblioteca de Controle do Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).

2. Renomeie `UserControl1` como `SerializationDemoControl`. Para obter mais informações, consulte [um símbolo de código refatoração Renomear](/visualstudio/ide/reference/rename).

3. No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> propriedade `10`.

4. Coloque um <xref:System.Windows.Forms.TextBox> no controlar o `SerializationDemoControl`.

5. Selecione o <xref:System.Windows.Forms.TextBox> controle. Na janela **Propriedades**, defina as propriedades a seguir.

    |Propriedade|Altere para|
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
> O <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valor é usado para habilitar a serialização da coleção.

 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

1. Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.

2. Localizar o `Strings` propriedade no <xref:System.Windows.Forms.PropertyGrid> da **contêiner de teste de UserControl**. Clique na propriedade `Strings` e, em seguida, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de conjunto de cadeia de caracteres**.

3. Insira várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**. Separe-os pressionando a tecla ENTER no final de cada cadeia de caracteres. Clique em **OK** quando terminar de inserir cadeias de caracteres.

> [!NOTE]
> As cadeias de caracteres que você digitou aparecem na <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.

## <a name="serializing-a-collection-property"></a>Serializando uma propriedade de coleção

Para testar o comportamento de serialização do seu controle, coloque-o em um formulário e altere o conteúdo da coleção com o **Editor de Coleção**. Você pode ver o estado da coleção serializada examinando um arquivo especial do designer, no qual o **Designer de Formulários do Windows** emite código.

### <a name="to-serialize-a-collection"></a>Para serializar uma coleção

1. Adicione um projeto de Aplicativos do Windows à solução. Nomeie o projeto `SerializationDemoControlTest`.

2. Na **Caixa de Ferramentas**, localize a guia chamada **Componentes da SerializationDemoControlLib**. Nessa guia, você encontrará o `SerializationDemoControl`. Para obter mais informações, confira [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. Coloque um `SerializationDemoControl` em seu formulário.

4. Localize a propriedade `Strings` na janela **Propriedades**. Clique na propriedade `Strings` e, em seguida, clique no botão de reticências (![captura de tela VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de conjunto de cadeia de caracteres**.

5. Digite várias cadeias de caracteres no **Editor de Conjunto de Cadeia de Caracteres**. Separe-os pressionando a tecla ENTER no final de cada cadeia de caracteres. Clique em **OK** quando terminar de inserir cadeias de caracteres.

> [!NOTE]
> As cadeias de caracteres que você digitou aparecem na <xref:System.Windows.Forms.TextBox> do `SerializationDemoControl`.

1. Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.

2. Abra o nó **Form1**. Abaixo está um arquivo chamado **Form1.Designer.cs** ou **Form1.Designer.vb**. Este é o arquivo no qual o **Designer de Formulários do Windows** emite um código que representa o estado de tempo de design do formulário e seus controles filho. Abra esse arquivo no **Editor de Códigos**.

3. Abra a região chamada **Código gerado pelo Windows Form Designer** e localize a seção rotulada como **serializationDemoControl1**. Sob esse rótulo está o código que representa o estado serializado do seu controle. As cadeias de caracteres que você digitou na etapa 5 aparecem em uma atribuição para a propriedade `Strings`. Os exemplos de código a seguir em c# e Visual Basic, mostrar o código semelhante ao que você verá se tiver digitado as cadeias de caracteres "vermelho", "orange" e "yellow".

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

4. No **Editor de códigos**, altere o valor da <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> no `Strings` propriedade para <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

5. Recompile a solução e repita as etapas 3 e 4.

> [!NOTE]
> Neste caso, o **Designer de Formulários do Windows** não emite nenhuma atribuição para a propriedade `Strings`.

## <a name="next-steps"></a>Próximas etapas

Se você souber como serializar uma coleção de tipos padrão, considere integrar seus controles personalizados mais profundamente no ambiente de tempo de design. Os tópicos a seguir descrevem como aprimorar a integração do tempo de design de seus controles personalizados:

- [Arquitetura de tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Atributos em controles dos Windows Forms](attributes-in-windows-forms-controls.md)

- [Visão geral da serialização do designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Visão geral da serialização do designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))
- [Como: Serializar coleções de tipos padrão com DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
- [Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
