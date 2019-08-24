---
title: 'Passo a passo: Criando um controle composto com o Visual C#'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1af6c0e013f82569eed8d085df0249f4fb991bb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015686"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>Passo a passo: Criar um controle composto com C\#

Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas. Basicamente, um controle de composição é um componente com uma representação visual. Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor. Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles. Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`. Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.

## <a name="create-the-project"></a>Criar o projeto

Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock

1. No Visual Studio, crie um novo projeto de **biblioteca de controle Windows Forms** e nomeie-o **ctlClockLib**.

     O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão. O namespace raiz é usado para qualificar os nomes dos componentes no assembly. Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`

2. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **UserControl1.cs**e clique em Renomear. Altere o nome de arquivo para `ctlClock.cs`. Clique no botão **Sim** quando solicitado se deseja renomear todas as referências ao elemento de código “UserControl1”.

    > [!NOTE]
    > Por padrão, um controle composto é herdado <xref:System.Windows.Forms.UserControl> da classe fornecida pelo sistema. A <xref:System.Windows.Forms.UserControl> classe fornece a funcionalidade exigida por todos os controles de composição e implementa métodos e propriedades padrão.

3. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Adicionar controles e componentes do Windows ao controle composto

Uma interface visual é uma parte essencial do controle de composição. Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer. Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Para adicionar um Rótulo e um Temporizador ao controle de composição

1. No **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlClock.cs**e clique em **Designer de exibição**.

2. Na **Caixa de Ferramentas**, expanda o nó **Controles Comuns** e clique duas vezes em **Rótulo**.

     Um <xref:System.Windows.Forms.Label> controle chamado `label1` é adicionado ao seu controle na superfície do designer.

3. No designer, clique em **label1**. Na janela Propriedades, defina as propriedades a seguir.

    |Propriedade|Altere para|
    |--------------|---------------|
    |**Nome**|`lblDisplay`|
    |**Texto**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font.Size**|`14`|

4. Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.

     Como um <xref:System.Windows.Forms.Timer> é um componente, ele não tem nenhuma representação visual em tempo de execução. Portanto, ele não é exibido com os controles na superfície do designer, mas no **Designer de Componentes** (uma bandeja na parte inferior da superfície do designer).

5. No **Designer de componentes**, clique **em timer1**e defina a <xref:System.Windows.Forms.Timer.Interval%2A> Propriedade como `1000` e a <xref:System.Windows.Forms.Timer.Enabled%2A> Propriedade como `true`.

     A <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a frequência com a qual <xref:System.Windows.Forms.Timer> o componente é tique. A cada tique de `timer1`, ele executa o código no evento `timer1_Tick`. O intervalo representa o número de milissegundos entre os tiques.

6. No **Designer de Componentes**, clique duas vezes em **timer1** para acessar o evento `timer1_Tick` de `ctlClock`.

7. Modifique o código para que ele fique parecido com o exemplo de código a seguir. Lembre-se de alterar o modificador de acesso de `private` para `protected`.

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     Esse código fará com que a hora atual seja mostrada em `lblDisplay`. Como o intervalo de `timer1` foi definido como `1000`, esse evento ocorrerá a cada vários milhares de milissegundos, atualizando a hora atual a cada segundo.

8. Modifique o método para que ele seja substituível pela palavra-chave `virtual`. Para obter mais informações, consulte a seção “Herdando de um controle de usuário” abaixo.

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="add-properties-to-the-composite-control"></a>Adicionar propriedades ao controle composto

O controle de relógio agora encapsula um <xref:System.Windows.Forms.Label> controle e um <xref:System.Windows.Forms.Timer> componente, cada um com seu próprio conjunto de propriedades inerentes. Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados. No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.

### <a name="to-add-a-property-to-your-composite-control"></a>Para adicionar uma propriedade ao controle de composição

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlClock.cs**e clique em **Exibir código**.

     O **Editor de Código** do controle é aberto.

