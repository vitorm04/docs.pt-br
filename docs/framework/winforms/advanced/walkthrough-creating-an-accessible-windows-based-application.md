---
title: 'Instruções passo a passo: criando um aplicativo baseado no Windows acessível'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 6c798d0f6a454c7ee819d5556970bca12f1812e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529617"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>Instruções passo a passo: criando um aplicativo baseado no Windows acessível
A criação de um aplicativo acessível tem implicações importantes nos negócios. Muitos órgãos governamentais tem regulamentos de acessibilidade para a compra de software. O logotipo Certified for Windows inclui requisitos de acessibilidade. Estima-se que 30 milhões de moradores, apenas dos EUA, muitos deles clientes potenciais, são afetados pela acessibilidade do software.  
  
 Este passo a passo abordará os cinco requisitos de acessibilidade para o logotipo Certified for Windows. De acordo com a esses requisitos, um aplicativo acessível:  
  
-   Dará suporte às configurações de tamanho, cor, fonte e de entrada do Painel de Controle. A barra de menus, a barra de título, as bordas e a barra de status serão todas redimensionadas quando o usuário alterar as configurações do painel de controle. Nenhuma alteração adicional aos controles ou ao código será necessária neste aplicativo.  
  
-   Dará suporte ao modo de alto contraste.  
  
-   Fornecerá acesso ao teclado documentado a todos os recursos.  
  
-   Exporá o local do foco do teclado visualmente e programaticamente.  
  
