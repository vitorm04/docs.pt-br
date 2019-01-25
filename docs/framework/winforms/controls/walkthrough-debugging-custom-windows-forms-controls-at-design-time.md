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
ms.openlocfilehash: ceee83c9deb318f5912eb724cbd237c3d7b73152
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733331"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>Passo a passo: Depurando controles do Windows Forms no tempo de design
Quando criar um controle personalizado, frequentemente você achará necessário depurar seu comportamento em tempo de design. Isso será especialmente válido se você estiver criando um designer personalizado para seu controle personalizado. Para obter detalhes, consulte [passo a passo: Criando um Windows Forms o controle que tira proveito dos recursos de tempo de Design do Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
 Você pode depurar seus controles personalizados usando o Visual Studio, da mesma forma que depuraria qualquer outra classe do .NET Framework. A diferença é que você depurará uma instância separada do Visual Studio que está executando o código do seu controle personalizado  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar um projeto dos Windows Forms para hospedar o controle personalizado  
  
-   Criar um projeto de biblioteca de controle  
  
-   Adicionar uma propriedade ao controle personalizado  
  
-   Adicionar o controle personalizado ao formulário de host  
  
-   Configurar o projeto para depuração em tempo de design  
  
-   Depurar o controle personalizado em tempo de design  
  
 Quando tiver terminado, você compreenderá as tarefas necessárias para depurar o comportamento de tempo de design de um controle personalizado.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto do aplicativo. Você usará este projeto para criar o aplicativo que hospeda o controle personalizado.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
-   Crie um projeto de aplicativo do Windows chamado "DebuggingExample" (**arquivo** > **New** > **projeto**  >  **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).  
  
## <a name="creating-a-control-library-project"></a>Criar um Projeto de Biblioteca de Controle  
 A etapa seguinte é criar o projeto de biblioteca de controle e configurar o controle personalizado.  
  
#### <a name="to-create-the-control-library-project"></a>Para criar o projeto de biblioteca de controles  
  
1.  Adicione um projeto de **Biblioteca de controle do Windows** à solução.  
  
2.  Adicione um novo item **UserControl** ao projeto DebugControlLibrary. Para obter detalhes, consulte [NIB: como: Adicionar novos itens de projeto](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Dê ao novo arquivo de origem o nome base "DebugControl".  
  
3.  Usando o **Gerenciador de Soluções**, exclua o controle padrão do projeto excluindo o arquivo de código com o nome de base "`UserControl1`". Para obter detalhes, consulte [NIB: como: Remover, apagar e excluir itens](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
4.  Compile a solução.  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Neste ponto, você poderá ver o controle personalizado na **Caixa de Ferramentas**.  
  
#### <a name="to-check-your-progress"></a>Para verificar o progresso  
  
-   Localize a nova guia chamada **Componentes de DebugControlLibrary** e clique para selecioná-la. Quando ela abrir, você verá seu controle listado como **DebugControl** com o ícone padrão ao lado dele.  
  
## <a name="adding-a-property-to-your-custom-control"></a>Adicionar uma Propriedade ao Controle Personalizado  
 Para demonstrar que o código de seu controle personalizado está sendo executado em tempo de design, você adicionará uma propriedade e definirá um ponto de interrupção no código que implementa a propriedade.  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>Para adicionar uma propriedade ao controle personalizado  
  
1.  Abra **DebugControl** no **Editor de Códigos**. Adicione o seguinte código à definição da classe:  
  
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
  
2.  Compile a solução.  
  
## <a name="adding-your-custom-control-to-the-host-form"></a>Adicionar o Controle Personalizado ao Formulário de Host  
 Para depurar o comportamento em tempo de design do controle personalizado, você colocará uma instância da classe do controle personalizado em um formulário do host.  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>Para adicionar o controle personalizado ao formulário de host  
  
1.  No projeto "DebuggingExample", abra Form1 no **Designer de Formulários do Windows**.  
  
2.  Na **caixa de Ferramentas**, abra a guia **Componentes de DebugControlLibrary** e arraste uma instância de **DebugControl** para o formulário.  
  
3.  Encontre a propriedade personalizada `DemoString` na janela **Propriedades**. Observe que você pode alterar seu valor, da mesma forma que faria com qualquer outra propriedade. Observe também que, quando a propriedade `DemoString` for selecionada, a cadeia de caracteres de descrição da propriedade aparecerá na parte inferior da janela **Propriedades**.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Configurar o Projeto para Depuração em Tempo de Design  
 Para depurar o comportamento em tempo de design do seu controle personalizado, você depurará uma instância separada do Visual Studio que está executando o código do seu controle personalizado.  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Para configurar o projeto para depuração em tempo de design  
  
1.  Clique com o botão direito do mouse no projeto **DebugControlLibrary** no **Gerenciador de Soluções** e selecione **Propriedades**.  
  
2.  Na folha de propriedades **DebugControlLibrary**, selecione a guia **Depurar**.  
  
     Na seção **Iniciar Ação**, selecione **Iniciar programa externo**. Você depurará uma instância separada do Visual Studio, então clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para procurar o IDE do Visual Studio. O nome do arquivo executável é **devenv.exe** e, se você o instalou no local padrão, o caminho dele é %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.  
  
3.  Clique em **OK** para fechar a caixa de diálogo.  
  
4.  Clique com botão direito do mouse no projeto **DebugControlLibrary** e selecione **Definir como Projeto de Inicialização** para habilitar essa configuração de depuração.  
  
## <a name="debugging-your-custom-control-at-design-time"></a>Depurar o Controle Personalizado em Tempo de Design  
 Agora, você está pronto para depurar o controle personalizado enquanto ele é executado em modo de design. Quando você iniciar a sessão de depuração, uma nova instância do Visual Studio será criada e você a usará para carregar a solução "DebuggingExample". Quando você abrir Form1 no **Designer de Formulários**, uma instância do controle personalizado será criada e começará a ser executada.  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>Para depurar o controle personalizado em tempo de design  
  
1.  Abra o arquivo de origem **DebugControl** no **Editor de Códigos** e coloque um ponto de interrupção no acessador `Set` da propriedade `DemoString`.  
  
2.  Pressione F5 para iniciar a sessão de depuração. Observe que uma nova instância do Visual Studio é criada. É possível diferenciar as instâncias de duas maneiras:  
  
    -   A instância de depuração tem as palavras **Em execução** na barra de título  
  
    -   A instância de depuração tem o botão **Iniciar** em sua barra de ferramentas **Depurar** desabilitado  
  
     Seu ponto de interrupção é definido na instância de depuração.  
  
3.  Na nova instância do Visual Studio, abra a solução "DebuggingExample". Você pode localizar facilmente a solução selecionando **Projetos Recentes** no menu **Arquivo**. O arquivo de solução "DebuggingExample.sln" será listado como o arquivo usado mais recentemente.  
  
4.  Abra Form1 no **Designer de Formulários** e selecione o controle **DebugControl**.  
  
5.  Altere o valor da propriedade `DemoString`. Observe que, quando você confirma a alteração, a instância de depuração do Visual Studio fica em foco e a execução é interrompida no ponto de interrupção. É possível percorrer passo a passo o acessador de propriedade, da mesma forma que você o faria com qualquer outro código.  
  
6.  Quando tiver terminado sua sessão de depuração, você pode sair ignorando a instância hospedada do Visual Studio ou clicando no botão **Parar Depuração** na instância de depuração.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você pode depurar seus controles personalizados em tempo de design, há muitas possibilidades para expandir a interação do controle com o IDE do Visual Studio.  
  
-   Você pode usar o <xref:System.ComponentModel.Component.DesignMode%2A> propriedade do <xref:System.ComponentModel.Component> classe para escrever um código que será executado somente em tempo de design. Para obter detalhes, consulte <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Há vários atributos que você pode aplicar a propriedades do controle para manipular a interação do seu controle personalizado com o designer. Você pode encontrar esses atributos no <xref:System.ComponentModel?displayProperty=nameWithType> namespace.  
  
-   Você pode escrever um designer personalizado para seu controle personalizado. Isso lhe dá controle total sobre a experiência de design usando a infra-estrutura de designer extensível exposta pelo Visual Studio. Para obter detalhes, consulte [passo a passo: Criando um Windows Forms o controle que tira proveito dos recursos de tempo de Design do Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
## <a name="see-also"></a>Consulte também
- [Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)
- [Como: Serviços de tempo de Design de acesso](https://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)
- [Como: Suporte de tempo de Design de acesso no Windows Forms](https://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
