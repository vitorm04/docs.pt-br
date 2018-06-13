---
title: 'Instruções passo a passo: criar um botão usando o Microsoft Expression Blend'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 55585aba8f734b4796c7ba63bcb840acac2c58c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558012"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Instruções passo a passo: criar um botão usando o Microsoft Expression Blend
Estas instruções passo a passo demonstram o processo de criação de um botão personalizado [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usando o Microsoft Expression Blend.  
  
> [!IMPORTANT]
>  O Microsoft Expression Blend gera um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], que é compilada para tornar o programa executável. Se você preferir trabalhar com [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] diretamente, há outra passo a passo que cria o mesmo aplicativo como isso usando um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] com Visual Studio, em vez de mesclagem. Consulte [Criar um botão usando XAML](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md) para obter mais informações.  
  
 A ilustração a seguir mostra o botão personalizado que você criará.  
  
 ![O botão personalizado que você criará](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")  
  
## <a name="convert-a-shape-to-a-button"></a>Converter uma forma em um botão  
 Na primeira parte deste passo a passo, você cria a aparência personalizada do botão personalizado. Para fazer isso, primeiramente deve converter um retângulo em um botão. Depois, acrescenta formas adicionais ao modelo do botão, criando um botão de aparência mais complexa. Por que não começar com um botão normal e personalizá-lo? Porque um botão tem funcionalidades internas das quais você não precisa; no caso de botões personalizados, é mais fácil começar com um retângulo.  
  
#### <a name="to-create-a-new-project-in-expression-blend"></a>Para criar um novo projeto no Expression Blend  
  
1.  Inicie o Expression Blend. (Clique em **Iniciar**, aponte para **Todos os programas**, aponte para **Microsoft Expression** e, em seguida, clique em **Microsoft Expression Blend**.)  
  
2.  Maximize o aplicativo, se necessário.  
  
3.  No menu **Arquivo**, clique em **Novo Projeto**.  
  
4.  Selecione **Aplicativo padrão (.exe)**.  
  
5.  Nomeie o projeto `CustomButton` e pressione **OK**.  
  
 Neste ponto, você tem um projeto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] em branco. É possível pressionar F5 para executar o aplicativo. Como pode ser esperado, o aplicativo consiste em apenas uma janela em branco. Em seguida, você cria um retângulo arredondado e o converte em um botão.  
  
#### <a name="to-convert-a-rectangle-to-a-button"></a>Para converter um retângulo em um botão  
  
1.  **Defina a propriedade de plano de fundo da janela para preto:** selecione a janela, clique no **guia propriedades**e defina o <xref:System.Windows.Controls.Control.Background%2A> propriedade `Black`.  
  
     ![Como definir a tela de fundo de um botão como preto](../../../../docs/framework/wpf/controls/media/custom-button-blend-changebackground.png "custom_button_blend_ChangeBackground")  
  
2.  **Desenhe um retângulo aproximadamente do tamanho de um botão na janela:** selecione a ferramenta de retângulo no painel de ferramentas do lado esquerdo e arraste o retângulo para a janela.  
  
     ![Como desenhar um retângulo](../../../../docs/framework/wpf/controls/media/custom-button-blend-drawrect.png "custom_button_blend_DrawRect")  
  
3.  **Complementam os cantos do retângulo:** arraste os pontos de controle do retângulo ou definir diretamente a <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriedades. Defina os valores de <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> a 20.  
  
     ![Como arredondar os cantos de um retângulo](../../../../docs/framework/wpf/controls/media/custom-button-blend-roundcorners.png "custom_button_blend_RoundCorners")  
  
4.  **Altere o retângulo para um botão:** selecione o retângulo. No menu **Ferramentas**, clique em **Fazer botão**.  
  
     ![Como transformar uma forma em um botão](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton.png "custom_button_blend_MakeButton")  
  
