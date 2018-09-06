---
title: 'Instruções passo a passo: criando um controle composto com o Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 5f8384140b813400e106ad959684264304541c93
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740619"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>Instruções passo a passo: criando um controle composto com o Visual C# #
Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas. Basicamente, um controle de composição é um componente com uma representação visual. Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor. Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles. Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`. Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock  
  
1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.  
  
2.  Na lista de projetos do Visual c#, selecione a **biblioteca de controle do Windows Forms** modelo de projeto, digite `ctlClockLib` no **nome** caixa e, em seguida, clique em **Okey**.  
  
     O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão. O namespace raiz é usado para qualificar os nomes dos componentes no assembly. Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`  
  
3.  No Gerenciador de Soluções, clique com o botão direito do mouse em **UserControl1.cs** e, em seguida, clique em **Renomear**. Altere o nome de arquivo para `ctlClock.cs`. Clique no botão **Sim** quando solicitado se deseja renomear todas as referências ao elemento de código “UserControl1”.  
  
    > [!NOTE]
    >  Por padrão, um controle de composição herda o <xref:System.Windows.Forms.UserControl> classe fornecida pelo sistema. O <xref:System.Windows.Forms.UserControl> classe fornece a funcionalidade requerida por todos os controles compostos e implementa propriedades e métodos padrão.  
  
4.  No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Adicionando controles e componentes do Windows ao controle de composição  
 Uma interface visual é uma parte essencial do controle de composição. Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer. Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Para adicionar um Rótulo e um Temporizador ao controle de composição  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.cs** e, em seguida, clique em **Exibir Designer**.  
  
2.  Na **Caixa de Ferramentas**, expanda o nó **Controles Comuns** e clique duas vezes em **Rótulo**.  
  
     Um <xref:System.Windows.Forms.Label> controle chamado `label1` é adicionado ao controle na superfície do designer.  
  
3.  No designer, clique em **label1**. Na janela Propriedades, defina as propriedades a seguir.  
  
    |Propriedade|Altere para|  
    |--------------|---------------|  
    |**Nome**|`lblDisplay`|  
    |**Texto**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.  
  
     Porque um <xref:System.Windows.Forms.Timer> é um componente, ele não tem representação visual em tempo de execução. Portanto, ele não é exibido com os controles na superfície do designer, mas no **Designer de Componentes** (uma bandeja na parte inferior da superfície do designer).  
  
5.  No **Component Designer**, clique em **timer1**e, em seguida, defina a <xref:System.Windows.Forms.Timer.Interval%2A> propriedade a ser `1000` e o <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade `true`.  
  
     O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a frequência com que o <xref:System.Windows.Forms.Timer> tiques do componente. A cada tique de `timer1`, ele executa o código no evento `timer1_Tick`. O intervalo representa o número de milissegundos entre os tiques.  
  
6.  No **Designer de Componentes**, clique duas vezes em **timer1** para acessar o evento `timer1_Tick` de `ctlClock`.  
  
7.  Modifique o código para que ele fique parecido com o exemplo de código a seguir. Lembre-se de alterar o modificador de acesso de `private` para `protected`.  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     Esse código fará com que a hora atual seja mostrada em `lblDisplay`. Como o intervalo de `timer1` foi definido como `1000`, esse evento ocorrerá a cada vários milhares de milissegundos, atualizando a hora atual a cada segundo.  
  
8.  Modifique o método para que ele seja substituível pela palavra-chave `virtual`. Para obter mais informações, consulte a seção “Herdando de um controle de usuário” abaixo.  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.  
  
## <a name="adding-properties-to-the-composite-control"></a>Adicionando propriedades ao controle de composição  
 O controle do relógio agora encapsula uma <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.Timer> componente, cada um com seu próprio conjunto de propriedades inerentes. Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados. No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>Para adicionar uma propriedade ao controle de composição  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.cs** e, em seguida, clique em **Exibir Código**.  
  
     O **Editor de Código** do controle é aberto.  
  
2.  Localize a instrução `public partial class ctlClock`. Sob a chave de abertura (`{)`, digite o código a seguir.  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.  
  
3.  Digite o código a seguir abaixo das declarações de variáveis da etapa 2.  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     O código anterior cria duas propriedades personalizadas, `ClockForeColor` e `ClockBackColor`, disponíveis para os próximos usuários desse controle. As instruções `get` e `set` fornecem armazenamento e recuperação do valor da propriedade, bem como o código para implementar a funcionalidade apropriada para a propriedade.  
  
4.  No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.  
  
## <a name="testing-the-control"></a>Testando o controle  
 Controles não são aplicativos autônomos; eles devem ser hospedados em um contêiner. Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**. Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).  
  
