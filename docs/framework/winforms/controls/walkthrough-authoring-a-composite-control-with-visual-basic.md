---
title: 'Passo a passo: Criar um controle composto com o Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: abfb91c61ef72bfc1626b4cc4dcea42b75e2ab35
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040236"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>Passo a passo: Criar um controle composto com o Visual Basic
Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas. Basicamente, um controle de composição é um componente com uma representação visual. Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor. Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles. Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`. Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.

## <a name="creating-the-project"></a>Criando o Projeto
 Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock

1. No menu **Arquivo**, aponte para **Novo** e clique em **Projeto** para abrir a caixa de diálogo **Novo Projeto**.

2. Na lista de projetos de Visual Basic, selecione o modelo de projeto da biblioteca de controle `ctlClockLib` do **Windows** , digite na caixa **nome** e clique em **OK**.

     O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão. O namespace raiz é usado para qualificar os nomes dos componentes no assembly. Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`

3. No Gerenciador de Soluções, clique com o botão direito do mouse em **UserControl1.vb** e, em seguida, clique em **Renomear**. Altere o nome de arquivo para `ctlClock.vb`. Clique no botão **Sim** quando solicitado se deseja renomear todas as referências ao elemento de código “UserControl1”.

    > [!NOTE]
    >  Por padrão, um controle composto é herdado <xref:System.Windows.Forms.UserControl> da classe fornecida pelo sistema. A <xref:System.Windows.Forms.UserControl> classe fornece a funcionalidade exigida por todos os controles de composição e implementa métodos e propriedades padrão.

4. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>Adicionando controles e componentes do Windows ao controle de composição
 Uma interface visual é uma parte essencial do controle de composição. Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer. Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Para adicionar um Rótulo e um Temporizador ao controle de composição

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.vb** e, em seguida, clique em **Exibir Designer**.

2. Na Caixa de Ferramentas, expanda o nó **Controles Comuns** e clique duas vezes em **Rótulo**.

     Um <xref:System.Windows.Forms.Label> controle chamado `Label1` é adicionado ao seu controle na superfície do designer.

3. No designer, clique em **Label1**. Na janela Propriedades, defina as propriedades a seguir.

    |Propriedade|Altere para|
    |--------------|---------------|
    |**Nome**|`lblDisplay`|
    |**Texto**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font.Size**|`14`|

4. Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.

     Como um <xref:System.Windows.Forms.Timer> é um componente, ele não tem nenhuma representação visual em tempo de execução. Portanto, ele não é exibido com os controles na superfície do designer, mas no Designer de Componentes (uma bandeja na parte inferior da superfície do designer).

5. No designer de componentes, clique em **Timer1**e <xref:System.Windows.Forms.Timer.Interval%2A> defina a propriedade como `1000` e a <xref:System.Windows.Forms.Timer.Enabled%2A> Propriedade como `True`.

     A <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a frequência com a qual o componente de timer é tique. A cada tique de `Timer1`, ele executa o código no evento `Timer1_Tick`. O intervalo representa o número de milissegundos entre os tiques.

6. No Designer de Componentes, clique duas vezes em **Timer1** para acessar o evento `Timer1_Tick` de `ctlClock`.

7. Modifique o código para que ele fique parecido com o exemplo de código a seguir. Lembre-se de alterar o modificador de acesso de `Private` para `Protected`.

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     Esse código fará com que a hora atual seja mostrada em `lblDisplay`. Como o intervalo de `Timer1` foi definido como `1000`, esse evento ocorrerá a cada vários milhares de milissegundos, atualizando a hora atual a cada segundo.

8. Modifique o método para que ele seja substituível. Para obter mais informações, consulte a seção “Herdando de um controle de usuário” abaixo.

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="adding-properties-to-the-composite-control"></a>Adicionando propriedades ao controle de composição
 O controle de relógio agora encapsula um <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.Timer> componente, cada um com seu próprio conjunto de propriedades inerentes. Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados. No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.