5.  **Especifique o escopo do estilo/modelo:** será exibida uma caixa de diálogo semelhante a esta.  
  
     ![A caixa de diálogo “Criar recurso de estilo”](../../../../docs/framework/wpf/controls/media/custom-button-blend-makebutton2.gif "custom_button_blend_MakeButton2")  
  
     Para **Nome do recurso (chave)**, selecione **Aplicar a todos**.  Isso fará o estilo e o modelo de botão resultantes se aplicarem a todos os objetos que são botões. Para **Definir em**, selecione **Aplicativo**. Assim, o estilo e o modelo de botão resultantes terão escopo em todo o aplicativo. Quando você define os valores nas duas caixas, o estilo de botão e o modelo se aplicam a todos os botões em todo o aplicativo; qualquer botão criado no aplicativo usará esse modelo, por padrão.  
  
## <a name="edit-the-button-template"></a>Editar o modelo de botão  
 Agora, você tem um retângulo que foi transformado em um botão. Nesta seção, você modificará o modelo de botão e personalizará ainda mais sua aparência.  
  
#### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Para editar o modelo de botão a fim de alterar a aparência do botão  
  
1.  **Acesse o modo de exibição Editar modelo:** para personalizar ainda mais a aparência do botão, precisamos editar o modelo de botão. Este modelo foi criado ao converter o retângulo em um botão. Para editar o modelo de botão, clique com o botão direito do mouse no botão e selecione **Editar partes do controle (modelo)** e, em seguida, **Editar modelo**.  
  
     ![Como editar um modelo](../../../../docs/framework/wpf/controls/media/custom-button-blend-edittemplate.jpg "custom_button_blend_EditTemplate")  
  
     No editor de modelo, observe que o botão agora é separado em um <xref:System.Windows.Shapes.Rectangle> e <xref:System.Windows.Controls.ContentPresenter>. O <xref:System.Windows.Controls.ContentPresenter> é usado para apresentar conteúdo dentro do botão (por exemplo, a cadeia de caracteres "Button"). Ambos o retângulo e <xref:System.Windows.Controls.ContentPresenter> são dispostos dentro de um <xref:System.Windows.Controls.Grid>.  
  
     ![Componentes da apresentação de um retângulo](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatepanel.png "custom_button_blend_TemplatePanel")  
  
2.  **Alterar os nomes dos componentes do modelo:** com o botão direito do retângulo no inventário do modelo, altere o <xref:System.Windows.Shapes.Rectangle> nome de "[retângulo]" para "outerRectangle" e altere "[ContentPresenter]" para "myContentPresenter".  
  
     ![Como renomear um componente de um modelo](../../../../docs/framework/wpf/controls/media/custom-button-blend-renamecomponents.png "custom_button_blend_RenameComponents")  
  
3.  **Alterar o retângulo para que ela está vazia dentro (como uma rosca):** selecione **outerRectangle** e defina <xref:System.Windows.Shapes.Shape.Fill%2A> como "Transparente" e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para 5.  
  
     ![Como esvaziar um retângulo](../../../../docs/framework/wpf/controls/media/custom-button-blend-changerectproperties.png "custom_button_blend_ChangeRectProperties")  
  
     Em seguida, defina o <xref:System.Windows.Shapes.Shape.Stroke%2A> para a cor que será o modelo. Para fazer isso, clique na caixa branca pequena ao lado de **Traço**, selecione **CustomExpression** e digite “{TemplateBinding Background}” na caixa de diálogo.  
  
     ![Como definir o uso de cor do modelo](../../../../docs/framework/wpf/controls/media/custom-button-blend-templatestroke.png "custom_button_blend_TemplateStroke")  
  
4.  **Crie um retângulo interno:** agora, crie outro retângulo (chame-o de “innerRectangle”) e posicione-o simetricamente dentro do **outerRectangle** . Para esse tipo de trabalho, você provavelmente desejará aplicar zoom para ampliar o botão na área de edição.  
  
    > [!NOTE]
    >  Seu retângulo pode ficar diferente da figura (por exemplo, pode ter cantos arredondados).  
  
     ![Como criar um retângulo dentro de outro retângulo](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangleproperties.png "custom_button_blend_innerRectangleProperties")  
  