#### <a name="to-test-your-control"></a>Para testar o controle  
  
1.  Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.  
  
2.  Na grade de propriedades do contêiner de teste, localize a propriedade `ClockBackColor` e, em seguida, selecione a propriedade para exibir a paleta de cores.  
  
3.  Escolha uma cor clicando nela.  
  
     A cor da tela de fundo do controle é alterada para a cor selecionada.  
  
4.  Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.  
  
     Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição. Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão. Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.  
  
## <a name="inheriting-from-a-composite-control"></a>Herdando de um controle de composição  
 Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis. O controle de composição agora pode ser usado como base para a criação de outros controles. O processo de derivação de classe de uma classe base é chamado *herança*. Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`. Esse controle será derivado de seu controle pai, `ctlClock`. Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.  
  
 A primeira etapa na criação de um controle herdado é derivá-lo de seu pai. Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.  
  
#### <a name="to-create-the-inherited-control"></a>Para criar o controle herdado  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib**, aponte para **Adicionar** e, em seguida, clique em **Controle de Usuário**.  
  
     A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
2.  Selecione o modelo **Controle de Usuário Herdado**.  
  
3.  Na caixa **Nome**, digite `ctlAlarmClock.cs` e clique em **Adicionar**.  
  
     A caixa de diálogo **Seletor de Herança** é exibida.  
  
4.  Em **Nome do Componente**, clique duas vezes em **ctlClock**.  
  
5.  No Gerenciador de Soluções, procure os projetos atuais.  
  
    > [!NOTE]
    >  Um arquivo chamado **ctlAlarmClock.cs** foi adicionado ao projeto atual.  
  
### <a name="adding-the-alarm-properties"></a>Adicionando as propriedades de alarme  
 As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição. Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.  
  
##### <a name="to-add-properties-to-your-composite-control"></a>Para adicionar propriedades ao controle de composição  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Código**.  
  
2.  Localize a instrução `public class`. Observe que o controle herda de `ctlClockLib.ctlClock`. Sob a chave de abertura (instrução `{)`, digite o código a seguir.  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>Fazendo adições à interface gráfica do controle  
 O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado. Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas. Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição. Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.  
  
##### <a name="to-add-the-label-control"></a>Para adicionar o controle de rótulo  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Designer**.  
  
     O designer de `ctlAlarmClock` é aberto na janela principal.  
  
2.  Clique na parte de exibição do controle e exiba a janela Propriedades.  
  
    > [!NOTE]
    >  Embora todas as propriedades sejam exibidas, elas ficam esmaecidas. Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades. Por padrão, os controles contidos em um controle de composição são `private` e suas propriedades não são acessíveis por nenhum meio.  
  
    > [!NOTE]
    >  Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `public` ou `protected`. Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.  
  
3.  Adicionar um <xref:System.Windows.Forms.Label> controle ao controle de composição.  
  
4.  Usando o mouse, arraste o <xref:System.Windows.Forms.Label> controle imediatamente abaixo da caixa de exibição. Na janela Propriedades, defina as propriedades a seguir.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |**Nome**|`lblAlarm`|  
    |**Texto**|**Alarme!**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visível**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a>Adicionando a funcionalidade de alarme  
 Nos procedimentos anteriores, você adicionou propriedades e um controle que habilitarão a funcionalidade de alarme do controle de composição. Neste procedimento, você adicionará um código para comparar a hora atual com a hora do alarme e, se forem iguais, elas piscarão um alarme. Ao substituir o método `timer1_Tick` de `ctlClock` e adicionar um código adicional a ele, você estenderá a funcionalidade de `ctlAlarmClock` ao mesmo tempo que reterá todas as funcionalidades inerentes de `ctlClock`.  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>Para substituir o método timer1_Tick de ctlClock  
  
1.  No **Editor de códigos**, localize a instrução `private bool blnAlarmSet;`. Imediatamente abaixo dela, adicione a instrução a seguir.  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  No **Editor de códigos**, localize a chave de fechamento (`})` no final da classe. Antes da chave, adicione o código a seguir.  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     A adição desse código realiza várias tarefas. A instrução `override` direciona o controle a usar esse método em vez do método herdado do controle base. Quando esse método é chamado, ele chama o método que substitui ao invocar a instrução `base.timer1_Tick`, garantindo que toda a funcionalidade incorporada no controle original seja reproduzida nesse controle. Em seguida, ele executa um código adicional para incorporar a funcionalidade de alarme. Um controle de rótulo intermitente será exibido quando o alarme for acionado.  
  
     O controle do despertador está quase concluído. A única coisa que resta é implementar uma maneira de desligá-lo. Para fazer isso, você adicionará um código ao método `lblAlarm_Click`.  
  
##### <a name="to-implement-the-shutoff-method"></a>Para implementar o método de desligamento  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock.cs** e, em seguida, clique em **Exibir Designer**.  
  
     O designer será aberto.  
  
2.  Adicione um botão no controle. Defina as propriedades do botão da seguinte maneira.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |**Nome**|`btnAlarmOff`|  
    |**Texto**|**Desabilitar o alarme**|  
  
3.  No designer, clique duas vezes em **btnAlarmOff**.  
  
     O **Editor de Código** é aberto na linha `private void btnAlarmOff_Click`.  
  
4.  Modifique esse método para que ele fique parecido com o código a seguir.  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.  
  
### <a name="using-the-inherited-control-on-a-form"></a>Usando o controle herdado em um formulário  
 É possível testar o controle herdado da mesma maneira que você testou o controle de classe base, `ctlClock`: pressione F5 para compilar o projeto e execute o controle no **Contêiner de Teste de UserControl**. Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).  
  
 Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário. Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner. Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo. Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`. Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>Para criar e adicionar o controle a um formulário de teste  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib** e, em seguida, clique em **Compilar**.  
  
