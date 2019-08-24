---
title: 'Passo a passo: Depurando controles do Windows Forms no tempo de design'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 824d8a7de8e9e37899cb84d6cee9621f84a5bc65
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015694"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a>Passo a passo: Depurar controles de Windows Forms personalizados em tempo de design

Quando criar um controle personalizado, frequentemente você achará necessário depurar seu comportamento em tempo de design. Isso será especialmente válido se você estiver criando um designer personalizado para seu controle personalizado. Para obter detalhes, [consulte Passo a passos: Criar um controle de Windows Forms que aproveita os recursos](creating-a-wf-control-design-time-features.md)de tempo de design do Visual Studio.

Você pode depurar seus controles personalizados usando o Visual Studio, da mesma forma que depuraria qualquer outra classe do .NET Framework. A diferença é que você depurará uma instância separada do Visual Studio que está executando o código do controle personalizado.

## <a name="create-the-project"></a>Criar o projeto

A primeira etapa é criar o projeto do aplicativo. Você usará este projeto para criar o aplicativo que hospeda o controle personalizado.

No Visual Studio, crie um projeto de aplicativo do Windows e nomeie-o **DebuggingExample**.

## <a name="create-the-control-library-project"></a>Criar o projeto de biblioteca de controle

1. Adicione um projeto de **Biblioteca de controle do Windows** à solução.

2. Adicione um novo item **UserControl** ao projeto DebugControlLibrary. Nomeie-o como **DebugControl**.

3. Em **Gerenciador de soluções**, exclua o controle padrão do projeto excluindo o arquivo de código com um nome base de UserControl1.

4. Compile a solução.

## <a name="checkpoint"></a>Ponto de verificação

Neste ponto, você poderá ver o controle personalizado na **Caixa de Ferramentas**.

Para verificar seu progresso, localize a nova guia chamada **componentes DebugControlLibrary** e clique para selecioná-lo. Quando ela abrir, você verá seu controle listado como **DebugControl** com o ícone padrão ao lado dele.

## <a name="add-a-property-to-your-custom-control"></a>Adicionar uma propriedade ao seu controle personalizado

Para demonstrar que o código de seu controle personalizado está sendo executado em tempo de design, você adicionará uma propriedade e definirá um ponto de interrupção no código que implementa a propriedade.

1. Abra **DebugControl** no **Editor de Códigos**. Adicione o seguinte código à definição da classe:

    ```vb
    Private demoStringValue As String = Nothing
    <BrowsableAttribute(true)>
    Public Property DemoString() As String

        Get
            Return Me.demoStringValue
        End Get

        Set(ByVal value As String)
            Me.demoStringValue = value
        End Set

    End Property
    ```

    ```csharp
    private string demoStringValue = null;
    [Browsable(true)]
    public string DemoString
    {
        get
        {
            return this.demoStringValue;
        }
        set
        {
            demoStringValue = value;
        }
    }
    ```

2. Compile a solução.

## <a name="add-your-custom-control-to-the-host-form"></a>Adicionar seu controle personalizado ao formulário do host

Para depurar o comportamento em tempo de design do controle personalizado, você colocará uma instância da classe do controle personalizado em um formulário do host.

1. No projeto "DebuggingExample", abra Form1 no **Designer de Formulários do Windows**.

2. Na **caixa de Ferramentas**, abra a guia **Componentes de DebugControlLibrary** e arraste uma instância de **DebugControl** para o formulário.

3. Encontre a propriedade personalizada `DemoString` na janela **Propriedades**. Observe que você pode alterar seu valor, da mesma forma que faria com qualquer outra propriedade. Observe também que, quando a propriedade `DemoString` for selecionada, a cadeia de caracteres de descrição da propriedade aparecerá na parte inferior da janela **Propriedades**.

## <a name="set-up-the-project-for-design-time-debugging"></a>Configurar o projeto para depuração em tempo de design

Para depurar o comportamento em tempo de design do seu controle personalizado, você depurará uma instância separada do Visual Studio que está executando o código do seu controle personalizado.

