---
title: 'Passo a passo: Criar um botão usando o Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 1b4c775ea0680dcd8252a98c722dfe8f7e62548f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942501"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Passo a passo: Criar um botão usando o Microsoft Expression Blend
Estas instruções passo a passo demonstram o processo de criação de um botão personalizado [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usando o Microsoft Expression Blend.  
  
> [!IMPORTANT]
> O Microsoft Expression Blend gera um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], que é compilada para tornar o programa executável. Se você preferir trabalhar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] diretamente, há outro passo a passos que cria o mesmo aplicativo que aquele que usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] com o Visual Studio em vez de Blend. Consulte [Criar um botão usando XAML](walkthrough-create-a-button-by-using-xaml.md) para obter mais informações.  
  
 A ilustração a seguir mostra o botão personalizado que você criará.  
  
 ![O botão personalizado que você criará](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Converter uma forma em um botão  
 Na primeira parte deste passo a passo, você cria a aparência personalizada do botão personalizado. Para fazer isso, primeiramente deve converter um retângulo em um botão. Depois, acrescenta formas adicionais ao modelo do botão, criando um botão de aparência mais complexa. Por que não começar com um botão normal e personalizá-lo? Porque um botão tem funcionalidades internas das quais você não precisa; no caso de botões personalizados, é mais fácil começar com um retângulo.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Para criar um novo projeto no Expression Blend  
  
1. Inicie o Expression Blend. (Clique em **Iniciar**, aponte para **Todos os programas**, aponte para **Microsoft Expression** e, em seguida, clique em **Microsoft Expression Blend**.)  
  
2. Maximize o aplicativo, se necessário.  
  
3. No menu **Arquivo**, clique em **Novo Projeto**.  
  
4. Selecione **Aplicativo padrão (.exe)** .  
  
5. Nomeie o projeto `CustomButton` e pressione **OK**.  
  
 Neste ponto, você tem um projeto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] em branco. É possível pressionar F5 para executar o aplicativo. Como pode ser esperado, o aplicativo consiste em apenas uma janela em branco. Em seguida, você cria um retângulo arredondado e o converte em um botão.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Para converter um retângulo em um botão  
  