2.  Adicione um novo projeto **Aplicativo do Windows** à solução e nomeie-o `Test`.  
  
3.  Em Gerenciador de Soluções, clique com o botão direito do mouse no nó **Referências** para seu projeto de teste. Clique em **Adicionar referência** para exibir a caixa de diálogo **Adicionar referência**. Clique na guia rotulada como **Projetos**. O projeto `ctlClockLib` estará listado em **Nome do Projeto**. Clique duas vezes no projeto para adicionar a referência ao projeto de teste.  
  
4.  No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Compilar**.  
  
5.  Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.  
  
6.  Clique duas vezes em **ctlAlarmClock** para adicionar uma cópia de `ctlAlarmClock` ao seu formulário.  
  
7.  No **caixa de ferramentas**, localize e clique duas vezes em **DateTimePicker** para adicionar um <xref:System.Windows.Forms.DateTimePicker> controle ao seu formulário e, em seguida, adicione um <xref:System.Windows.Forms.Label> controle clicando duas vezes em **rótulo**.  
  
8.  Use o mouse para posicionar os controles em um local conveniente do formulário.  
  
9. Defina as propriedades desses controles conforme mostrado a seguir.  
  
    |Controle|Propriedade|Valor|  
    |-------------|--------------|-----------|  
    |`label1`|**Texto**|`(blank space)`|  
    ||**Nome**|`lblTest`|  
    |`dateTimePicker1`|**Nome**|`dtpTest`|  
    ||**Formatar**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. No designer, clique duas vezes em **dtpTest**.  
  
     O **Editor de Códigos** é aberto para `private void dtpTest_ValueChanged`.  
  
11. Modifique o código para que ele fique parecido com o mostrado a seguir.  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Definir como Projeto de Inicialização**.  
  
13. No menu **Depuração**, clique em **Iniciar Depuração**.  
  
     O programa de teste é iniciado. Observe que a hora atual é atualizada na `ctlAlarmClock` controle e que a hora de início é mostrada no <xref:System.Windows.Forms.DateTimePicker> controle.  
  
14. Clique o <xref:System.Windows.Forms.DateTimePicker> onde os minutos da hora são exibidos.  
  
15. Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.  
  
     A hora da configuração do alarme é mostrada em `lblTest`. Aguarde até que a hora exibida atinja a hora de configuração do alarme. Quando a hora exibida atingir a hora na qual o alarme está definido, o `lblAlarm` piscará.  
  
16. Desligue o alarme clicando em `btnAlarmOff`. Agora você pode redefinir o alarme.  
  
     Este passo a passo abordou alguns dos principais conceitos. Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição. Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada. Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.  
  
## <a name="see-also"></a>Consulte também  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Programação com componentes](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Instruções passo a passo para criação de componentes](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Passo a passo: herdando um controle dos Windows Forms com Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