-   Evitará a transmissão de informações importantes apenas através do som.  
  
 Para obter mais informações, consulte [Recursos para projetar aplicativos acessíveis](/visualstudio/ide/reference/resources-for-designing-accessible-applications).  
  
 Para obter informações sobre suporte a diferentes layouts de teclado, consulte [Melhores práticas para o desenvolvimento de aplicativos prontos para o mundo](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Este passo a passo cria a interface do usuário para um aplicativo que recebe pedidos de pizza. Ele consiste em um <xref:System.Windows.Forms.TextBox> para o nome do cliente, um <xref:System.Windows.Forms.RadioButton> grupo para selecionar o tamanho da pizza, um <xref:System.Windows.Forms.CheckedListBox> para selecionar os ingredientes, dois controles de botão rotulado ordem e Cancelar e um Menu com um comando de saída.  
  
 O usuário insere o nome do cliente, o tamanho da pizza e os ingredientes desejados. Quando o usuário clica no botão Pedir, um resumo do pedido e o custo são exibidos em uma caixa de mensagem e os controles são limpos e preparados para o próximo pedido. Quando o usuário clica no botão Cancelar, os controles são limpos e preparados para o próximo pedido. Quando o usuário clica no item de menu Sair, o programa é fechado.  
  
 A ênfase deste passo a passo não é no código para um sistema de pedidos de vendas, mas na acessibilidade da interface do usuário. O passo a passo demonstra os recursos de acessibilidade de vários controles usados com frequência, incluindo botões, botões de opção, caixas de texto e rótulos.  
  
#### <a name="to-begin-making-the-application"></a>Para começar a criar o aplicativo  
  
-   Crie um novo aplicativo do Windows em Visual Basic ou Visual c#. Nomeie o projeto como **PizzaOrder**. (Para obter detalhes, consulte [Criando novas soluções e projetos](/visualstudio/ide/creating-solutions-and-projects)).  
  
## <a name="adding-the-controls-to-the-form"></a>Adicionando os controles ao formulário  
 Ao adicionar controles a um formulário, tenha em mente as seguintes diretrizes para criar um aplicativo acessível:  
  
-   Definir o <xref:System.Windows.Forms.Control.AccessibleDescription%2A> e <xref:System.Windows.Forms.Control.AccessibleName%2A> propriedades. Neste exemplo, a configuração padrão para o <xref:System.Windows.Forms.Control.AccessibleRole%2A> é suficiente. Para obter mais informações sobre as propriedades de acessibilidade, consulte [Fornecendo informações de acessibilidade para controles em um Windows Form](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).  
  
-   Defina o tamanho da fonte como 10 pontos ou mais.  
  
    > [!NOTE]
    >  Se você definir o tamanho da fonte do formulário como 10 ao iniciar, todos os controles adicionados posteriormente ao formulário terão um tamanho da fonte de 10.  
  
-   Certifique-se de que qualquer controle de rótulo que descreve um controle TextBox venha logo antes do controle TextBox na ordem de tabulação.  
  
-   Adicionar uma chave de acesso, usando o caractere "&", para o <xref:System.Windows.Forms.Control.Text%2A> propriedade de qualquer controle que o usuário deseja navegar.  
  
-   Adicionar uma chave de acesso, usando o caractere "&", para o <xref:System.Windows.Forms.Control.Text%2A> propriedade do rótulo que precede um controle que o usuário deseja navegar. Definir os rótulos <xref:System.Windows.Forms.Label.UseMnemonic%2A> propriedade `true`, de modo que o foco é definido para o próximo controle na ordem de tabulação quando o usuário pressiona a tecla de acesso.  
  
-   Adicione chaves de acesso a todos os itens de menu.  
  
#### <a name="to-make-your-windows-application-accessible"></a>Para tornar seu aplicativo do Windows acessível  
  
-   Adicione os controles ao formulário e defina as propriedades conforme descrito abaixo. Veja a imagem no final da tabela para um modelo de como organizar os controles no formulário.  
  
    |Objeto|Propriedade|Valor|  
    |------------|--------------|-----------|  
    |Form1|AccessibleDescription|Formulário de pedido|  
    ||AccessibleName|Formulário de pedido|  
    ||Tamanho da fonte|10|  
    ||Texto|Formulário de pedido de pizza|  
    |PictureBox|Nome|logotipo|  
    ||AccessibleDescription|Uma fatia de pizza|  
    ||AccessibleName|Logotipo da empresa|  
    ||Image|Qualquer ícone ou bitmap|  
    |Rotular|Nome|companyLabel|  
    ||Texto|Pizza boa|  
    ||TabIndex|1|  
    ||AccessibleDescription|Nome da empresa|  
    ||AccessibleName|Nome da empresa|  
    ||Backcolor|Azul|  
    ||Forecolor|Amarelo|  
    ||Tamanho da fonte|18|  
    |Rotular|Nome|customerLabel|  
    ||Texto|&Nome|  
    ||TabIndex|2|  
    ||AccessibleDescription|Rótulo de nome do cliente|  
    ||AccessibleName|Rótulo de nome do cliente|  
    ||UseMnemonic|verdadeiro|  
    |TextBox|Nome|customerName|  
    ||Texto|(nenhum)|  
    ||TabIndex|3|  
    ||AccessibleDescription|Nome do cliente|  
    ||AccessibleName|Nome do cliente|  
    |GroupBox|Nome|sizeOptions|  
    ||AccessibleDescription|Opções de tamanho de pizza|  
    ||AccessibleName|Opções de tamanho de pizza|  
    ||Texto|Tamanho de pizza|  
    ||TabIndex|4|  
    |RadioButton|Nome|smallPizza|  
    ||Texto|&Pequena $6.00|  
    ||Selecionado|verdadeiro|  
    ||TabIndex|0|  
    ||AccessibleDescription|Pizza pequena|  
    ||AccessibleName|Pizza pequena|  
    |RadioButton|Nome|largePizza|  
    ||Texto|&Grande $10.00|  
    ||TabIndex|1|  
    ||AccessibleDescription|Pizza grande|  
    ||AccessibleName|Pizza grande|  
    |Rotular|Nome|toppingsLabel|  
    ||Texto|&Ingredientes ($0.75 cada)|  
    ||TabIndex|5|  
    ||AccessibleDescription|Rótulo de ingredientes|  
    ||AccessibleName|Rótulo de ingredientes|  
    ||UseMnemonic|verdadeiro|  
    |CheckedListBox|Nome|ingredientes|  
    ||TabIndex|6|  
    ||AccessibleDescription|Ingredientes disponíveis|  
    ||AccessibleName|Ingredientes disponíveis|  
    ||Itens|Pepperoni, Linguiça, Cogumelos|  
    |Botão|Nome|ordem|  
    ||Texto|&Ordem|  
    ||TabIndex|7|  
    ||AccessibleDescription|Total do pedido|  
    ||AccessibleName|Pedido total|  
    |Botão|Nome|cancelar|  
    ||Texto|&Cancelar|  
    ||TabIndex|8|  
    ||AccessibleDescription|Cancelar o pedido|  
    ||AccessibleName|Cancelar pedido|  
    |MainMenu|Nome|theMainMenu|  
    |MenuItem|Nome|fileCommands|  
    ||Texto|&Arquivo|  
    |MenuItem|Nome|exitApp|  
    ||Texto|Sa&ir|  
  
     ![Formulário de pedido de pizza](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")  
Seu formulário será algo parecido com o seguinte:  
  
## <a name="supporting-high-contrast-mode"></a>Suporte ao modo de alto contraste  
 O modo de Alto Contraste é uma configuração de sistema do Windows que melhora a legibilidade, usando cores contrastantes e tamanhos de fonte que são benéficos para usuários com deficiências visuais. O <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> é fornecida para determinar se o modo de alto contraste está definido.  
  
 Se SystemInformation.HighContrast for `true`, o aplicativo deverá:  
  
-   Exibir todos os elementos de interface do usuário usando o esquema de cores do sistema  
  
-   Transmitir, por dicas visuais ou por som, quaisquer informações que são transmitidas por meio de cor. Por exemplo, se determinados itens de lista estão realçados com uma fonte vermelha, você também pode adicionar negrito à fonte para que o usuário tenha uma dica diferente das cores de que os itens estão realçados.  
  
-   Omitir imagens ou padrões por trás do texto  
  
 O aplicativo deve verificar a configuração de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> quando o aplicativo é iniciado e responder ao evento de sistema <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>. O <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> é gerado sempre que o valor de <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> alterações.  
  
 Em nosso aplicativo, o único elemento que não está usando as configurações do sistema para a cor é o `lblCompanyName`. O <xref:System.Drawing.SystemColors> classe é usada para alterar as configurações de cor do rótulo para as cores do sistema selecionadas pelo usuário.  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>Para habilitar o modo de Alto Contraste de uma maneira eficaz  
  
1.  Crie um método para definir as cores do rótulo para as cores do sistema.  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  Chame o procedimento `SetColorScheme` no construtor do formulário (`Public Sub New()` no Visual Basic e `public class Form1` no Visual C#). Para acessar o construtor no Visual Basic, você precisará expandir a região rotulada como **Código gerado pelo Windows Form Designer**.  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  Criar um procedimento de evento, com a assinatura apropriada, para responder a <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> eventos.  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  Adicione código ao construtor de formulário, após a chamada ao `InitializeComponents`, para associar o procedimento de evento ao evento do sistema. Esse método chama o procedimento `SetColorScheme`.  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  Adicione código para o formulário <xref:System.Windows.Forms.Control.Dispose%2A> método, antes da chamada para o <xref:System.Windows.Forms.Control.Dispose%2A> método da classe base, para liberar o evento quando o aplicativo for fechado. Para acessar o <xref:System.Windows.Forms.Control.Dispose%2A> método no Visual Basic, você precisará expandir a região rotulada como código gerado pelo Windows Form Designer.  
  
    > [!NOTE]
    >  O código de evento do sistema executa um thread separado do aplicativo principal. Se você não liberar o evento, o código que você associou com o evento será executado mesmo depois que o programa for fechado.  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  Pressione F5 para executar o aplicativo.  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>Transmitindo informações importantes por outros meios além do som  
 Neste aplicativo, nenhuma informação é transmitida apenas pelo som. Se você usa som em seu aplicativo, você também deve fornecer as informações por algum outro meio.  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>Para fornecer informações por outros meios além do som  
  
1.  Faça a barra de título piscar, usando a função FlashWindow da API do Windows. Para obter um exemplo de como chamar funções da API do Windows, consulte [Passo a passo: chamando APIs do Windows](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
    > [!NOTE]
    >  O usuário pode ter o serviço SoundSentry do Windows habilitado, que também fará com que a janela pisque quando os sons do sistema forem executados pelo alto-falante do computador.  
  
2.  Exiba as informações importantes em uma janela não modal para que o usuário possa responder a elas.  
  
3.  Exiba uma caixa de mensagem que obtém o foco do teclado. Evite esse método quando o usuário pode estar digitando.  
  
4.  Exiba um indicador de status na área de notificação de status da barra de tarefas. Para obter detalhes, consulte [Adicionando ícones de aplicativo ao TaskBar com o componente NotifyIcon dos Windows Forms](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Antes de implantar o aplicativo, você deve testar os recursos de acessibilidade que implementou.  
  
#### <a name="to-test-accessibility-features"></a>Para testar os recursos de acessibilidade  
  
1.  Para testar o acesso do teclado, desconecte o mouse e navegue na interface do usuário até cada recurso, usando apenas o teclado. Certifique-se de que todas as tarefas podem ser realizadas usando apenas o teclado.  
  
2.  Para testar o suporte ao Alto Contraste, escolha o ícone de Opções de Acessibilidade no Painel de Controle. Clique na guia Exibir e marque a caixa de seleção Usar Alto Contraste. Navegue por todos os elementos de interface do usuário para garantir que as alterações de cores e fontes estão refletidas. Além disso, verifique se as imagens ou os padrões desenhados atrás do texto estão omitidos.  
  
    > [!NOTE]
    >  O Windows NT 4 não tem um ícone de Opções de Acessibilidade no Painel de Controle. Portanto, este procedimento para alterar a configuração SystemInformation.HighContrast não funciona no Windows NT 4.  
  
3.  Outras ferramentas estão prontamente disponíveis para testar a acessibilidade de um aplicativo.  
  
4.  Para testar a exposição do foco do teclado, execute a Lupa. (Para abri-la, clique no menu **Iniciar**, aponte para **Programas**, aponte para **Acessórios**, aponte para **Acessibilidade** e, em seguida, clique em **Lupa**). Navegue na interface do usuário usando as tabulações do teclado e o mouse. Verifique se toda a navegação é rastreada corretamente na **Lupa**.  
  
5.  Para testar a exposição dos elementos da tela, execute Inspecionar e use o mouse e a tecla TAB para acessar cada elemento. Verifique se as informações apresentadas nos campos Nome, Estado, Função, Local e Valor da janela Inspecionar são significativas para o usuário para cada objeto na interface do usuário.
