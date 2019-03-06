---
title: 'Passo a passo: Localizando um aplicativo híbrido'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 116a847d4f7b0591e823416cf5744e68d689c6ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378074"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Passo a passo: Localizando um aplicativo híbrido

Este passo a passo mostra como localizar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos em um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-com base em aplicativo híbrido.

As tarefas ilustradas neste passo a passo incluem:

-   Criando o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projeto host.

-   Atributo de conteúdo localizável.

-   Habilitando a localização.

-   Atribuindo identificadores de recursos.

-   Usando a ferramenta LocBaml para produzir um assembly satélite.

Para obter uma listagem de código completa das tarefas ilustradas neste passo a passo, consulte [Localizando um exemplo de aplicativo híbrido](https://go.microsoft.com/fwlink/?LinkID=160015).

Quando tiver terminado, você terá um aplicativo híbrido localizado.

## <a name="prerequisites"></a>Pré-requisitos

Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

-   Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Criando o projeto de host do Windows Forms

A primeira etapa é criar o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplicativo do projeto e adicionar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento com conteúdo que você vai localizar.

### <a name="to-create-the-host-project"></a>Criar o projeto de host

1.  Criar uma **aplicativo WPF** projeto chamado `LocalizingWpfInWf`.  (**Arquivo** > **nova** > **projeto** > **Visual C#** ou **Visual Basic**   >  **Área de trabalho clássica** > **aplicativo WPF**).

2.  Adicionar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> elemento chamado `SimpleControl` ao projeto.

3.  Use o <xref:System.Windows.Forms.Integration.ElementHost> controle para colocar um `SimpleControl` elemento no formulário. Para obter mais informações, confira [Passo a passo: Hospedando um controle composto do WPF 3D nos Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Adicionando conteúdo localizável

Em seguida, você adicionará uma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle de rótulo e defina o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo do elemento em uma cadeia de caracteres localizável.

### <a name="to-add-localizable-content"></a>Para adicionar um conteúdo localizável

1.  Na **Gerenciador de soluções**, clique duas vezes em **Simplecontrol** para abri-lo no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2.  Defina o conteúdo do <xref:System.Windows.Controls.Button> controlar usando o código a seguir.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  Na **Gerenciador de soluções**, clique duas vezes em **Form1** abri-lo no Designer de formulários do Windows.

4.  Abra o **caixa de ferramentas** e clique duas vezes em **rótulo** para adicionar um controle de rótulo ao formulário. Defina o valor de sua <xref:System.Windows.Forms.Control.Text%2A> propriedade para `"Hello"`.

5.  Pressione **F5** para compilar e executar o aplicativo.

     Os dois os `SimpleControl` elemento e o controle de rótulo exibem o texto **"Hello"**.

## <a name="enabling-localization"></a>Habilitando a localização

O Designer de Formulários do Windows fornece configurações para habilitar a localização em um assembly satélite.

### <a name="to-enable-localization"></a>Para permitir a localização

1.  Na **Gerenciador de soluções**, clique duas vezes em **Form1.cs** abri-lo no Designer de formulários do Windows.

2.  No **propriedades** janela, defina o valor no formato **localizável** propriedade `true`.

3.  No **propriedades** janela, defina o valor da **idioma** propriedade a ser **Espanhol (Espanha)**.

4.  No Designer de Formulários do Windows, selecione o controle de rótulo.

5.  No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Text%2A> propriedade `"Hola"`.

     Um novo arquivo de recursos chamado Form1.es-ES.resx é adicionado ao projeto.

6.  Na **Gerenciador de soluções**, clique com botão direito **Form1.cs** e clique em **Exibir código** para abri-lo no Editor de códigos.

7.  Copie o seguinte código para o `Form1` construtor, antes de chamar `InitializeComponent`.

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  Na **Gerenciador de soluções**, clique com botão direito **LocalizingWpfInWf** e clique em **descarregar projeto**.

     O nome do projeto é rotulado **(não disponível)**.

9. Clique com botão direito **LocalizingWpfInWf**e clique em **Editar Localizingwpfinwf**.

     O arquivo de projeto é aberto no Editor de Códigos.

10. Copie a seguinte linha para a primeira `PropertyGroup` no arquivo de projeto.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Salve o arquivo de projeto e feche-o.

12. Na **Gerenciador de soluções**, clique com botão direito **LocalizingWpfInWf** e clique em **recarregar projeto**.

## <a name="assigning-resource-identifiers"></a>Atribuindo identificadores de recursos

Você pode mapear o conteúdo localizável para assemblies de recursos usando identificadores de recurso. O aplicativo MsBuild.exe atribui automaticamente identificadores de recurso ao especificar o `updateuid` opção.

### <a name="to-assign-resource-identifiers"></a>Para atribuir identificadores de recursos

1.  No Menu Iniciar, abra o Prompt de comando do desenvolvedor para Visual Studio.

2.  Use o comando a seguir para atribuir identificadores de recurso ao seu conteúdo localizável.

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3.  Na **Gerenciador de soluções**, clique duas vezes em **Simplecontrol** para abri-lo no Editor de códigos. Você verá que o `msbuild` comando tiver adicionado o `Uid` a todos os elementos de atributo. Isso facilita a localização por meio da atribuição de identificadores de recurso.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  Pressione **F6** para compilar a solução.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Usando LocBaml para produzir um assembly satélite

O conteúdo localizado é armazenado em um recurso somente *assembly satélite*. Use a ferramenta de linha de comando LocBaml.exe para produzir um assembly localizado para o seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.

### <a name="to-produce-a-satellite-assembly"></a>Para produzir um assembly satélite

1.  Copie LocBaml.exe para sua pasta do projeto obj\Debug. Para obter mais informações, consulte [localizar um aplicativo](how-to-localize-an-application.md).

2.  Na janela do Prompt de Comando, use o seguinte comando para extrair cadeias de caracteres de recurso em um arquivo temporário.

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  Abra o arquivo Temp com o Visual Studio ou outro editor de texto. Substitua a cadeia de caracteres `"Hello"` pela tradução do espanhol, `"Hola"`.

4.  Salve o arquivo temp.csv.

5.  Use o seguinte comando para gerar o arquivo de recurso localizado.

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     O arquivo LocalizingWpfInWf.g.es-ES.resources é criado na pasta obj\Debug.

6.  Use o seguinte comando para compilar o assembly satélite localizado.

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     O arquivo LocalizingWpfInWf.resources.dll é criado na pasta obj\Debug.

7.  Copie o arquivo LocalizingWpfInWf.resources.dll para a pasta do projeto bin\Debug\es-ES. Substitua o arquivo existente.

8.  Execute LocalizingWpfInWf.exe, que está localizado na pasta bin\Debug de seu projeto. Não recompilar o aplicativo ou o assembly satélite será substituído.

     O aplicativo mostra as cadeias de caracteres localizadas em vez de cadeias de caracteres em inglês.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Localizar um aplicativo](how-to-localize-an-application.md)
- [Passo a passo: Localizando Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