### <a name="to-add-a-property-to-your-composite-control"></a>Para adicionar uma propriedade ao controle de composição

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClock.vb** e, em seguida, clique em **Exibir Código**.

     O Editor de Código do controle é aberto.

2. Localize a instrução `Public Class ctlClock`. Abaixo dela, digite o código a seguir.

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.

3. Insira o código a seguir abaixo das declarações de variáveis da etapa 2.

    ```vb
    ' Declares the name and type of the property.
    Property ClockBackColor() as Color
        ' Retrieves the value of the private variable colBColor.
        Get
            Return colBColor
        End Get
        ' Stores the selected value in the private variable colBColor, and
        ' updates the background color of the label control lblDisplay.
        Set(ByVal value as Color)
            colBColor = value
            lblDisplay.BackColor = colBColor
        End Set

    End Property
    ' Provides a similar set of instructions for the foreground color.
    Property ClockForeColor() as Color
        Get
            Return colFColor
        End Get
        Set(ByVal value as Color)
            colFColor = value
            lblDisplay.ForeColor = colFColor
        End Set
    End Property
    ```

     O código anterior cria duas propriedades personalizadas, `ClockForeColor` e `ClockBackColor`, disponíveis para os próximos usuários desse controle com a invocação da instrução `Property`. As instruções `Get` e `Set` fornecem armazenamento e recuperação do valor da propriedade, bem como o código para implementar a funcionalidade apropriada para a propriedade.

4. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="testing-the-control"></a>Testando o controle
 Controles não são projetos autônomos; eles devem ser hospedados em um contêiner. Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.

### <a name="to-test-your-control"></a>Para testar o controle

1. Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**.

2. Na grade de propriedades do contêiner de teste, selecione a propriedade `ClockBackColor` e, em seguida, clique na seta suspensa para exibir a paleta de cores.

3. Escolha uma cor clicando nela.

     A cor da tela de fundo do controle é alterada para a cor selecionada.

4. Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.

5. Clique em **Fechar** para fechar o **Contêiner de Teste de UserControl**.

     Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição. Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão. Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.

## <a name="inheriting-from-a-composite-control"></a>Herdando de um controle de composição
 Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis. O controle de composição agora pode ser usado como base para a criação de outros controles. O processo de derivação de classe de uma classe base é chamado *herança*. Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`. Esse controle será derivado de seu controle pai, `ctlClock`. Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.

 A primeira etapa na criação de um controle herdado é derivá-lo de seu pai. Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.

### <a name="to-create-the-inherited-control"></a>Para criar o controle herdado

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib**, aponte para **Adicionar** e, em seguida, clique em **Controle de Usuário**.

     A caixa de diálogo **Adicionar Novo Item** é aberta.

2. Selecione o modelo **Controle de Usuário Herdado**.

3. Na caixa **Nome**, digite `ctlAlarmClock.vb` e clique em **Adicionar**.

     A caixa de diálogo **Seletor de Herança** é exibida.

4. Em **Nome do Componente**, clique duas vezes em **ctlClock**.

5. No Gerenciador de Soluções, procure os projetos atuais.

    > [!NOTE]
    >  Um arquivo chamado **ctlAlarmClock.vb** foi adicionado ao projeto atual.

### <a name="adding-the-alarm-properties"></a>Adicionando as propriedades de alarme
 As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição. Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.

#### <a name="to-add-properties-to-your-composite-control"></a>Para adicionar propriedades ao controle de composição

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Código**.

2. Localize a declaração de classe do controle ctlAlarmClock, que aparece como `Public Class ctlAlarmClock`.  Na declaração de classe, insira o código a seguir.

    ```vb
    Private dteAlarmTime As Date
    Private blnAlarmSet As Boolean
    ' These properties will be declared as Public to allow future
    ' developers to access them.
    Public Property AlarmTime() As Date
        Get
            Return dteAlarmTime
        End Get
        Set(ByVal value as Date)
            dteAlarmTime = value
        End Set
    End Property
    Public Property AlarmSet() As Boolean
        Get
            Return blnAlarmSet
        End Get
        Set(ByVal value as Boolean)
            blnAlarmSet = value
        End Set
    End Property
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a>Fazendo adições à interface gráfica do controle
 O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado. Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas. Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição. Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.