1. Clique com o botão direito do mouse no projeto **DebugControlLibrary** no **Gerenciador de Soluções** e selecione **Propriedades**.

2. Na folha de propriedades **DebugControlLibrary**, selecione a guia **Depurar**.

     Na seção **Iniciar Ação**, selecione **Iniciar programa externo**. Você estará Depurando uma instância separada do Visual Studio, então clique nas reticências (![o botão de reticências (...) no botão janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png)) para procurar o IDE do Visual Studio. O nome do arquivo executável é **devenv. exe**e, se você tiver instalado no local padrão, seu caminho será *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.

3. Selecione **OK** para fechar a caixa de diálogo.

4. Clique com botão direito do mouse no projeto **DebugControlLibrary** e selecione **Definir como Projeto de Inicialização** para habilitar essa configuração de depuração.

## <a name="debug-your-custom-control-at-design-time"></a>Depurar seu controle personalizado em tempo de design

Agora, você está pronto para depurar o controle personalizado enquanto ele é executado em modo de design. Quando você iniciar a sessão de depuração, uma nova instância do Visual Studio será criada e você a usará para carregar a solução "DebuggingExample". Quando você abrir Form1 no **Designer de Formulários**, uma instância do controle personalizado será criada e começará a ser executada.

1. Abra o arquivo de origem **DebugControl** no **Editor de Códigos** e coloque um ponto de interrupção no acessador `Set` da propriedade `DemoString`.

2. Pressione **F5** para iniciar a sessão de depuração. Uma nova instância do Visual Studio é criada. É possível diferenciar as instâncias de duas maneiras:

    - A instância de depuração tem as palavras **Em execução** na barra de título

    - A instância de depuração tem o botão **Iniciar** em sua barra de ferramentas **Depurar** desabilitado

   Seu ponto de interrupção é definido na instância de depuração.

3. Na nova instância do Visual Studio, abra a solução "DebuggingExample". Você pode localizar facilmente a solução selecionando **Projetos Recentes** no menu **Arquivo**. O arquivo de solução "DebuggingExample.sln" será listado como o arquivo usado mais recentemente.

4. Abra Form1 no **Designer de Formulários** e selecione o controle **DebugControl**.

5. Altere o valor da propriedade `DemoString`. Quando você confirma a alteração, a instância de depuração do Visual Studio adquire o foco e a execução é interrompida em seu ponto de interrupção. É possível percorrer passo a passo o acessador de propriedade, da mesma forma que você o faria com qualquer outro código.

6. Para interromper a depuração, saia da instância hospedada do Visual Studio ou selecione o botão **parar depuração** na instância de depuração.

## <a name="next-steps"></a>Próximas etapas

Agora que você pode depurar seus controles personalizados em tempo de design, há muitas possibilidades para expandir a interação do controle com o IDE do Visual Studio.

- Você pode usar a <xref:System.ComponentModel.Component.DesignMode%2A> propriedade <xref:System.ComponentModel.Component> da classe para escrever o código que será executado somente no momento do design. Para obter detalhes, consulte <xref:System.ComponentModel.Component.DesignMode%2A>.

- Há vários atributos que você pode aplicar a propriedades do controle para manipular a interação do seu controle personalizado com o designer. Você pode encontrar esses atributos no <xref:System.ComponentModel?displayProperty=nameWithType> namespace.

- Você pode escrever um designer personalizado para seu controle personalizado. Isso lhe dá controle total sobre a experiência de design usando a infra-estrutura de designer extensível exposta pelo Visual Studio. Para obter detalhes, [consulte Passo a passos: Criar um controle de Windows Forms que aproveita os recursos](creating-a-wf-control-design-time-features.md)de tempo de design do Visual Studio.

## <a name="see-also"></a>Consulte também

- [Passo a passo: Criando um controle de Windows Forms que aproveita os recursos de tempo de design do Visual Studio](creating-a-wf-control-design-time-features.md)