1. **Defina a propriedade de plano de fundo da janela como preto:** Selecione a janela, clique na **guia Propriedades**e defina a <xref:System.Windows.Controls.Control.Background%2A> Propriedade como `Black`.  
  
     ![Como definir a tela de fundo de um botão como preto](./media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2. **Desenhe um retângulo aproximadamente do tamanho de um botão na janela:** Selecione a ferramenta retângulo no painel de ferramentas à esquerda e arraste o retângulo para a janela.  
  
     ![Como desenhar um retângulo](./media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3. **Arredonde os cantos do retângulo:** Arraste os pontos de controle do retângulo ou defina diretamente as <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> Propriedades e. <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> Defina os valores de <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> para 20.  
  
     ![Como arredondar os cantos de um retângulo](./media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4. **Altere o retângulo para um botão:** Selecione o retângulo. No menu **Ferramentas**, clique em **Fazer botão**.  
  
     ![Como transformar uma forma em um botão](./media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5. **Especifique o escopo do estilo/modelo:** É exibida uma caixa de diálogo semelhante à seguinte.  
  
     ![A caixa de diálogo “Criar recurso de estilo”](./media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Para **Nome do recurso (chave)** , selecione **Aplicar a todos**.  Isso fará o estilo e o modelo de botão resultantes se aplicarem a todos os objetos que são botões. Para **Definir em**, selecione **Aplicativo**. Assim, o estilo e o modelo de botão resultantes terão escopo em todo o aplicativo. Quando você define os valores nas duas caixas, o estilo de botão e o modelo se aplicam a todos os botões em todo o aplicativo; qualquer botão criado no aplicativo usará esse modelo, por padrão.  
  
## <a name="edit-the-button-template"></a>Editar o modelo de botão  
 Agora, você tem um retângulo que foi transformado em um botão. Nesta seção, você modificará o modelo de botão e personalizará ainda mais sua aparência.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Para editar o modelo de botão a fim de alterar a aparência do botão  
  
1. **Vá para a exibição de modelo de edição:** Para personalizar ainda mais a aparência de nosso botão, precisamos editar o modelo de botão. Este modelo foi criado ao converter o retângulo em um botão. Para editar o modelo de botão, clique com o botão direito do mouse no botão e selecione **Editar partes do controle (modelo)** e, em seguida, **Editar modelo**.  
  
     ![Como editar um modelo](./media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     No editor de modelos, observe que o botão agora está separado em um <xref:System.Windows.Shapes.Rectangle> e no <xref:System.Windows.Controls.ContentPresenter>. O <xref:System.Windows.Controls.ContentPresenter> é usado para apresentar conteúdo dentro do botão (por exemplo, a cadeia de caracteres "Button"). O retângulo e <xref:System.Windows.Controls.ContentPresenter> o são dispostos dentro de um <xref:System.Windows.Controls.Grid>.  
  
     ![Componentes da apresentação de um retângulo](./media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2. **Altere os nomes dos componentes do modelo:** Clique com o botão direito do mouse no retângulo no inventário do <xref:System.Windows.Shapes.Rectangle> modelo, altere o nome de "[Rectangle]" para "outerRectangle" e altere "[ContentPresenter]" para "myContentPresenter".  
  
     ![Como renomear um componente de um modelo](./media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3. **Altere o retângulo para que ele fique vazio dentro (como uma rosca):** Selecione **outerRectangle** e defina <xref:System.Windows.Shapes.Shape.Fill%2A> como "transparente" e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> como 5.  
  
     ![Como esvaziar um retângulo](./media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Em seguida, <xref:System.Windows.Shapes.Shape.Stroke%2A> defina o como a cor de qualquer modelo. Para fazer isso, clique na caixa branca pequena ao lado de **Traço**, selecione **CustomExpression** e digite “{TemplateBinding Background}” na caixa de diálogo.  
  
     ![Como definir o uso de cor do modelo](./media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4. **Criar um retângulo interno:** Agora, crie outro retângulo (nomeie-o como "innerRectangle") e posicione-o simetricamente no interior de **outerRectangle** . Para esse tipo de trabalho, você provavelmente desejará aplicar zoom para ampliar o botão na área de edição.  
  
    > [!NOTE]
    > Seu retângulo pode ficar diferente da figura (por exemplo, pode ter cantos arredondados).  
  
     ![Como criar um retângulo dentro de outro retângulo](./media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5. **Mover ContentPresenter para a parte superior:** Neste ponto, é possível que o texto "botão" não fique mais visível. Isso ocorre porque o **innerRectangle** fica sobre o **myContentPresenter**. Para corrigir isso, arraste **myContentPresenter** para baixo de **innerRectangle**. Reposicione os retângulos e o **myContentPresenter** para terem uma aparência semelhante à aparência abaixo.  
  
    > [!NOTE]
    > Como alternativa, também é possível posicionar o **myContentPresenter** na parte superior clicando com o botão direito do mouse nele e pressionando **Encaminhar**.  
  
     ![Como mover um botão para a parte superior de outro botão](./media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6. **Altere a aparência de innerRectangle:** Defina os <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>valores <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> como 20. Além disso, defina o <xref:System.Windows.Shapes.Shape.Fill%2A> para o plano de fundo do modelo usando a expressão personalizada "{modelo de plano de fundo} <xref:System.Windows.Shapes.Shape.Stroke%2A> " e defina como "transparente". Observe <xref:System.Windows.Shapes.Shape.Fill%2A> que as configurações de e <xref:System.Windows.Shapes.Shape.Stroke%2A> de **innerRectangle** são o oposto delas para **outerRectangle**.  
  
     ![Como alterar a aparência de um retângulo](./media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7. **Adicione uma camada de vidro na parte superior:** A parte final da personalização da aparência do botão é adicionar uma camada de vidro na parte superior. Essa camada do vidro consiste em um terceiro retângulo. Como o vidro cobrirá o botão inteiro, o retângulo de vidro terá dimensões semelhantes às do **outerRectangle**. Portanto, para criar o retângulo, basta fazer uma cópia do **outerRectangle**. Destaque p **outerRectangle** e use CTRL+C e CTRL+V para fazer uma cópia. Nomeie esse novo retângulo como “glassCube”.  
  
8. **Reposicione glassCube se necessário:** Se **glassCube** já não estiver posicionado para que ele cubra o botão inteiro, arraste-o para a posição.  
  
9. **Dê ao glassCube uma forma um pouco diferente da outerRectangle:** Altere as propriedades de **glassCube**. Comece alterando as <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> Propriedades e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> para 10 e para o <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para 2.  
  
     ![As configurações de aparência para o glassCube](./media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Faça com que o glassCube pareça um vidro:** <xref:System.Windows.Shapes.Shape.Fill%2A> Defina como uma aparência de vidro usando um gradiente linear que seja de 75% opaco e alterna entre a cor branca e transparente em 6 intervalos de espaçamento uniforme. As marcas de gradiente devem ser definidas como:  
  
    - Parada de gradiente 1: Branco com valor alfa de 75%  
  
    - Parada de gradiente 2: Transparente  
  
    - Parada de gradiente 3: Branco com valor alfa de 75%  
  
    - Parada de gradiente 4: Transparente  
  
    - Parada de gradiente 5: Branco com valor alfa de 75%  
  
    - Parada do gradiente 6: Transparente  
  
     É criada uma aparência de vidro “ondulada”.  
  
     ![Um retângulo parecido com vidro](./media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Ocultar a camada de vidro:** Agora que você vê a aparência da camada de vidro, vá para o **painel aparência** do **painel Propriedades** e defina a opacidade como 0% para ocultá-la. Nas próximas seções, vamos usar gatilhos de propriedade e eventos para mostrar e manipular a camada de vidro.  
  
     ![Como ocultar o retângulo de vidro](./media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Personalizar o comportamento do botão  
 Neste ponto, você personalizou a apresentação do botão editando seu modelo; porém, o botão não reage a ações do usuário como botões comuns (por exemplo, mudando de aparência quando o mouse passa por cima, recebendo foco e clicando). Os próximos dois procedimentos mostram como criar comportamentos como esses em um botão personalizado. Começaremos com gatilhos de propriedade e, a seguir, adicionaremos gatilhos de evento e animações.  
  
#### <a name="to-set-property-triggers"></a>Para definir gatilhos de propriedade  
  
1. **Criar um novo gatilho de propriedade:** Com **glassCube** selecionado, clique em **+ Propriedade** no painel de **gatilhos** (consulte a figura que segue a próxima etapa). É criado um gatilho de propriedade com um gatilho de propriedade padrão.  
  
2. **Tornar IsMouseOver a propriedade usada pelo gatilho:** Altere a propriedade para <xref:System.Windows.UIElement.IsMouseOver%2A>. Isso faz com que o gatilho de propriedade <xref:System.Windows.UIElement.IsMouseOver%2A> seja ativado `true` quando a propriedade é (quando o usuário aponta para o botão com o mouse).  
  
     ![Como definir um gatilho em uma propriedade](./media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3. **IsMouseOver dispara a opacidade de 100% para glassCube:** Observe que a **gravação do gatilho está ativada** (consulte a figura anterior). Isso significa que qualquer alteração feita nos valores de propriedade de **glassCube** enquanto a gravação estiver ativada se tornará uma ação que ocorre <xref:System.Windows.UIElement.IsMouseOver%2A> quando `true`é. Durante a gravação, altere <xref:System.Windows.UIElement.Opacity%2A> o de **glassCube** para 100%.  
  
     ![Como definir a opacidade de um botão](./media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Você criou seu primeiro gatilho de propriedade. Observe que o **painel** de gatilhos do editor gravou o <xref:System.Windows.UIElement.Opacity%2A> que está sendo alterado para 100%.  
  
     ![O painel "Gatilhos"](./media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Pressione F5 para executar o aplicativo e mova o ponteiro do mouse sobre o botão e fora dele. A camada de vidro deve aparecer quando você passa o mouse sobre o botão e desaparecer quando o ponteiro sair.  
  
4. **Alteração de valor de traço de gatilhos IsMouseOver:** Vamos associar algumas outras ações ao <xref:System.Windows.UIElement.IsMouseOver%2A> gatilho. Enquanto o registro continua, mude a seleção de **glassCube** para **outerRectangle**. Em seguida, <xref:System.Windows.Shapes.Shape.Stroke%2A> defina o de **outerRectangle** para a expressão personalizada "{DynamicResource {x:static SystemColors. HighlightBrushKey}}". Isso define o <xref:System.Windows.Shapes.Shape.Stroke%2A> para a cor de realce típica usada pelos botões. Pressione F5 para ver o efeito ao passar o mouse sobre o botão.  
  
     ![Como definir o traço para a cor de destaque](./media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5. **O IsMouseOver dispara o texto borrado:** Vamos associar mais uma ação ao gatilho de <xref:System.Windows.UIElement.IsMouseOver%2A> propriedade. Faça o conteúdo do botão parecer um pouco desfocado quando o vidro aparecer sobre ele. Para fazer isso, podemos aplicar um desfoque <xref:System.Windows.Media.Effects.BitmapEffect> <xref:System.Windows.Controls.ContentPresenter> ao (myContentPresenter).  
  
     ![Como desfocar o conteúdo de um botão](./media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    > Para retornar o **painel Propriedades** para o que era antes da pesquisa <xref:System.Windows.Media.Effects.BitmapEffect>, limpe o texto da caixa de **pesquisa**.  
  
     Neste ponto, usamos um gatilho de propriedade com várias ações associadas para criar o comportamento de destaque para quando o ponteiro do mouse entrar e sair da área do botão. Outro comportamento comum para um botão é destacar quando ele tem o foco (como após ser clicado). Podemos adicionar esse comportamento adicionando outro gatilho de propriedade para a <xref:System.Windows.UIElement.IsFocused%2A> propriedade.  
  
6. **Criar gatilho de propriedade para IsFocused:** Usando o mesmo procedimento <xref:System.Windows.UIElement.IsMouseOver%2A> do (consulte a primeira etapa desta seção), crie outro gatilho de propriedade para a <xref:System.Windows.UIElement.IsFocused%2A> propriedade. Enquanto o **registro de gatilho estiver ativado**, adicione as ações a seguir ao gatilho:  
  
    - **glassCube** Obtém um <xref:System.Windows.UIElement.Opacity%2A> de 100%.  
  
    - **outerRectangle** Obtém um <xref:System.Windows.Shapes.Shape.Stroke%2A> valor de expressão personalizada de "{DynamicResource {x:static SystemColors. HighlightBrushKey}}".  
  
 Como etapa final deste passo a passo, adicionaremos animações ao botão. Essas animações serão disparadas por eventos – especificamente, <xref:System.Windows.UIElement.MouseEnter> os <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos e.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Para usar gatilhos de evento e animações para adicionar interatividade  
  
1. **Criar um gatilho de evento de MouseEnter:** Adicione um novo gatilho de evento e <xref:System.Windows.UIElement.MouseEnter> selecione como o evento a ser usado no gatilho.  
  
     ![Como criar um gatilho de evento MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2. **Criar uma linha do tempo de animação:** Em seguida, associe uma linha do tempo <xref:System.Windows.UIElement.MouseEnter> de animação ao evento.  
  
     ![Como adicionar uma linha do tempo da animação a um evento](./media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Depois de pressionar **OK** para criar uma nova linha do tempo, é exibido um **painel Linha do tempo** e “O registro da linha do tempo está ativado” fica visível no painel de design. Isso significa que podemos começar a registrar mudanças na propriedade na linha do tempo (mudanças na propriedade de animação).  
  
    > [!NOTE]
    > Talvez seja necessário redimensionar a janela e/ou painéis para ver a exibição.  
  
     ![O painel da linha do tempo](./media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3. **Criar um quadro chave:** Para criar uma animação, selecione o objeto que você deseja animar, crie dois ou mais quadros-chave na linha do tempo e, para esses quadros, defina os valores de propriedade que você deseja que a animação interpolara. A figura a seguir é uma orientação para a criação de um quadro chave.  
  
     ![Como criar um quadro chave](./media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4. **Reduzir glassCube neste quadro-chave:** Com o segundo quadro-chave selecionado, reduza o tamanho do **glassCube** para 90% de seu tamanho total usando a **transformação de tamanho**.  
  
     ![Como reduzir o tamanho de um botão](./media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Pressione F5 para executar o aplicativo. Mova o ponteiro do mouse sobre o botão. Observe que a camada do vidro é reduzida sobre o botão.  
  
5. **Crie outro gatilho de evento e associe uma animação diferente a ele:** Vamos adicionar mais uma animação. Use um procedimento semelhante ao que você usou para criar a animação anterior do gatilho de evento:  
  
    1. Crie um novo gatilho de evento usando <xref:System.Windows.Controls.Primitives.ButtonBase.Click> o evento.  
  
    2. Associe uma nova linha do tempo <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ao evento.  
  
     ![Como criar uma nova linha do tempo](./media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1. Para essa linha do tempo, crie dois quadros chave, em 0,0 segundos e, o segundo, em 0,3 segundos.  
  
    2. Com o quadro chave destacado em 0,3 segundos, defina o **ângulo de transformação de giro** como 360 graus.  
  
     ![Como criar uma transformação de giro](./media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1. Pressione F5 para executar o aplicativo. Clique no botão. Observe que a camada do vidro vai girar.  
  
## <a name="conclusion"></a>Conclusão  
 Você concluiu um botão personalizado. Para fazer isso, utilizou um modelo de botão que foi aplicado a todos os botões no aplicativo. Se você sair do modo de edição de modelo (consulte a figura a seguir) e criar mais botões, verá que a aparência e o comportamento deles são semelhantes aos do botão personalizado, não ao botão padrão.  
  
 ![O modelo de botão personalizado](./media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Vários botões que usam o mesmo modelo](./media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Pressione F5 para executar o aplicativo. Clique nos botões e observe como todos eles se comportam da mesma maneira.  
  
 Lembre-se de que enquanto você estava Personalizando o modelo, <xref:System.Windows.Shapes.Shape.Fill%2A> definiu a propriedade de <xref:System.Windows.Shapes.Shape.Stroke%2A> innerRectangle e a propriedade **outerRectangle** para o plano de fundo do modelo ({Binding background}). Por isso, quando definir a cor da tela de fundo dos botões individuais, a tela de fundo definida será utilizada para as respectivas propriedades. Tente alterar as telas de fundo agora. Na figura a seguir, gradientes diferentes são usados. Portanto, apesar de um modelo ser útil para a personalização total de controles como botões, controles com modelos ainda podem ser modificados para ter aparências distintas.  
  
 ![Botões com o mesmo modelo e aparências distintas](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Para concluir, durante o processo de personalização de um modelo de botão, você aprendeu a fazer o seguinte no Microsoft Expression Blend:  
  
- Personalize a aparência de um controle.  
  
- Defina gatilhos de propriedade. Os gatilhos de propriedade são muito úteis, porque podem ser utilizados na maioria dos objetos, não apenas em controles.  
  
- Defina gatilhos de evento. Os gatilhos de evento são muito úteis, porque podem ser utilizados na maioria dos objetos, não apenas em controles.  
  
- Crie animações.  
  
- Diversos: crie gradientes, adicione BitmapEffects, use transformações e defina as propriedades básicas dos objetos.  
  
## <a name="see-also"></a>Consulte também

- [Criar um botão usando XAML](walkthrough-create-a-button-by-using-xaml.md)
- [Estilo e modelagem](styling-and-templating.md)
- [Visão geral da animação](../graphics-multimedia/animation-overview.md)
- [Visão geral da pintura com cores sólidas e gradientes](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Visão geral dos efeitos de bitmap](../graphics-multimedia/bitmap-effects-overview.md)