5.  **Mova o ContentPresenter para a parte superior:** neste ponto, é possível que o texto “Botão” não esteja mais visível. Isso ocorre porque o **innerRectangle** fica sobre o **myContentPresenter**. Para corrigir isso, arraste **myContentPresenter** para baixo de **innerRectangle**. Reposicione os retângulos e o **myContentPresenter** para terem uma aparência semelhante à aparência abaixo.  
  
    > [!NOTE]
    >  Como alternativa, também é possível posicionar o **myContentPresenter** na parte superior clicando com o botão direito do mouse nele e pressionando **Encaminhar**.  
  
     ![Como mover um botão para a parte superior de outro botão](../../../../docs/framework/wpf/controls/media/custom-button-blend-innerrectangle2.png "custom_button_blend_innerRectangle2")  
  
6.  **Alterar a aparência de innerRectangle:** definir o <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>, e <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> valores para 20. In addition, defina o <xref:System.Windows.Shapes.Shape.Fill%2A> ao plano de fundo do modelo usando a expressão personalizada "{TemplateBinding plano}") e defina <xref:System.Windows.Shapes.Shape.Stroke%2A> como "transparente". Observe que as configurações para o <xref:System.Windows.Shapes.Shape.Fill%2A> e <xref:System.Windows.Shapes.Shape.Stroke%2A> de **innerRectangle** são o oposto dos para **outerRectangle**.  
  
     ![Como alterar a aparência de um retângulo](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties1.png "custom_button_blend_glassRectangleProperties1")  
  
7.  **Adicione uma camada de vidro na parte superior:** a peça final da personalização da aparência do botão é adicionar uma camada de vidro na parte superior. Essa camada do vidro consiste em um terceiro retângulo. Como o vidro cobrirá o botão inteiro, o retângulo de vidro terá dimensões semelhantes às do **outerRectangle**. Portanto, para criar o retângulo, basta fazer uma cópia do **outerRectangle**. Destaque p **outerRectangle** e use CTRL+C e CTRL+V para fazer uma cópia. Nomeie esse novo retângulo como “glassCube”.  
  
8.  **Reposicione o glassCube, se necessário:** caso o **glassCube** ainda não esteja posicionado para cobrir o botão inteiro, arraste-o até a posição.  
  
9. **Dê ao glassCube uma forma um pouco diferente da do outerRectangle:** mude as propriedades do **glassCube**. Começar alterando o <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> e <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> propriedades para 10 e o <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> para 2.  
  
     ![As configurações de aparência para o glassCube](../../../../docs/framework/wpf/controls/media/custom-button-blend-glasscubeappearance.gif "custom_button_blend_GlassCubeAppearance")  
  
10. **Fazer glassCube a aparência de vidro:** definir o <xref:System.Windows.Shapes.Shape.Fill%2A> uma aparência vítreo usando um gradiente linear que é de 75% opaco e alterna entre a cor branco e transparente 6 aproximadamente uniformemente espaçados intervalos. As marcas de gradiente devem ser definidas como:  
  
    -   Marca de gradiente 1: branco com valor alfa de 75%  
  
    -   Marca de gradiente 2: transparente  
  
    -   Marca de gradiente 3: branco com valor alfa de 75%  
  
    -   Marca de gradiente 4: transparente  
  
    -   Marca de gradiente 5: branco com valor alfa de 75%  
  
    -   Marca de gradiente 6: transparente  
  
     É criada uma aparência de vidro “ondulada”.  
  
     ![Um retângulo com aparência de vidro](../../../../docs/framework/wpf/controls/media/custom-button-blend-glassrectangleproperties2.png "custom_button_blend_glassRectangleProperties2")  
  