#### <a name="to-add-the-label-control"></a>Para adicionar o controle de rótulo

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock** e, em seguida, clique em **Exibir Designer**.

     O designer de `ctlAlarmClock` é aberto na janela principal.

2. Clique em `lblDisplay` (a parte de exibição do controle) e exiba a janela Propriedades.

    > [!NOTE]
    >  Embora todas as propriedades sejam exibidas, elas ficam esmaecidas. Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades. Por padrão, os controles contidos em um controle de composição são `Private` e suas propriedades não são acessíveis por nenhum meio.

    > [!NOTE]
    >  Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `Public` ou `Protected`. Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.

3. Adicione um <xref:System.Windows.Forms.Label> controle ao seu controle composto.

4. Usando o mouse, arraste o <xref:System.Windows.Forms.Label> controle imediatamente abaixo da caixa de exibição. Na janela Propriedades, defina as propriedades a seguir.

    |Propriedade|Configuração|
    |--------------|-------------|
    |**Nome**|`lblAlarm`|
    |**Texto**|**Alarme!**|
    |**TextAlign**|`MiddleCenter`|
    |**Visível**|`False`|

### <a name="adding-the-alarm-functionality"></a>Adicionando a funcionalidade de alarme
 Nos procedimentos anteriores, você adicionou propriedades e um controle que habilitarão a funcionalidade de alarme do controle de composição. Neste procedimento, você adicionará um código para comparar a hora atual com a hora do alarme e, se forem iguais, elas soarão e piscarão um alarme. Ao substituir o método `Timer1_Tick` de `ctlClock` e adicionar um código adicional a ele, você estenderá a funcionalidade de `ctlAlarmClock` ao mesmo tempo que reterá todas as funcionalidades inerentes de `ctlClock`.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Para substituir o método Timer1_Tick de ctlClock

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock.vb** e, em seguida, clique em **Exibir Código**.

2. Localize a instrução `Private blnAlarmSet As Boolean`. Imediatamente abaixo dela, adicione a instrução a seguir.

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. Localize a instrução `End Class` na parte inferior da página. Logo antes da instrução `End Class`, adicione o código a seguir.

    ```vb
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _
        As System.EventArgs)
        ' Calls the Timer1_Tick method of ctlClock.
        MyBase.Timer1_Tick(sender, e)
        ' Checks to see if the Alarm is set.
        If AlarmSet = False Then
            Exit Sub
        End If
        ' If the date, hour, and minute of the alarm time are the same as
        ' now, flash and beep an alarm.
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _
            AlarmTime.Minute = Now.Minute Then
            ' Sounds an audible beep.
            Beep()
            ' Sets lblAlarmVisible to True, and changes the background color based on the
            ' value of blnColorTicker. The background color of the label will
            ' flash once per tick of the clock.
            lblAlarm.Visible = True
            If blnColorTicker = False Then
                lblAlarm.BackColor = Color.PeachPuff
                blnColorTicker = True
            Else
                lblAlarm.BackColor = Color.Plum
                blnColorTicker = False
            End If
        Else
            ' Once the alarm has sounded for a minute, the label is made
            ' invisible again.
            lblAlarm.Visible = False
        End If
    End Sub
    ```

     A adição desse código realiza várias tarefas. A instrução `Overrides` direciona o controle a usar esse método em vez do método herdado do controle base. Quando esse método é chamado, ele chama o método que substitui ao invocar a instrução `MyBase.Timer1_Tick`, garantindo que toda a funcionalidade incorporada no controle original seja reproduzida nesse controle. Em seguida, ele executa um código adicional para incorporar a funcionalidade de alarme. Um controle de rótulo intermitente será exibido quando o alarme for acionado e um alarme sonoro audível será ouvido.

    > [!NOTE]
    >  Como você está substituindo um manipulador de eventos herdado, você não precisa especificar o evento com a palavra-chave `Handles`. O evento já está vinculado. O que você está substituindo é a implementação do manipulador.

     O controle do despertador está quase concluído. A única coisa que resta é implementar uma maneira de desligá-lo. Para fazer isso, você adicionará um código ao método `lblAlarm_Click`.

