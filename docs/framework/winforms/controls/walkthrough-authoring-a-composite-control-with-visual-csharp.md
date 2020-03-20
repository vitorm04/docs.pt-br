---
title: 'Instruções passo a passo: criando um controle composto com o Visual C#'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546718"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a>Passo a passo: Autor de um Controle Composto com C\#

Os controles de composição fornecem um meio pelo qual as interfaces gráficas personalizadas podem ser criadas e reutilizadas. Basicamente, um controle de composição é um componente com uma representação visual. Assim, ele pode consistir em um ou mais controles, componentes ou blocos de código dos Windows Forms que podem estender a funcionalidade ao validar a entrada do usuário, modificar propriedades de exibição ou executar outras tarefas exigidas pelo autor. Os controles de composição podem ser colocados nos Windows Forms da mesma maneira que outros controles. Na primeira parte deste passo a passo, você cria um controle de composição simples chamado `ctlClock`. Na segunda parte do passo a passo, você estende a funcionalidade de `ctlClock` por meio da herança.

## <a name="create-the-project"></a>Criar o projeto

Ao criar um novo projeto, você especifica seu nome para definir o namespace raiz, o nome do assembly e o nome do projeto e garante que o componente padrão estará no namespace correto.

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>Para criar a biblioteca de controles de ctlClockLib e o controle ctlClock

1. No Visual Studio, crie um novo projeto **da Biblioteca de Controle de Formulários do Windows** e nomeie-o **ctlClockLib**.

     O nome do projeto, `ctlClockLib`, também é atribuído ao namespace raiz por padrão. O namespace raiz é usado para qualificar os nomes dos componentes no assembly. Por exemplo, se dois assemblies fornecem componentes chamados `ctlClock`, será possível especificar o componente `ctlClock` usando `ctlClockLib.ctlClock.`

2. No **Solution Explorer**, clique com o botão direito do **UserControl1.cs**e clique em **Renomear**. Altere o nome de arquivo para `ctlClock.cs`. Clique no botão **Sim** quando for perguntado se deseja renomear todas as referências ao elemento de código "UserControl1".

    > [!NOTE]
    > Por padrão, um controle composto <xref:System.Windows.Forms.UserControl> herda da classe fornecida pelo sistema. A <xref:System.Windows.Forms.UserControl> classe fornece a funcionalidade exigida por todos os controles compostos e implementa métodos e propriedades padrão.

3. No menu **Arquivo**, clique em **Salvar Tudo** para salvar o projeto.

## <a name="add-windows-controls-and-components-to-the-composite-control"></a>Adicionar controles e componentes do Windows ao controle composto

Uma interface visual é uma parte essencial do controle de composição. Essa interface visual é implementada pela adição de um ou mais controles do Windows à superfície do designer. Na demonstração a seguir, você incorporará controles do Windows no controle de composição e escreverá um código para implementar a funcionalidade.

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>Para adicionar um Rótulo e um Temporizador ao controle de composição

1. No **Solution Explorer,** clique com o botão **direito do ctlClock.cs**e clique em Exibir **Designer**.

2. Na **caixa de ferramentas,** expanda o nó **Controles comuns** e clique duas vezes em **Etiqueta**.

     Um <xref:System.Windows.Forms.Label> controle `label1` nomeado é adicionado ao seu controle na superfície do designer.

3. No designer, clique **em label1**. Na janela Propriedades, defina as propriedades a seguir.

    |Propriedade|Altere para|
    |--------------|---------------|
    |**Nome**|`lblDisplay`|
    |**Texto**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Fonte.Tamanho**|`14`|

4. Na **Caixa de Ferramentas**, expanda o nó **Componentes** e clique duas vezes em **Temporizador**.

     Porque <xref:System.Windows.Forms.Timer> a é um componente, ele não tem representação visual no tempo de execução. Portanto, ele não aparece com os controles na superfície do designer, mas sim no **Component Designer** (uma bandeja na parte inferior da superfície do designer).