11. **Oculte a camada de vidro:** depois de ver qual é a aparência da camada vítrea, acesse o **painel Aparência** do **painel Propriedades** e defina a opacidade como 0% para ocultá-la. Nas próximas seções, vamos usar gatilhos de propriedade e eventos para mostrar e manipular a camada de vidro.  
  
     ![Como ocultar o retângulo de vidro](../../../../docs/framework/wpf/controls/media/custom-button-glassrectangleproperties3.gif "custom_button_glassRectangleProperties3")  
  
## <a name="customize-the-button-behavior"></a>Personalizar o comportamento do botão  
 Neste ponto, você personalizou a apresentação do botão editando seu modelo; porém, o botão não reage a ações do usuário como botões comuns (por exemplo, mudando de aparência quando o mouse passa por cima, recebendo foco e clicando). Os próximos dois procedimentos mostram como criar comportamentos como esses em um botão personalizado. Começaremos com gatilhos de propriedade e, a seguir, adicionaremos gatilhos de evento e animações.  
  
#### <a name="to-set-property-triggers"></a>Para definir gatilhos de propriedade  
  
1.  **Crie um novo gatilho de propriedade:** com **glassCube** selecionado, clique em **+ Propriedade**, no painel **Gatilhos** (veja a figura após a próxima etapa). É criado um gatilho de propriedade com um gatilho de propriedade padrão.  
  
2.  **Tornar IsMouseOver a propriedade usada pelo gatilho:** alterar a propriedade como <xref:System.Windows.UIElement.IsMouseOver%2A>. Isso faz com que o disparador de propriedade Ativar quando a <xref:System.Windows.UIElement.IsMouseOver%2A> é de propriedade `true` (quando o usuário aponta para o botão com o mouse).  
  
     ![Como definir um gatilho em uma propriedade](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger.png "custom_button_blend_IsMousedOverPropertyTrigger")  
  
3.  **IsMouseOver dispara uma opacidade de 100% para glassCube:** observe que o **registro do gatilho está ativado** (veja a figura anterior). Isso significa que as alterações feitas aos valores de propriedade de **glassCube** durante a gravação em se tornará uma ação que ocorre quando <xref:System.Windows.UIElement.IsMouseOver%2A> é `true`. Durante a gravação, altere o <xref:System.Windows.UIElement.Opacity%2A> de **glassCube** a 100%.  
  
     ![Como definir a opacidade de um botão](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger2.gif "custom_button_blend_IsMousedOverPropertyTrigger2")  
  
     Você criou seu primeiro gatilho de propriedade. Observe que o **painel gatilhos** do editor registrou o <xref:System.Windows.UIElement.Opacity%2A> que está sendo alterado para 100%.  
  
     ![O painel "Gatilhos"](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
     Pressione F5 para executar o aplicativo e mova o ponteiro do mouse sobre o botão e fora dele. A camada de vidro deve aparecer quando você passa o mouse sobre o botão e desaparecer quando o ponteiro sair.  
  
4.  **Gatilhos IsMouseOver traçar a alteração de valor:** permite associar algumas outras ações com o <xref:System.Windows.UIElement.IsMouseOver%2A> gatilho. Enquanto o registro continua, mude a seleção de **glassCube** para **outerRectangle**. Em seguida, defina o <xref:System.Windows.Shapes.Shape.Stroke%2A> de **outerRectangle** para a expressão personalizada de "{DynamicResource {X:Static SystemColors.HighlightBrushKey}}". Isso define o <xref:System.Windows.Shapes.Shape.Stroke%2A> para o típico realçar cor usada por botões. Pressione F5 para ver o efeito ao passar o mouse sobre o botão.  
  
     ![Como definir o traço para a cor de destaque](../../../../docs/framework/wpf/controls/media/custom-button-blend-ismousedoverpropertytrigger3.png "custom_button_blend_IsMousedOverPropertyTrigger3")  
  
5.  **IsMouseOver dispara texto borrado:** permite associar um mais ações para o <xref:System.Windows.UIElement.IsMouseOver%2A> disparador de propriedade. Faça o conteúdo do botão parecer um pouco desfocado quando o vidro aparecer sobre ele. Para fazer isso, é possível aplicar um desfoque <xref:System.Windows.Media.Effects.BitmapEffect> para o <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).  
  
     ![Como desfocar o conteúdo de um botão](../../../../docs/framework/wpf/controls/media/custom-button-blend-propertytriggerwithbitmapeffect.png "custom_button_blend_PropertyTriggerWithBitMapEffect")  
  
    > [!NOTE]
    >  Para retornar o **painel de propriedades** voltar ao que era antes de você procurar <xref:System.Windows.Media.Effects.BitmapEffect>, limpe o texto do **caixa de pesquisa**.  
  
     Neste ponto, usamos um gatilho de propriedade com várias ações associadas para criar o comportamento de destaque para quando o ponteiro do mouse entrar e sair da área do botão. Outro comportamento comum para um botão é destacar quando ele tem o foco (como após ser clicado). Podemos adicionar esse comportamento adicionando outro disparador de propriedade para o <xref:System.Windows.UIElement.IsFocused%2A> propriedade.  
  