2. Localize a instrução `public partial class ctlClock`. Sob a chave de abertura (`{)`, digite o código a seguir.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.

3. Insira ou cole o código a seguir sob as declarações de variável da etapa 2.

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

4. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="test-the-control"></a>Testar o controle

Controles não são aplicativos autônomos; eles devem ser hospedados em um contêiner. Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.

### <a name="to-test-your-control"></a>Para testar o controle

1. Pressione **F5** para compilar o projeto e executar o controle no **contêiner de teste do UserControl**.

2. Na grade de propriedades do contêiner de teste, localize a propriedade `ClockBackColor` e, em seguida, selecione a propriedade para exibir a paleta de cores.

3. Escolha uma cor clicando nela.

   A cor da tela de fundo do controle é alterada para a cor selecionada.

4. Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.

   Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição. Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão. Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.

## <a name="inherit-from-a-composite-control"></a>Herdar de um controle composto

Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis. O controle de composição agora pode ser usado como base para a criação de outros controles. O processo de derivação de classe de uma classe base é chamado *herança*. Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`. Esse controle será derivado de seu controle pai, `ctlClock`. Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.

A primeira etapa na criação de um controle herdado é derivá-lo de seu pai. Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.

### <a name="to-create-the-inherited-control"></a>Para criar o controle herdado

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlClockLib**, aponte para **Adicionar**e clique em **controle de usuário**.

     A caixa de diálogo **Adicionar Novo Item** é aberta.

2. Selecione o modelo **Controle de Usuário Herdado**.

3. Na caixa **Nome**, digite `ctlAlarmClock.cs` e clique em **Adicionar**.

     A caixa de diálogo **Seletor de Herança** é exibida.

4. Em **Nome do Componente**, clique duas vezes em **ctlClock**.

5. Em **Gerenciador de soluções**, navegue pelos projetos atuais.

    > [!NOTE]
    > Um arquivo chamado **ctlAlarmClock.cs** foi adicionado ao projeto atual.

### <a name="add-the-alarm-properties"></a>Adicionar as propriedades do alarme

As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição. Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.

#### <a name="to-add-properties-to-your-composite-control"></a>Para adicionar propriedades ao controle de composição

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlAlarmClock**e clique em **Exibir código**.

2. Localize a instrução `public class`. Observe que o controle herda de `ctlClockLib.ctlClock`. Sob a chave de abertura (instrução `{)`, digite o código a seguir.

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

### <a name="add-to-the-graphical-interface-of-the-control"></a>Adicionar à interface gráfica do controle

O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado. Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas. Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição. Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.

#### <a name="to-add-the-label-control"></a>Para adicionar o controle de rótulo

1. No **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlAlarmClock**e clique em **Designer de exibição**.

     O designer de `ctlAlarmClock` é aberto na janela principal.

2. Clique na parte de exibição do controle e exiba a janela Propriedades.

    > [!NOTE]
    > Embora todas as propriedades sejam exibidas, elas ficam esmaecidas. Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades. Por padrão, os controles contidos em um controle de composição são `private` e suas propriedades não são acessíveis por nenhum meio.

    > [!NOTE]
    > Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `public` ou `protected`. Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.

3. Adicione um <xref:System.Windows.Forms.Label> controle ao seu controle composto.

4. Usando o mouse, arraste o <xref:System.Windows.Forms.Label> controle imediatamente abaixo da caixa de exibição. Na janela Propriedades, defina as propriedades a seguir.

    |Propriedade|Configuração|
    |--------------|-------------|
    |**Nome**|`lblAlarm`|
    |**Texto**|**Alarme!**|
    |**TextAlign**|`MiddleCenter`|
    |**Visível**|`false`|

### <a name="add-the-alarm-functionality"></a>Adicionar a funcionalidade de alarme

Nos procedimentos anteriores, você adicionou propriedades e um controle que habilitarão a funcionalidade de alarme do controle de composição. Neste procedimento, você adicionará um código para comparar a hora atual com a hora do alarme e, se forem iguais, elas piscarão um alarme. Ao substituir o método `timer1_Tick` de `ctlClock` e adicionar um código adicional a ele, você estenderá a funcionalidade de `ctlAlarmClock` ao mesmo tempo que reterá todas as funcionalidades inerentes de `ctlClock`.

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>Para substituir o método timer1_Tick de ctlClock

1. No **Editor de códigos**, localize a instrução `private bool blnAlarmSet;`. Imediatamente abaixo dela, adicione a instrução a seguir.

    ```csharp
    private bool blnColorTicker;
    ```

2. No **Editor de códigos**, localize a chave de fechamento (`})` no final da classe. Antes da chave, adicione o código a seguir.

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

#### <a name="to-implement-the-shutoff-method"></a>Para implementar o método de desligamento

1. No **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlAlarmClock.cs**e clique em **Designer de exibição**.

     O designer será aberto.

2. Adicione um botão no controle. Defina as propriedades do botão da seguinte maneira.

    |Propriedade|Valor|
    |--------------|-----------|
    |**Nome**|`btnAlarmOff`|
    |**Texto**|**Desabilitar o alarme**|

3. No designer, clique duas vezes em **btnAlarmOff**.

     O **Editor de Código** é aberto na linha `private void btnAlarmOff_Click`.

4. Modifique esse método para que ele fique parecido com o código a seguir.

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

### <a name="use-the-inherited-control-on-a-form"></a>Usar o controle herdado em um formulário

Você pode testar seu controle herdado da mesma maneira que testou o controle de classe `ctlClock`base,: Pressione **F5** para compilar o projeto e executar o controle no **contêiner de teste do UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.

Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário. Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner. Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo. Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`. Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Para criar e adicionar o controle a um formulário de teste

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **ctlClockLib**e clique em **Compilar**.