5. No **Designer de componentes,** clique em <xref:System.Windows.Forms.Timer.Interval%2A> **timer1**e, em seguida, defina a propriedade para e a `1000` <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade para `true`.

     A <xref:System.Windows.Forms.Timer.Interval%2A> propriedade controla a <xref:System.Windows.Forms.Timer> frequência com que o componente marca. A cada tique de `timer1`, ele executa o código no evento `timer1_Tick`. O intervalo representa o número de milissegundos entre os tiques.

6. No **Component Designer**, **temporizador** de `timer1_Tick` dois `ctlClock`cliques1 para ir ao evento para .

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

Seu controle de relógio <xref:System.Windows.Forms.Label> agora encapsula <xref:System.Windows.Forms.Timer> um controle e um componente, cada um com seu próprio conjunto de propriedades inerentes. Embora as propriedades individuais desses controles não estejam acessíveis aos próximos usuários do controle, você poderá criar e expor propriedades personalizadas, escrevendo os blocos de código apropriados. No procedimento a seguir, você adicionará propriedades ao controle que permitem ao usuário alterar a cor da tela de fundo e do texto.

### <a name="to-add-a-property-to-your-composite-control"></a>Para adicionar uma propriedade ao controle de composição

1. No **Solution Explorer,** clique com o botão **direito do ctlClock.cs**e clique em **'Exibir código '**.

     O **Editor de Códigos** para o seu controle é aberto.

