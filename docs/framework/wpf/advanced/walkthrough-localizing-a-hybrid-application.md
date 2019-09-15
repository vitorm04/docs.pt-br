---
title: 'Passo a passo: localizar um aplicativo híbrido'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b98bf7b3f0aa4e7698a5c0ca7c8ae16051ce6300
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991770"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Passo a passo: localizar um aplicativo híbrido

Este tutorial mostra como localizar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos em um aplicativo híbrido baseado em um. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]

As tarefas ilustradas neste passo a passo incluem:

- Criando o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projeto host.

- Atributo de conteúdo localizável.

- Habilitando a localização.

- Atribuindo identificadores de recursos.

- Usando a ferramenta LocBaml para produzir um assembly satélite.

Para obter uma listagem de código completa das tarefas ilustradas neste passo a passos, consulte [localizando um exemplo de aplicativo híbrido](https://go.microsoft.com/fwlink/?LinkID=160015).

Quando tiver terminado, você terá um aplicativo híbrido localizado.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Criando o projeto de host do Windows Forms

A primeira etapa é criar o projeto [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] de aplicativo e adicionar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento com conteúdo que será localizado.

### <a name="to-create-the-host-project"></a>Criar o projeto de host

1. Crie um projeto de **aplicativo** do `LocalizingWpfInWf`WPF chamado.  (**Arquivo** > **novo** **projeto Visual C#**  Visual BasicaplicativoWPF > de**área de trabalho clássica**). >  >  > 

2. Adicione um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> elemento chamado`SimpleControl` ao projeto.

3. Use o <xref:System.Windows.Forms.Integration.ElementHost> controle para posicionar `SimpleControl` um elemento no formulário. Para obter mais informações, confira [Passo a passo: Hospedando um controle composto do WPF 3D no Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Adicionando conteúdo localizável

Em seguida, você adicionará [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] um controle rótulo e definirá o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo do elemento como uma cadeia de caracteres localizável.

### <a name="to-add-localizable-content"></a>Para adicionar um conteúdo localizável

1. Em **Gerenciador de soluções**, clique duas vezes em **SimpleControl. XAML** para abri [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]-lo no.

2. Defina o conteúdo do <xref:System.Windows.Controls.Button> controle usando o código a seguir.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. Em **Gerenciador de soluções**, clique duas vezes em **Form1** para abri-lo no designer de formulários do Windows.

4. Abra a **caixa de ferramentas** e clique duas vezes em **rótulo** para adicionar um controle rótulo ao formulário. Defina o valor de sua <xref:System.Windows.Forms.Control.Text%2A> Propriedade como `"Hello"`.

5. Pressione **F5** para compilar e executar o aplicativo.

     O `SimpleControl` elemento e o controle rótulo exibem o texto **"Olá"** .

## <a name="enabling-localization"></a>Habilitando a localização

O Designer de Formulários do Windows fornece configurações para habilitar a localização em um assembly satélite.

### <a name="to-enable-localization"></a>Para permitir a localização

1. Em **Gerenciador de soluções**, clique duas vezes em **Form1.cs** para abri-lo no designer de formulários do Windows.

2. Na janela **Propriedades** , defina o valor da propriedade **localizável** do formulário como `true`.

3. Na janela **Propriedades** , defina o valor da propriedade **Language** como **espanhol (Espanha)** .

4. No Designer de Formulários do Windows, selecione o controle de rótulo.

5. Na janela **Propriedades** , defina o valor da <xref:System.Windows.Forms.Control.Text%2A> Propriedade como. `"Hola"`

     Um novo arquivo de recursos chamado Form1.es-ES.resx é adicionado ao projeto.

6. No **Gerenciador de soluções**, clique com o botão direito do mouse em **Form1.cs** e clique em **Exibir código** para abri-lo no editor de códigos.

7. Copie o código a seguir para `Form1` o construtor, precedendo `InitializeComponent`a chamada para.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **LocalizingWpfInWf** e clique em **descarregar projeto**.

     O nome do projeto é rotulado **(não disponível)** .

9. Clique com o botão direito do mouse em **LocalizingWpfInWf**e clique em **Editar LocalizingWpfInWf. csproj**.

     O arquivo de projeto é aberto no Editor de Códigos.

10. Copie a linha a seguir para o `PropertyGroup` primeiro no arquivo de projeto.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Salve o arquivo de projeto e feche-o.

12. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **LocalizingWpfInWf** e clique em **recarregar projeto**.

## <a name="assigning-resource-identifiers"></a>Atribuindo identificadores de recursos

Você pode mapear o conteúdo localizável para assemblies de recursos usando identificadores de recurso. O aplicativo MSBuild. exe atribui automaticamente identificadores de recursos quando você especifica a `updateuid` opção.

### <a name="to-assign-resource-identifiers"></a>Para atribuir identificadores de recursos

1. No menu Iniciar, abra o Prompt de Comando do Desenvolvedor para o Visual Studio.

2. Use o comando a seguir para atribuir identificadores de recurso ao seu conteúdo localizável.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. Em **Gerenciador de soluções**, clique duas vezes em **SimpleControl. XAML** para abri-lo no editor de código. Você verá que o `msbuild` comando adicionou o `Uid` atributo a todos os elementos. Isso facilita a localização por meio da atribuição de identificadores de recurso.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Pressione **F6** para compilar a solução.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Usando LocBaml para produzir um assembly satélite

O conteúdo localizado é armazenado em um *assembly satélite*somente de recursos. Use a ferramenta de linha de comando LocBaml. exe para produzir um assembly localizado para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seu conteúdo.

### <a name="to-produce-a-satellite-assembly"></a>Para produzir um assembly satélite

1. Copie LocBaml.exe para sua pasta do projeto obj\Debug. Para obter mais informações, consulte [localizar um aplicativo](how-to-localize-an-application.md).

2. Na janela do Prompt de Comando, use o seguinte comando para extrair cadeias de caracteres de recurso em um arquivo temporário.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Abra o arquivo temp. csv com o Visual Studio ou outro editor de texto. Substitua a cadeia `"Hello"` de caracteres pela `"Hola"`tradução espanhola.

4. Salve o arquivo temp.csv.

5. Use o seguinte comando para gerar o arquivo de recurso localizado.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     O arquivo LocalizingWpfInWf.g.es-ES.resources é criado na pasta obj\Debug.

6. Use o seguinte comando para compilar o assembly satélite localizado.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     O arquivo LocalizingWpfInWf.resources.dll é criado na pasta obj\Debug.

7. Copie o arquivo LocalizingWpfInWf.resources.dll para a pasta do projeto bin\Debug\es-ES. Substitua o arquivo existente.

8. Execute LocalizingWpfInWf.exe, que está localizado na pasta bin\Debug de seu projeto. Não recompilar o aplicativo ou o assembly satélite será substituído.

     O aplicativo mostra as cadeias de caracteres localizadas em vez de cadeias de caracteres em inglês.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Localizar um aplicativo](how-to-localize-an-application.md)
- [Passo a passo: Localizando Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