2. Adicione um novo projeto de **aplicativo do Windows** à solução e nomeie-o como **Test**.

3. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **referências** para seu projeto de teste. Clique em **Adicionar referência** para exibir a caixa de diálogo **Adicionar referência**. Clique na guia rotulada como **Projetos**. O projeto `ctlClockLib` estará listado em **Nome do Projeto**. Clique duas vezes no projeto para adicionar a referência ao projeto de teste.

4. No **Gerenciador de soluções**, clique com o botão direito do mouse em **teste**e clique em **Compilar**.

5. Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.

6. Clique duas vezes em **ctlAlarmClock** para adicionar uma cópia de `ctlAlarmClock` ao seu formulário.

7. Na **caixa de ferramentas**, localize e clique duas vezes em **DateTimePicker** para <xref:System.Windows.Forms.DateTimePicker> adicionar um controle ao formulário e, em seguida <xref:System.Windows.Forms.Label> , adicione um controle clicando duas vezes em **rótulo**.

8. Use o mouse para posicionar os controles em um local conveniente do formulário.

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

12. No **Gerenciador de soluções**, clique com o botão direito do mouse em **teste**e clique em **definir como projeto de inicialização**.

13. No menu **Depuração**, clique em **Iniciar Depuração**.

     O programa de teste é iniciado. Observe que a hora atual é atualizada no `ctlAlarmClock` controle e que a hora de início é mostrada <xref:System.Windows.Forms.DateTimePicker> no controle.

14. Clique no <xref:System.Windows.Forms.DateTimePicker> local em que os minutos da hora são exibidos.

15. Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.

     A hora da configuração do alarme é mostrada em `lblTest`. Aguarde até que a hora exibida atinja a hora de configuração do alarme. Quando a hora exibida atingir a hora na qual o alarme está definido, o `lblAlarm` piscará.

16. Desligue o alarme clicando em `btnAlarmOff`. Agora você pode redefinir o alarme.

Este artigo abordou vários conceitos importantes. Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição. Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada. Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.

## <a name="see-also"></a>Consulte também

- [Variedades de controles personalizados](varieties-of-custom-controls.md)
- [Como: Exibir um controle na caixa de diálogo escolher itens da Toolbox](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Passo a passo: Herdar de um controle de Windows Forms com o VisualC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