2. Localize a instrução `public partial class ctlClock`. Sob a chave de abertura (`{)`, digite o código a seguir.

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     Essas instruções criam as variáveis particulares que você usará para armazenar os valores para as propriedades que está prestes a criar.

3. Digite ou cole o seguinte código abaixo das declarações variáveis da etapa 2.

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

## <a name="test-the-control"></a>Teste o Controle

Controles não são aplicativos autônomos; eles devem ser hospedados em um contêiner. Teste o comportamento do tempo de execução do controle e exerça suas propriedades com o **Contêiner de Teste de UserControl**. Para obter mais informações, consulte [Como testar o comportamento em tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

### <a name="to-test-your-control"></a>Para testar o controle

1. Pressione **F5** para construir o projeto e execute seu controle no **contêiner de teste UserControl**.

2. Na grade de propriedades do contêiner de teste, localize a propriedade `ClockBackColor` e, em seguida, selecione a propriedade para exibir a paleta de cores.

3. Escolha uma cor clicando nela.

   A cor da tela de fundo do controle é alterada para a cor selecionada.

4. Use uma sequência semelhante de eventos para verificar se a propriedade `ClockForeColor` está funcionando como esperado.

   Nesta seção e nas seções anteriores, você viu como os componentes e controles do Windows podem ser combinados com um código e empacotamento para fornecer funcionalidade personalizada na forma de um controle de composição. Você aprendeu a expor as propriedades no controle de composição e a testar o controle após sua conclusão. Na próxima seção, você aprenderá a construir um controle de composição herdado usando `ctlClock` como base.

## <a name="inherit-from-a-composite-control"></a>Herdar de um controle composto

Nas seções anteriores, você aprendeu a combinar controles, componentes e código do Windows em controles de composição reutilizáveis. O controle de composição agora pode ser usado como base para a criação de outros controles. O processo de derivação de classe de uma classe base é chamado *herança*. Nesta seção, você criará um controle de composição chamado `ctlAlarmClock`. Esse controle será derivado de seu controle pai, `ctlClock`. Você aprenderá a estender a funcionalidade de `ctlClock`, substituindo métodos pai e adicionando novos métodos e novas propriedades.

A primeira etapa na criação de um controle herdado é derivá-lo de seu pai. Essa ação cria um novo controle que tem todas as propriedades, métodos e características gráficas do controle pai, mas que também pode atuar como uma base para a adição de uma funcionalidade nova ou modificada.

### <a name="to-create-the-inherited-control"></a>Para criar o controle herdado

1. No **Solution Explorer**, clique com o botão direito do mouse **ctlClockLib,** aponte para **Adicionar**e clique em Controle **do Usuário**.

     A caixa de diálogo **Adicionar Novo Item** é aberta.

2. Selecione o modelo **Controle de Usuário Herdado**.

3. Na caixa **Nome**, digite `ctlAlarmClock.cs` e clique em **Adicionar**.

     A caixa de diálogo **Seletor de Herança** é exibida.

4. Em **Nome do Componente**, clique duas vezes em **ctlClock**.

5. No **Solution Explorer,** navegue pelos projetos atuais.

    > [!NOTE]
    > Um arquivo chamado **ctlAlarmClock.cs** foi adicionado ao projeto atual.

### <a name="add-the-alarm-properties"></a>Adicione as propriedades do alarme

As propriedades são adicionadas a um controle herdado da mesma forma que são adicionadas a um controle de composição. Agora você usará a sintaxe de declaração de propriedade para adicionar duas propriedades ao controle: `AlarmTime`, que armazenará o valor de data e hora em que o alarme será acionado e `AlarmSet`, que indicará se o alarme está definido.

#### <a name="to-add-properties-to-your-composite-control"></a>Para adicionar propriedades ao controle de composição

1. No **Solution Explorer,** clique com o botão direito do **mouse ctlAlarmClock**e clique **em Exibir Código**.

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

### <a name="add-to-the-graphical-interface-of-the-control"></a>Adicionar à Interface Gráfica do Controle

O controle herdado tem uma interface visual que é idêntica ao controle do qual ele é herdado. Ele contém os mesmos controles constituintes que seu controle pai, mas as propriedades dos controles constituintes só estarão disponíveis se forem especificamente expostas. Você pode fazer adições à interface gráfica de um controle de composição herdado da mesma maneira como faria com qualquer controle de composição. Para continuar fazendo adições à interface visual do despertador, você adicionará um controle de rótulo que piscará quando o alarme estiver soando.

#### <a name="to-add-the-label-control"></a>Para adicionar o controle de rótulo

1. No **Solution Explorer**, clique com o botão direito do mouse **ctlAlarmClock**e clique em Exibir **Designer**.

     O designer de `ctlAlarmClock` é aberto na janela principal.

2. Clique na parte de exibição do controle e exiba a janela Propriedades.

    > [!NOTE]
    > Embora todas as propriedades sejam exibidas, elas ficam esmaecidas. Isso indica que essas propriedades são nativas de `lblDisplay` e não podem ser modificadas nem acessadas na janela Propriedades. Por padrão, os controles contidos em um controle de composição são `private` e suas propriedades não são acessíveis por nenhum meio.

    > [!NOTE]
    > Se você desejar que os próximos usuários do controle de composição tenham acesso a seus controles internos, declare-os como `public` ou `protected`. Isso permitirá definir e modificar as propriedades de controles contidos no controle de composição usando o código apropriado.

3. Adicione <xref:System.Windows.Forms.Label> um controle ao seu controle composto.

4. Usando o mouse, <xref:System.Windows.Forms.Label> arraste o controle imediatamente abaixo da caixa de exibição. Na janela Propriedades, defina as propriedades a seguir.

    |Propriedade|Configuração|
    |--------------|-------------|
    |**Nome**|`lblAlarm`|
    |**Texto**|**Alarme!**|
    |**TextAlign**|`MiddleCenter`|
    |**Visível**|`false`|

### <a name="add-the-alarm-functionality"></a>Adicione a funcionalidade do alarme

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

1. No **Solution Explorer,** clique com o botão **direito do ctlAlarmClock.cs**e clique em Exibir **Designer**.

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

### <a name="use-the-inherited-control-on-a-form"></a>Use o Controle Herdado em um formulário

Você pode testar seu controle herdado da mesma `ctlClock`forma que testou o controle de classe base: Pressione **F5** para construir o projeto e executar seu controle no **Contêiner de Teste UserControl**. Para obter mais informações, consulte [Como testar o comportamento em tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Para colocar o controle em funcionamento, você precisará hospedá-lo em um formulário. Assim como ocorre com um controle de composição padrão, um controle de composição herdado não pode ser autônomo e deve ser hospedado em um formulário ou em outro contêiner. Já que `ctlAlarmClock` tem uma profundidade maior de funcionalidade, um código adicional é necessário para testá-lo. Neste procedimento, você escreverá um programa simples para testar a funcionalidade de `ctlAlarmClock`. Você escreverá um código para definir e exibir a propriedade `AlarmTime` de `ctlAlarmClock` e testará suas funções inerentes.

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>Para criar e adicionar o controle a um formulário de teste

1. No **Solution Explorer**, clique com o botão direito do mouse **ctlClockLib**e clique em **Build**.

2. Adicione um novo projeto **de aplicativo de formulários** do Windows à solução e nomeie-o **teste**.

3. No **Solution Explorer,** clique com o botão direito do mouse no nó **Referências** para o projeto de teste. Clique em **Adicionar referência** para exibir a caixa de diálogo **Adicionar referência**. Clique na guia rotulada como **Projetos**. O projeto `ctlClockLib` estará listado em **Nome do Projeto**. Clique duas vezes no projeto para adicionar a referência ao projeto de teste.

4. No **Solution Explorer,** clique com o botão direito do **mouse em Teste**e clique em **Build**.

5. Na **Caixa de Ferramentas**, expanda o nó **Componentes de ctlClockLib**.

6. Clique duas vezes em **ctlAlarmClock** para adicionar uma cópia de `ctlAlarmClock` ao seu formulário.

7. Na **caixa de ferramentas**, localize e clique <xref:System.Windows.Forms.DateTimePicker> duas vezes em **DateTimePicker** para adicionar um controle ao seu formulário e, em seguida, adicione um <xref:System.Windows.Forms.Label> controle clicando duas vezes em **Etiqueta**.

8. Use o mouse para posicionar os controles em um local conveniente do formulário.

9. Defina as propriedades desses controles conforme mostrado a seguir.

    |Control|Propriedade|Valor|
    |-------------|--------------|-----------|
    |`label1`|**Texto**|`(blank space)`|
    ||**Nome**|`lblTest`|
    |`dateTimePicker1`|**Nome**|`dtpTest`|
    ||**Formato**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

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

12. No **Solution Explorer,** clique com o botão direito do **mouse em Teste**e clique em Definir como Projeto **startup**.

13. No menu **Debug,** clique em **Iniciar depuração**.

     O programa de teste é iniciado. Observe que o tempo atual `ctlAlarmClock` é atualizado no controle, e <xref:System.Windows.Forms.DateTimePicker> que o tempo de partida é mostrado no controle.

14. Clique <xref:System.Windows.Forms.DateTimePicker> no local onde os minutos da hora são exibidos.

15. Usando o teclado, defina um valor de minutos que tem um minuto a mais que a hora atual mostrada por `ctlAlarmClock`.

     A hora da configuração do alarme é mostrada em `lblTest`. Aguarde até que a hora exibida atinja a hora de configuração do alarme. Quando a hora exibida atingir a hora na qual o alarme está definido, o `lblAlarm` piscará.

16. Desligue o alarme clicando em `btnAlarmOff`. Agora você pode redefinir o alarme.

Este artigo abordou uma série de conceitos-chave. Você aprendeu a criar um controle de composição, combinando controles e componentes em um contêiner de controle de composição. Você aprendeu a adicionar propriedades ao controle e a escrever um código para implementar a funcionalidade personalizada. Na última seção, você aprendeu a estender a funcionalidade de determinado controle de composição por meio da herança e a alterar a funcionalidade dos métodos do host ao substituí-los.

## <a name="see-also"></a>Confira também

- [Variedades de Controles Personalizados](varieties-of-custom-controls.md)
- [Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Instruções passo a passo: herdando um controle dos Windows Forms com Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
