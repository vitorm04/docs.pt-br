---
title: 'Passo a passo: Criar um botão usando o Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 3cf9d133aee5a2c3d93c1a464c96fdaebcf230f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018124"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Passo a passo: Criar um botão usando o Microsoft Expression Blend
Estas instruções passo a passo demonstram o processo de criação de um botão personalizado [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usando o Microsoft Expression Blend.  
  
> [!IMPORTANT]
>  O Microsoft Expression Blend gera um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], que é compilada para tornar o programa executável. Se você preferir trabalhar com [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] diretamente, há outro passo a passo que cria o mesmo aplicativo como este usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] com Visual Studio em vez de mesclagem. Consulte [Criar um botão usando XAML](walkthrough-create-a-button-by-using-xaml.md) para obter mais informações.  
  
 A ilustração a seguir mostra o botão personalizado que você criará.  
  
 ![O botão personalizado que você criará](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Converter uma forma em um botão  
 Na primeira parte deste passo a passo, você cria a aparência personalizada do botão personalizado. Para fazer isso, primeiramente deve converter um retângulo em um botão. Depois, acrescenta formas adicionais ao modelo do botão, criando um botão de aparência mais complexa. Por que não começar com um botão normal e personalizá-lo? Porque um botão tem funcionalidades internas das quais você não precisa; no caso de botões personalizados, é mais fácil começar com um retângulo.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Para criar um novo projeto no Expression Blend  
  
1. Inicie o Expression Blend. (Clique em **Iniciar**, aponte para **Todos os programas**, aponte para **Microsoft Expression** e, em seguida, clique em **Microsoft Expression Blend**.)  
  
2. Maximize o aplicativo, se necessário.  
  
3. No menu **Arquivo**, clique em **Novo Projeto**.  
  
4. Selecione **Aplicativo padrão (.exe)**.  
  
5. Nomeie o projeto `CustomButton` e pressione **OK**.  
  
 Neste ponto, você tem um projeto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] em branco. É possível pressionar F5 para executar o aplicativo. Como pode ser esperado, o aplicativo consiste em apenas uma janela em branco. Em seguida, você cria um retângulo arredondado e o converte em um botão.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Para converter um retângulo em um botão  
  