6.  **Criar o disparador de propriedade para IsFocused:** usando o mesmo procedimento para <xref:System.Windows.UIElement.IsMouseOver%2A> (consulte a primeira etapa desta seção), crie outro gatilho de propriedade para o <xref:System.Windows.UIElement.IsFocused%2A> propriedade. Enquanto o **registro de gatilho estiver ativado**, adicione as ações a seguir ao gatilho:  
  
    -   **glassCube** obtém um <xref:System.Windows.UIElement.Opacity%2A> de 100%.  
  
    -   **outerRectangle** obtém um <xref:System.Windows.Shapes.Shape.Stroke%2A> valor de expressão personalizada de "{DynamicResource {X:Static SystemColors.HighlightBrushKey}}".  
  
 Como etapa final deste passo a passo, adicionaremos animações ao botão. Essas animações serão disparadas por eventos — especificamente, o <xref:System.Windows.UIElement.MouseEnter> e <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos.  
  
#### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Para usar gatilhos de evento e animações para adicionar interatividade  
  
1.  **Criar um gatilho de evento MouseEnter:** adicionar um novo gatilho de evento e selecione <xref:System.Windows.UIElement.MouseEnter> como o evento a ser usado no gatilho.  
  
     ![Como criar um gatilho de evento MouseEnter](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger.png "custom_button_blend_MouseOverEventTrigger")  
  
2.  **Criar uma linha do tempo de animação:** em seguida, associar uma linha de tempo de animação para o <xref:System.Windows.UIElement.MouseEnter> evento.  
  
     ![Como adicionar uma linha do tempo da animação a um evento](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger2.png "custom_button_blend_MouseOverEventTrigger2")  
  
     Depois de pressionar **OK** para criar uma nova linha do tempo, é exibido um **painel Linha do tempo** e “O registro da linha do tempo está ativado” fica visível no painel de design. Isso significa que podemos começar a registrar mudanças na propriedade na linha do tempo (mudanças na propriedade de animação).  
  
    > [!NOTE]
    >  Talvez seja necessário redimensionar a janela e/ou painéis para ver a exibição.  
  
     ![O painel da linha do tempo](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger3.png "custom_button_blend_MouseOverEventTrigger3")  
  
3.  **Crie um quadro chave:** para criar uma animação, selecione o objeto que deseja animar, crie dois ou mais quadros chave na linha do tempo e, para esses quadros chave, defina os valores da propriedade entre os quais quer a interpolação da animação. A figura a seguir é uma orientação para a criação de um quadro chave.  
  
     ![Como criar um quadro chave](../../../../docs/framework/wpf/controls/media/custom-button-blend-mouseovereventtrigger4.png "custom_button_blend_MouseOverEventTrigger4")  
  