#### <a name="to-implement-the-shutoff-method"></a>Para implementar o método de desligamento

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlAlarmClock.vb** e, em seguida, clique em **Exibir Designer**.

2. No designer, clique duas vezes em **lblAlarm**. O **Editor de Código** é aberto na linha `Private Sub lblAlarm_Click`.

3. Modifique esse método para que ele fique parecido com o código a seguir.

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

### <a name="using-the-inherited-control-on-a-form"></a>Usando o controle herdado em um formulário
 Você pode testar seu controle herdado da mesma maneira que testou o controle de classe `ctlClock`base,: Pressione F5 para compilar o projeto e execute seu controle no **Contêiner de Teste de UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.

 Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário. Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner. Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo. Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`. Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Para criar e adicionar o controle a um formulário de teste

1. No Gerenciador de Soluções, clique com o botão direito do mouse em **ctlClockLib** e, em seguida, clique em **Compilar**.

2. No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto**.

3. Adicione um novo projeto **Aplicativo do Windows** à solução e nomeie-o `Test`.

     O projeto **Teste** é adicionado ao Gerenciador de Soluções.

4. No Gerenciador de Soluções, clique com o botão direito do mouse no nó de projeto `Test` e, em seguida, clique em **Adicionar Referência** para exibir a caixa de diálogo **Adicionar Referência**.

5. Clique na guia rotulada como **Projetos**. O projeto **ctlClockLib** estará listado em **Nome do Projeto**. Clique duas vezes em **ctlClockLib** para adicionar a referência ao projeto de teste.

6. No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Compilar**.

7. Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.

8. Clique duas vezes em **ctlAlarmClock** para adicionar uma instância de `ctlAlarmClock` ao formulário.

9. Na **caixa de ferramentas**, localize e clique duas vezes em **DateTimePicker** para <xref:System.Windows.Forms.DateTimePicker> adicionar um controle ao formulário e, em seguida <xref:System.Windows.Forms.Label> , adicione um controle clicando duas vezes em **rótulo**.

10. Use o mouse para posicionar os controles em um local conveniente do formulário.

11. Defina as propriedades desses controles conforme mostrado a seguir.

    |Controle|Propriedade|Valor|
    |-------------|--------------|-----------|
    |`label1`|**Texto**|`(blank space)`|
    ||**Nome**|`lblTest`|
    |`dateTimePicker1`|**Nome**|`dtpTest`|
    ||**Formatar**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. No designer, clique duas vezes em **dtpTest**.

     O **Editor de Códigos** é aberto para `Private Sub dtpTest_ValueChanged`.

13. Modifique o código para que ele fique parecido com o mostrado a seguir.

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. No Gerenciador de Soluções, clique com o botão direito do mouse em **Testar** e, em seguida, clique em **Definir como Projeto de Inicialização**.

15. No menu **Depuração**, clique em **Iniciar Depuração**.

     O programa de teste é iniciado. Observe que a hora atual é atualizada no `ctlAlarmClock` controle e que a hora de início é mostrada <xref:System.Windows.Forms.DateTimePicker> no controle.

16. Clique no <xref:System.Windows.Forms.DateTimePicker> local em que os minutos da hora são exibidos.

17. Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.

     A hora da configuração do alarme é mostrada em `lblTest`. Aguarde até que a hora exibida atinja a hora de configuração do alarme. Quando a hora exibida atingir a hora na qual o alarme está definido, o alarme sonoro soará e `lblAlarm` piscará.

18. Desligue o alarme clicando em `lblAlarm`. Agora você pode redefinir o alarme.

     Este passo a passo abordou alguns dos principais conceitos. Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição. Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada. Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como: Controles de composição de autor](how-to-author-composite-controls.md)
- [Como: Exibir um controle na caixa de diálogo escolher itens da Toolbox](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