1. **Defina a propriedade Background da janela como preto:** Selecione a janela, clique no **guia propriedades**e defina as <xref:System.Windows.Controls.Control.Background%2A> propriedade `Black`.  
  
     ![Como definir a tela de fundo de um botão como preto](./media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2. **Desenhe um retângulo aproximadamente do tamanho de um botão na janela:** Selecione a ferramenta de retângulo no painel à esquerda de ferramenta e arraste o retângulo para a janela.  
  
     ![Como desenhar um retângulo](./media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3. **Harmonizar os cantos do retângulo:** Arraste os pontos de controle do retângulo ou defina diretamente a <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriedades. Defina os valores das <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> a 20.  
  
     ![Como arredondar os cantos de um retângulo](./media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4. **Altere o retângulo em um botão:** Selecione o retângulo. No menu **Ferramentas**, clique em **Fazer botão**.  
  
     ![Como transformar uma forma em um botão](./media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5. **Especifique o escopo do estilo/modelo:** Aparece uma caixa de diálogo semelhante à seguinte.  
  
     ![A caixa de diálogo “Criar recurso de estilo”](./media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Para **Nome do recurso (chave)**, selecione **Aplicar a todos**.  Isso fará o estilo e o modelo de botão resultantes se aplicarem a todos os objetos que são botões. Para **Definir em**, selecione **Aplicativo**. Assim, o estilo e o modelo de botão resultantes terão escopo em todo o aplicativo. Quando você define os valores nas duas caixas, o estilo de botão e o modelo se aplicam a todos os botões em todo o aplicativo; qualquer botão criado no aplicativo usará esse modelo, por padrão.  
  
## <a name="edit-the-button-template"></a>Editar o modelo de botão  
 Agora, você tem um retângulo que foi transformado em um botão. Nesta seção, você modificará o modelo de botão e personalizará ainda mais sua aparência.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Para editar o modelo de botão a fim de alterar a aparência do botão  
  
1. **Entrar no modo de exibição Editar modelo:** Para personalizar a aparência do botão, é necessário editar o modelo de botão. Este modelo foi criado ao converter o retângulo em um botão. Para editar o modelo de botão, clique com o botão direito do mouse no botão e selecione **Editar partes do controle (modelo)** e, em seguida, **Editar modelo**.  
  
     ![Como editar um modelo](./media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     No editor de modelo, observe que o botão foi separado em um <xref:System.Windows.Shapes.Rectangle> e o <xref:System.Windows.Controls.ContentPresenter>. O <xref:System.Windows.Controls.ContentPresenter> é usado para apresentar conteúdo dentro do botão (por exemplo, a cadeia de caracteres "Botão"). Os dois o retângulo e <xref:System.Windows.Controls.ContentPresenter> são dispostos dentro de um <xref:System.Windows.Controls.Grid>.  
  
     ![Componentes da apresentação de um retângulo](./media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2. **Altere os nomes dos componentes do modelo:** Clique com botão direito o retângulo no inventário do modelo, altere o <xref:System.Windows.Shapes.Rectangle> nome de "[Rectangle]" para "outerRectangle" e mude "[ContentPresenter]" para "myContentPresenter".  
  
     ![Como renomear um componente de um modelo](./media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3. **Altere o retângulo para que fique vazio no interior (como uma rosca):** Selecione **outerRectangle** e defina <xref:System.Windows.Shapes.Shape.Fill%2A> como "Transparent" e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para 5.  
  
     ![Como esvaziar um retângulo](./media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Em seguida, defina o <xref:System.Windows.Shapes.Shape.Stroke%2A> para a cor de tudo o que será o modelo. Para fazer isso, clique na caixa branca pequena ao lado de **Traço**, selecione **CustomExpression** e digite “{TemplateBinding Background}” na caixa de diálogo.  
  
     ![Como definir o uso de cor do modelo](./media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4. **Crie um retângulo interno:** Agora, crie outro retângulo (chame-o "innerRectangle") e posicione-o simetricamente dentro de **outerRectangle** . Para esse tipo de trabalho, você provavelmente desejará aplicar zoom para ampliar o botão na área de edição.  
  
    > [!NOTE]
    >  Seu retângulo pode ficar diferente da figura (por exemplo, pode ter cantos arredondados).  
  
     ![Como criar um retângulo dentro de outro retângulo](./media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5. **Mova o ContentPresenter para a parte superior:** Neste ponto, é possível que o texto "Botão" não será visível mais. Isso ocorre porque o **innerRectangle** fica sobre o **myContentPresenter**. Para corrigir isso, arraste **myContentPresenter** para baixo de **innerRectangle**. Reposicione os retângulos e o **myContentPresenter** para terem uma aparência semelhante à aparência abaixo.  
  
    > [!NOTE]
    >  Como alternativa, também é possível posicionar o **myContentPresenter** na parte superior clicando com o botão direito do mouse nele e pressionando **Encaminhar**.  
  
     ![Como mover um botão para a parte superior de outro botão](./media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6. **Altere a aparência do innerRectangle:** Defina as <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> valores como 20. Além disso, defina as <xref:System.Windows.Shapes.Shape.Fill%2A> ao plano de fundo do modelo usando a expressão personalizada "{TemplateBinding Background}") e defina <xref:System.Windows.Shapes.Shape.Stroke%2A> para "transparent". Observe que as configurações para o <xref:System.Windows.Shapes.Shape.Fill%2A> e <xref:System.Windows.Shapes.Shape.Stroke%2A> dos **innerRectangle** são o oposto do **outerRectangle**.  
  
     ![Como alterar a aparência de um retângulo](./media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7. **Adicione uma camada de vidro na parte superior:** A peça final da personalização da aparência do botão é adicionar uma camada de vidro na parte superior. Essa camada do vidro consiste em um terceiro retângulo. Como o vidro cobrirá o botão inteiro, o retângulo de vidro terá dimensões semelhantes às do **outerRectangle**. Portanto, para criar o retângulo, basta fazer uma cópia do **outerRectangle**. Destaque p **outerRectangle** e use CTRL+C e CTRL+V para fazer uma cópia. Nomeie esse novo retângulo como “glassCube”.  
  
8. **Reposicione o glassCube, se necessário:** Se **glassCube** é ainda não estiver posicionado de forma que ele abranja a todo o botão, arraste-o para a posição.  
  
9. **Dê ao glassCube uma forma ligeiramente diferente outerRectangle:** Alterar as propriedades de **glassCube**. Começar alterando a <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriedades para 10 e o <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para 2.  
  
     ![As configurações de aparência para o glassCube](./media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Verifique o glassCube aparência de vidro:** Defina o <xref:System.Windows.Shapes.Shape.Fill%2A> uma aparência vítrea ao usando um gradiente linear que seja 75% opaco e alterna entre as cores branco e transparente 6 aproximadamente uniformemente espaçados a intervalos. As marcas de gradiente devem ser definidas como:  
  
    - Parada de gradiente 1: Branco com valor alfa de 75%  
  
    - Parada de gradiente 2: Transparente  
  
    - Parada de gradiente 3: Branco com valor alfa de 75%  
  
    - Parada de gradiente 4: Transparente  
  
    - Parada de gradiente 5: Branco com valor alfa de 75%  
  
    - Parada de gradiente 6: Transparente  
  
     É criada uma aparência de vidro “ondulada”.  
  
     ![Um retângulo com aparência de vidro](./media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Oculte a camada do vidro:** Agora que você veja o que a aparência da camada vítrea, vá para o **painel aparência** da **painel de propriedades** e definir a opacidade como 0% para ocultá-la. Nas próximas seções, vamos usar gatilhos de propriedade e eventos para mostrar e manipular a camada de vidro.  
  
     ![Como ocultar o retângulo de vidro](./media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Personalizar o comportamento do botão  
 Neste ponto, você personalizou a apresentação do botão editando seu modelo; porém, o botão não reage a ações do usuário como botões comuns (por exemplo, mudando de aparência quando o mouse passa por cima, recebendo foco e clicando). Os próximos dois procedimentos mostram como criar comportamentos como esses em um botão personalizado. Começaremos com gatilhos de propriedade e, a seguir, adicionaremos gatilhos de evento e animações.  
  
#### <a name="to-set-property-triggers"></a>Para definir gatilhos de propriedade  
  
1. **Crie um novo gatilho de propriedade:** Com o **glassCube** selecionado, clique em **+ propriedade** no **gatilhos** painel (consulte a figura a seguir a próxima etapa). É criado um gatilho de propriedade com um gatilho de propriedade padrão.  
  
2. **Transforme IsMouseOver na propriedade usada pelo gatilho:** Altere a propriedade para <xref:System.Windows.UIElement.IsMouseOver%2A>. Isso faz com que o gatilho de propriedade Ativar quando a <xref:System.Windows.UIElement.IsMouseOver%2A> é de propriedade `true` (quando o usuário aponta para o botão com o mouse).  
  
     ![Como definir um gatilho em uma propriedade](./media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3. **IsMouseOver dispara uma opacidade de 100% para glassCube:** Observe que o **gravação de gatilho está** (consulte a figura anterior). Isso significa que as alterações feitas aos valores de propriedade de **glassCube** durante a gravação em se tornará uma ação que ocorre quando <xref:System.Windows.UIElement.IsMouseOver%2A> é `true`. Durante a gravação, alterar o <xref:System.Windows.UIElement.Opacity%2A> dos **glassCube** para 100%.  
  
     ![Como definir a opacidade de um botão](./media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Você criou seu primeiro gatilho de propriedade. Observe que o **painel gatilhos** do editor registrou a <xref:System.Windows.UIElement.Opacity%2A> que está sendo alterado para 100%.  
  
     ![O painel "Gatilhos"](./media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Pressione F5 para executar o aplicativo e mova o ponteiro do mouse sobre o botão e fora dele. A camada de vidro deve aparecer quando você passa o mouse sobre o botão e desaparecer quando o ponteiro sair.  
  
4. **IsMouseOver gatilhos traçar a alteração do valor:** Vamos associar outras ações com o <xref:System.Windows.UIElement.IsMouseOver%2A> gatilho. Enquanto o registro continua, mude a seleção de **glassCube** para **outerRectangle**. Em seguida, defina as <xref:System.Windows.Shapes.Shape.Stroke%2A> dos **outerRectangle** para a expressão personalizada de "{DynamicResource {X:Static Highlightbrushkey}}". Isso define o <xref:System.Windows.Shapes.Shape.Stroke%2A> para típica usada pelos botões de cor de realce. Pressione F5 para ver o efeito ao passar o mouse sobre o botão.  
  
     ![Como definir o traço para a cor de destaque](./media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5. **IsMouseOver dispara texto desfocado:** Vamos associar mais de uma ação para o <xref:System.Windows.UIElement.IsMouseOver%2A> disparador de propriedade. Faça o conteúdo do botão parecer um pouco desfocado quando o vidro aparecer sobre ele. Para fazer isso, podemos aplicar um desfoque <xref:System.Windows.Media.Effects.BitmapEffect> para o <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Como desfocar o conteúdo de um botão](./media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Para retornar o **painel de propriedades** volta ao que era antes de você a procure <xref:System.Windows.Media.Effects.BitmapEffect>, limpar o texto da **caixa de pesquisa**.  
  
     Neste ponto, usamos um gatilho de propriedade com várias ações associadas para criar o comportamento de destaque para quando o ponteiro do mouse entrar e sair da área do botão. Outro comportamento comum para um botão é destacar quando ele tem o foco (como após ser clicado). Podemos acrescentar tal comportamento adicionando outro gatilho de propriedade para o <xref:System.Windows.UIElement.IsFocused%2A> propriedade.  
  
6. **Crie gatilho de propriedade para IsFocused:** Usando o mesmo procedimento para <xref:System.Windows.UIElement.IsMouseOver%2A> (consulte a primeira etapa desta seção), crie outro gatilho de propriedade para o <xref:System.Windows.UIElement.IsFocused%2A> propriedade. Enquanto o **registro de gatilho estiver ativado**, adicione as ações a seguir ao gatilho:  
  
    - **glassCube** obtém um <xref:System.Windows.UIElement.Opacity%2A> de 100%.  
  
    - **outerRectangle** obtém um <xref:System.Windows.Shapes.Shape.Stroke%2A> valor de expressão personalizada de "{DynamicResource {X:Static Highlightbrushkey}}".  
  
 Como etapa final deste passo a passo, adicionaremos animações ao botão. Essas animações serão disparadas por eventos — especificamente, o <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Para usar gatilhos de evento e animações para adicionar interatividade  
  
1. **Crie um gatilho de evento MouseEnter:** Adicione um novo gatilho de evento e selecione <xref:System.Windows.UIElement.MouseEnter> como o evento para usar no gatilho.  
  
     ![Como criar um gatilho de evento MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2. **Crie uma linha do tempo de animação:** Em seguida, associe uma linha do tempo de animação para o <xref:System.Windows.UIElement.MouseEnter> eventos.  
  
     ![Como adicionar uma linha do tempo da animação a um evento](./media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Depois de pressionar **OK** para criar uma nova linha do tempo, é exibido um **painel Linha do tempo** e “O registro da linha do tempo está ativado” fica visível no painel de design. Isso significa que podemos começar a registrar mudanças na propriedade na linha do tempo (mudanças na propriedade de animação).  
  
    > [!NOTE]
    >  Talvez seja necessário redimensionar a janela e/ou painéis para ver a exibição.  
  
     ![O painel da linha do tempo](./media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3. **Crie um quadro-chave:** Para criar uma animação, selecione o objeto que você deseja animar, crie duas ou mais quadros chave na linha do tempo e para esses quadros chave, defina os valores de propriedade que você deseja que a animação para interpolar entre. A figura a seguir é uma orientação para a criação de um quadro chave.  
  
     ![Como criar um quadro chave](./media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4. **Reduza glassCube neste quadro chave:** Com o segundo quadro chave selecionado, reduzir o tamanho do **glassCube** a 90% de seu tamanho total usando o **transformar tamanho**.  
  
     ![Como reduzir o tamanho de um botão](./media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Pressione F5 para executar o aplicativo. Mova o ponteiro do mouse sobre o botão. Observe que a camada do vidro é reduzida sobre o botão.  
  
5. **Crie outro gatilho de evento e associe uma animação diferente ele:** Vamos adicionar mais uma animação. Use um procedimento semelhante ao que você usou para criar a animação anterior do gatilho de evento:  
  
    1. Criar um novo gatilho de evento usando o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
    2. Associar uma nova linha do tempo com o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
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
  
 Lembre-se de que, enquanto estava Personalizando o modelo, você defina as <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade de **innerRectangle** e o <xref:System.Windows.Shapes.Shape.Stroke%2A> propriedade **outerRectangle** no plano de fundo do modelo ({ TemplateBinding Background}). Por isso, quando definir a cor da tela de fundo dos botões individuais, a tela de fundo definida será utilizada para as respectivas propriedades. Tente alterar as telas de fundo agora. Na figura a seguir, gradientes diferentes são usados. Portanto, apesar de um modelo ser útil para a personalização total de controles como botões, controles com modelos ainda podem ser modificados para ter aparências distintas.  
  
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