4.  **Reduza glassCube neste quadro chave:** com o segundo quadro chave selecionado, reduza o tamanho do **glassCube** para 90% do seu tamanho total usando **Transformar tamanho**.  
  
     ![Como reduzir o tamanho de um botão](../../../../docs/framework/wpf/controls/media/custom-button-blend-sizetransform.png "custom_button_blend_SizeTransform")  
  
     Pressione F5 para executar o aplicativo. Mova o ponteiro do mouse sobre o botão. Observe que a camada do vidro é reduzida sobre o botão.  
  
5.  **Crie outro gatilho de evento e associe uma animação diferente a ele:** vamos adicionar mais uma animação. Use um procedimento semelhante ao que você usou para criar a animação anterior do gatilho de evento:  
  
    1.  Criar um novo gatilho de evento usando o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
    2.  Associar uma nova linha do tempo com o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento.  
  
     ![Como criar uma nova linha do tempo](../../../../docs/framework/wpf/controls/media/custom-button-blend-clickeventtrigger1.png "custom_button_blend_ClickEventTrigger1")  
  
    1.  Para essa linha do tempo, crie dois quadros chave, em 0,0 segundos e, o segundo, em 0,3 segundos.  
  
    2.  Com o quadro chave destacado em 0,3 segundos, defina o **ângulo de transformação de giro** como 360 graus.  
  
     ![Como criar uma transformação de giro](../../../../docs/framework/wpf/controls/media/custom-button-blend-rotatetransform.gif "custom_button_blend_RotateTransform")  
  
    1.  Pressione F5 para executar o aplicativo. Clique no botão. Observe que a camada do vidro vai girar.  
  
## <a name="conclusion"></a>Conclusão  
 Você concluiu um botão personalizado. Para fazer isso, utilizou um modelo de botão que foi aplicado a todos os botões no aplicativo. Se você sair do modo de edição de modelo (consulte a figura a seguir) e criar mais botões, verá que a aparência e o comportamento deles são semelhantes aos do botão personalizado, não ao botão padrão.  
  
 ![O modelo de botão personalizado](../../../../docs/framework/wpf/controls/media/custom-button-blend-scopeup.gif "custom_button_blend_ScopeUp")  
  
 ![Vários botões que usam o mesmo modelo](../../../../docs/framework/wpf/controls/media/custom-button-blend-createmultiplebuttons.png "custom_button_blend_CreateMultipleButtons")  
  
 Pressione F5 para executar o aplicativo. Clique nos botões e observe como todos eles se comportam da mesma maneira.  
  
 Lembre-se de que, enquanto você foram Personalizando o modelo, você definir o <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade **innerRectangle** e <xref:System.Windows.Shapes.Shape.Stroke%2A> propriedade **outerRectangle** no plano de fundo do modelo ({ Plano TemplateBinding}). Por isso, quando definir a cor da tela de fundo dos botões individuais, a tela de fundo definida será utilizada para as respectivas propriedades. Tente alterar as telas de fundo agora. Na figura a seguir, gradientes diferentes são usados. Portanto, apesar de um modelo ser útil para a personalização total de controles como botões, controles com modelos ainda podem ser modificados para ter aparências distintas.  
  
 ![Botões com o mesmo modelo e aparências distintas](../../../../docs/framework/wpf/controls/media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")  
  
 Para concluir, durante o processo de personalização de um modelo de botão, você aprendeu a fazer o seguinte no Microsoft Expression Blend:  
  
-   Personalize a aparência de um controle.  
  
-   Defina gatilhos de propriedade. Os gatilhos de propriedade são muito úteis, porque podem ser utilizados na maioria dos objetos, não apenas em controles.  
  
-   Defina gatilhos de evento. Os gatilhos de evento são muito úteis, porque podem ser utilizados na maioria dos objetos, não apenas em controles.  
  
-   Crie animações.  
  
-   Diversos: crie gradientes, adicione BitmapEffects, use transformações e defina as propriedades básicas dos objetos.  
  
## <a name="see-also"></a>Consulte também  
 [Criar um botão usando XAML](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Visão geral dos efeitos de bitmap](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
