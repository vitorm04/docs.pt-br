---
title: Arquitetura de controle ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: e02b9daa40a5f8a2f8bfd8874d006550628a70b3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654715"
---
# <a name="toolstrip-control-architecture"></a>Arquitetura de controle ToolStrip
O <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.ToolStripItem> classes fornecem um sistema flexível e extensível para exibir itens de menu, status e barra de ferramentas. Essas classes estão contidas na <xref:System.Windows.Forms> namespace e eles todos geralmente são nomeados com o prefixo "ToolStrip" (como <xref:System.Windows.Forms.ToolStripOverflow>) ou com o sufixo "Strip" (como <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 Os tópicos a seguir descrevem <xref:System.Windows.Forms.ToolStrip> e os controles que derivam dela.  
  
 <xref:System.Windows.Forms.ToolStrip> é a classe base abstrata para <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, e <xref:System.Windows.Forms.ContextMenuStrip>. O seguinte objeto de modelo mostra o <xref:System.Windows.Forms.ToolStrip> hierarquia de herança.  
  
 ![Diagrama que mostra o modelo de objeto ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)  
  
 Você pode acessar todos os itens em uma <xref:System.Windows.Forms.ToolStrip> por meio de <xref:System.Windows.Forms.ToolStrip.Items%2A> coleção. Você pode acessar todos os itens em uma <xref:System.Windows.Forms.ToolStripDropDownItem> por meio de <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> coleção. Em uma classe derivada de <xref:System.Windows.Forms.ToolStrip>, você também pode usar o <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> propriedade para acessar somente os itens que são exibidos no momento. Estes são os itens que não estão atualmente em um menu de estouro.  
  
 Os itens a seguir são projetados especificamente para funcionar perfeitamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para o <xref:System.Windows.Forms.ToolStrip> controle:  
  
- <xref:System.Windows.Forms.ToolStripButton>  
  
- <xref:System.Windows.Forms.ToolStripSeparator>  
  
- <xref:System.Windows.Forms.ToolStripLabel>  
  
- <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
- <xref:System.Windows.Forms.ToolStripSplitButton>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> é o contêiner de nível superior que substitui <xref:System.Windows.Forms.MainMenu>. Ele também oferece os recursos de manipulação de chaves e MDI (interface de múltiplos documentos). Funcionalmente, <xref:System.Windows.Forms.ToolStripDropDownItem> e <xref:System.Windows.Forms.ToolStripMenuItem> funcionam junto com <xref:System.Windows.Forms.MenuStrip>, embora eles sejam derivados de <xref:System.Windows.Forms.ToolStripItem>.  
  
 Os itens a seguir são projetados especificamente para funcionar perfeitamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para o <xref:System.Windows.Forms.MenuStrip> controle:  
  
- <xref:System.Windows.Forms.ToolStripMenuItem>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> substitui o <xref:System.Windows.Forms.StatusBar> controle. Recursos especiais do <xref:System.Windows.Forms.StatusStrip> incluem um layout de tabela personalizados, o suporte para o formulário de dimensionamento e deslocamento do seguia e o `Spring` propriedade, que permite um <xref:System.Windows.Forms.ToolStripStatusLabel> para preencher automaticamente o espaço disponível.  
  
 Os itens a seguir são projetados especificamente para funcionar perfeitamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para o <xref:System.Windows.Forms.StatusStrip> controle:  
  
- <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
- <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
- <xref:System.Windows.Forms.ToolStripSplitButton>  
  
- <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> substitui <xref:System.Windows.Forms.ContextMenu>. Você pode associar um <xref:System.Windows.Forms.ContextMenuStrip> com qualquer controle e o botão direito do mouse clique exibirá automaticamente o menu de contexto (ou menu de atalho). Você pode mostrar uma <xref:System.Windows.Forms.ContextMenuStrip> programaticamente, usando o <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> método. <xref:System.Windows.Forms.ContextMenuStrip> dá suporte a cancelável <xref:System.Windows.Forms.ToolStripDropDown.Opening> e <xref:System.Windows.Forms.ToolStripDropDown.Closing> eventos para lidar com cenários de vários cliques e preenchimento dinâmico. <xref:System.Windows.Forms.ContextMenuStrip> dá suporte a imagens, estado de seleção de item de menu, texto, as chaves de acesso, atalhos e menus em cascata.  
  
 Os itens a seguir são projetados especificamente para funcionar perfeitamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para o <xref:System.Windows.Forms.ContextMenuStrip> controle:  
  
- <xref:System.Windows.Forms.ToolStripMenuItem>  
  
- <xref:System.Windows.Forms.ToolStripSeparator>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>Recursos genéricos de ToolStrip  
 Os tópicos a seguir descrevem os recursos e o comportamento que são genéricos para o <xref:System.Windows.Forms.ToolStrip> e controles derivados.  
  
#### <a name="painting"></a>Pintura  
 Você pode fazer a pintura personalizada no <xref:System.Windows.Forms.ToolStrip> controles de várias maneiras. Assim como acontece com outros controles Windows Forms, o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.ToolStripItem> ambos têm substituível `OnPaint` métodos e `Paint` eventos. Assim como ocorre com pintura regular, o sistema de coordenadas é relativo à área de cliente do controle, ou seja, o canto superior esquerdo do controle é 0, 0. O `Paint` evento e `OnPaint` método para um <xref:System.Windows.Forms.ToolStripItem> se comportam como outros eventos de pintura do controle.  
  
 O <xref:System.Windows.Forms.ToolStrip> controles também fornecem acesso mais refinado para a renderização de itens e contêiner por meio de <xref:System.Windows.Forms.ToolStripRenderer> classe, que tem métodos substituíveis para pintar a tela de fundo, tela de fundo do item, imagem do item, seta do item, texto do item e a borda da <xref:System.Windows.Forms.ToolStrip>. Os argumentos de evento para esses métodos expõem várias propriedades como retângulos, cores e formatos de texto que você pode ajustar conforme desejado.  
  
 Para ajustar apenas alguns aspectos de como um item é pintado, você normalmente substitui o <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Se você estiver escrevendo um novo item e desejar controlar todos os aspectos de pintura, substitua o método `OnPaint`. De dentro `OnPaint`, você pode usar os métodos do <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Por padrão, o <xref:System.Windows.Forms.ToolStrip> tem buffer duplo, aproveitando o <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> configuração.  
  
#### <a name="parenting"></a>Gerenciamento do domínio pai  
 O conceito de contêiner posse e parentesco é mais complexo em <xref:System.Windows.Forms.ToolStrip> controla que em outros controles de contêiner do Windows Forms. Isso é necessário para dar suporte a cenários dinâmicos, como estouro, compartilhamento de itens de lista suspensa entre vários <xref:System.Windows.Forms.ToolStrip> itens e para dar suporte a geração de um <xref:System.Windows.Forms.ContextMenuStrip> de um controle.  
  
 A lista a seguir descreve os membros relacionados ao gerenciamento do domínio pai e explica o seu uso.  
  
- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> acessa o item que é a origem do item de lista suspensa. Isso é semelhante à <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, mas em vez de retornar um controle, ele retorna um <xref:System.Windows.Forms.ToolStripItem>.  
  
- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> determina qual controle é a origem do <xref:System.Windows.Forms.ContextMenuStrip> quando vários controles compartilham o mesmo <xref:System.Windows.Forms.ContextMenuStrip>.  
  
- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> é um acessador de somente leitura para o <xref:System.Windows.Forms.ToolStripItem.Parent%2A> propriedade. Um pai difere de um proprietário de um pai denota o atual retornado <xref:System.Windows.Forms.ToolStrip> no qual o item é exibido, que pode ser na área de excedentes.  
  
- <xref:System.Windows.Forms.ToolStripItem.Owner%2A> Retorna o <xref:System.Windows.Forms.ToolStrip> cuja coleção de itens contém atual <xref:System.Windows.Forms.ToolStripItem>. Isso é a melhor maneira de referenciar <xref:System.Windows.Forms.ToolStrip.ImageList%2A> ou outras propriedades no nível superior <xref:System.Windows.Forms.ToolStrip> sem escrever códigos especiais para manipular o estouro.  
  
#### <a name="behavior-of-inherited-controls"></a>Comportamento de controles herdados  
 Os seguintes controles são bloqueados sempre que eles são usados em herança:  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
- <xref:System.Windows.Forms.MenuStrip>  
  
- <xref:System.Windows.Forms.ContextMenuStrip>  
  
- <xref:System.Windows.Forms.StatusStrip>  
  
- <xref:System.Windows.Forms.ToolStripPanel> que inclui os painéis em uma <xref:System.Windows.Forms.ToolStripContainer> também individuais e <xref:System.Windows.Forms.ToolStripPanel> controles.  
  
 Por exemplo, crie um novo aplicativo dos Windows Forms usando um ou mais dos controles na lista anterior. Defina o modificador de acesso de um ou mais controles para `public` ou `protected` e, em seguida, compile o projeto. Adicione um formulário que herda do primeiro formulário e, em seguida, selecione um controle herdado. O controle aparece bloqueado, comportando-se como se o seu modificador de acesso fosse `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>Suporte Herança de ToolStripContainer  
 O <xref:System.Windows.Forms.ToolStripContainer> controle dá suporte a cenários herdados limitados, semelhantes ao exemplo a seguir:  
  
1. Criar um novo aplicativo Windows Form.  
  
2. Adicionar um <xref:System.Windows.Forms.ToolStripContainer> ao formulário.  
  
3. Defina o modificador de acesso do <xref:System.Windows.Forms.ToolStripContainer> à `public` ou `protected`.  
  
4. Adicione qualquer combinação de <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.ContextMenuStrip> controles para o <xref:System.Windows.Forms.ToolStripPanel> regiões do <xref:System.Windows.Forms.ToolStripContainer>.  
  
5. Compile o projeto.  
  
6. Adicione um formulário que herda do primeiro formulário.  
  
7. Selecione o herdadas <xref:System.Windows.Forms.ToolStripContainer> no formulário.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Comportamento herdado de controles filho  
 Depois de você concluir as etapas anteriores, ocorre o seguinte comportamento herdado:  
  
- No designer, o controle aparece com um ícone herdado.  
  
- O <xref:System.Windows.Forms.ToolStripPanel> controles são bloqueados; você não é possível selecionar nem reorganizar seu conteúdo.  
  
- Você pode adicionar controles para o <xref:System.Windows.Forms.ToolStripContentPanel>, mova os controles e torná-los controles filhos do <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
- Suas alterações persistem após compilar o formulário.  
  
    > [!NOTE]
    >  Remova os modificadores de acesso de todos os <xref:System.Windows.Forms.ToolStripPanel> controles que fazem parte de um <xref:System.Windows.Forms.ToolStripContainer>. O modificador de acesso do <xref:System.Windows.Forms.ToolStripContainer> rege todo o controle.  
  
#### <a name="partial-trust"></a>Confiança parcial  
 As limitações de `ToolStrip`s sob confiança parcial são projetadas para impedir entrada acidental de informações pessoais que possam ser usadas por pessoas ou serviços não autorizados. As medidas de proteção são as seguintes:  
  
- `ToolStripDropDown` controles exigem <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> para exibir itens em um <xref:System.Windows.Forms.ToolStripControlHost>. Isso se aplica a ambos os controles intrínsecos, como <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, e <xref:System.Windows.Forms.ToolStripProgressBar> como bem como para criados pelo usuário controla. Se esse requisito não for atendido, esses itens não serão exibidos. Nenhuma exceção é lançada.  
  
- Definindo o <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> propriedade para `false` não é permitido e o cancelável <xref:System.Windows.Forms.ToolStripDropDown.Closing> evento parâmetro será ignorado. Isso torna impossível realizar mais de um pressionamento da tecla sem fechar o item suspenso. Se esse requisito não for atendido, esses itens não serão exibidos. Nenhuma exceção é lançada.  
  
- Muitos pressionamento de tecla a manipulação de eventos não serão gerados se ocorrerem em contextos de confiança parcial diferente de <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
- Chaves de acesso não são processados quando <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> não é concedida.  
  
#### <a name="usage"></a>Uso  
 Os seguintes padrões de uso tem uma influência <xref:System.Windows.Forms.ToolStrip> layout, a interação do teclado e o comportamento do usuário final:  
  
- Ingressou em um <xref:System.Windows.Forms.ToolStripPanel>  
  
     O <xref:System.Windows.Forms.ToolStrip> pode ser reposicionado dentro do <xref:System.Windows.Forms.ToolStripPanel> e entre <xref:System.Windows.Forms.ToolStripPanel>s. O `Dock` propriedade será ignorada e se o <xref:System.Windows.Forms.ToolStrip.Stretch%2A> é de propriedade `false`, o tamanho dos <xref:System.Windows.Forms.ToolStrip> aumenta à medida que itens são adicionados à <xref:System.Windows.Forms.ToolStripPanel>. Normalmente, o <xref:System.Windows.Forms.ToolStrip> não participa na ordem de tabulação.  
  
- Encaixado  
  
     O <xref:System.Windows.Forms.ToolStrip> é colocado em um dos lados de um contêiner em uma posição fixa, e seu tamanho se expande sobre toda a borda para o qual ela está ancorada. Normalmente, o <xref:System.Windows.Forms.ToolStrip> não participa na ordem de tabulação.  
  
- Posição absoluta  
  
     O <xref:System.Windows.Forms.ToolStrip> é semelhante a outros controles, em que ele é colocado pelo <xref:System.Windows.Forms.Control.Location%2A> propriedade, tem um tamanho fixo e normalmente participa na ordem de tabulação.  
  
#### <a name="keyboard-interaction"></a>Interação do teclado  
  
##### <a name="access-keys"></a>Teclas de acesso  
 Combinadas com ou após a tecla ALT, as teclas de acesso são uma maneira de ativar um controle usando o teclado. <xref:System.Windows.Forms.ToolStrip> dá suporte a ambas as chaves de acesso explícitas e implícitas. A definição explícita usa um caractere e comercial (&) que precede a letra. A definição implícita usa um algoritmo que tenta encontrar um item correspondente com base na ordem de caracteres em uma determinada propriedade `Text`.  
  
##### <a name="shortcut-keys"></a>Teclas de Atalho  
 As teclas de atalho usadas por um <xref:System.Windows.Forms.MenuStrip> usam uma combinação da <xref:System.Windows.Forms.Keys> enumeração (que não é específico da ordem) para definir a tecla de atalho. Você também pode usar o <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriedade para exibir uma tecla de atalho com apenas texto, como exibir "Del" em vez de "Delete".  
  
##### <a name="navigation"></a>Navegação  
 A tecla ALT ativa o <xref:System.Windows.Forms.MenuStrip> apontado por <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. A partir daí, CTRL + TAB navega entre <xref:System.Windows.Forms.ToolStrip> controla dentro `ToolStripPanel`s. A tecla TAB e as teclas de direção no teclado numérico navegarem entre itens em um <xref:System.Windows.Forms.ToolStrip>. Um algoritmo especial manipula a navegação na região de estouro. Barra de espaços seleciona um <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ou <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Foco e validação  
 Quando ativado pela tecla ALT, o <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ToolStrip> normalmente não toma nem remove o foco do controle que tem o foco no momento. Se houver um controle hospedado dentro de <xref:System.Windows.Forms.MenuStrip> ou uma lista suspensa do <xref:System.Windows.Forms.MenuStrip>, o controle receberá foco quando o usuário pressiona a tecla TAB. Em geral, o <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, e <xref:System.Windows.Forms.Control.Leave> eventos de <xref:System.Windows.Forms.MenuStrip> pode não ser gerado quando são ativados pelo teclado. Nesses casos, use o <xref:System.Windows.Forms.MenuStrip.MenuActivate> e <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> eventos em vez disso.  
  
 Por padrão, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> é `false`. Chamar <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitamente em seu formulário para executar a validação.  
  
#### <a name="layout"></a>Layout  
 Você controla <xref:System.Windows.Forms.ToolStrip> layout escolhendo um dos membros <xref:System.Windows.Forms.ToolStripLayoutStyle> com o <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> propriedade.  
  
##### <a name="stack-layouts"></a>Layouts de pilha  
 Empilhamento é a organização de itens ao lado de cada um dos outros em ambas as extremidades do <xref:System.Windows.Forms.ToolStrip>. A lista a seguir descreve os layouts de pilha.  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> é o padrão. Essa configuração faz com que o <xref:System.Windows.Forms.ToolStrip> altere seu layout automaticamente de acordo com o <xref:System.Windows.Forms.ToolStrip.Orientation%2A> propriedade para lidar com cenários de encaixe e arrastando.  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> renderiza o <xref:System.Windows.Forms.ToolStrip> itens verticalmente ao lado uns aos outros.  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> renderiza o <xref:System.Windows.Forms.ToolStrip> itens ao lado uns aos outros, horizontalmente.  
  
##### <a name="other-features-of-stack-layouts"></a>Outros recursos de layouts de pilha  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Determina o final do <xref:System.Windows.Forms.ToolStrip> ao qual o item é alinhado.  
  
 Quando itens não se ajustarem dentro de <xref:System.Windows.Forms.ToolStrip>, um botão de estouro é exibida automaticamente. O <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriedade determina se um item é exibido na área de estouro sempre, conforme necessário ou nunca.  
  
 No <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> evento, você pode inspecionar a <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriedade para determinar se um item foi colocado no principal <xref:System.Windows.Forms.ToolStrip>, o estouro <xref:System.Windows.Forms.ToolStrip>, ou se ele não está sendo exibido em todos os. As razões comuns por que um item não é exibido são que o item não se ajusta no principal <xref:System.Windows.Forms.ToolStrip> e sua <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriedade foi definida como <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Tornar um <xref:System.Windows.Forms.ToolStrip> móvel, colocando-o um <xref:System.Windows.Forms.ToolStripPanel> e definindo seu <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> para <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Outras opções de layout  
 As outras opções de layout são <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> e <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Layout de fluxo  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> o layout é o padrão para <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, e <xref:System.Windows.Forms.ToolStripOverflow>. Ele é semelhante ao <xref:System.Windows.Forms.FlowLayoutPanel>. Os recursos do <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> layout são da seguinte maneira:  
  
- Todos os recursos do <xref:System.Windows.Forms.FlowLayoutPanel> são expostos pelo <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriedade. Você deve converter o <xref:System.Windows.Forms.LayoutSettings> de classe para um <xref:System.Windows.Forms.FlowLayoutSettings> classe.  
  
- Você pode usar o <xref:System.Windows.Forms.ToolStripItem.Dock%2A> e <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> propriedades no código para alinhar os itens dentro da linha.  
  
- A propriedade <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é ignorada.  
  
- No <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> evento, você pode inspecionar a <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriedade para determinar se um item foi colocado no principal <xref:System.Windows.Forms.ToolStrip> ou não se ajusta.  
  
- A alça não é processada e, portanto, uma <xref:System.Windows.Forms.ToolStrip> na <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> estilo de layout em um <xref:System.Windows.Forms.ToolStripPanel> não pode ser movido.  
  
- O <xref:System.Windows.Forms.ToolStrip> botão de estouro não é processado, e <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> é ignorado.  
  
##### <a name="table-layout"></a>Layout da tabela  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> o layout é o padrão para <xref:System.Windows.Forms.StatusStrip>. Ele é semelhante ao <xref:System.Windows.Forms.TableLayoutPanel>. Os recursos do <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> layout são da seguinte maneira:  
  
- Todos os recursos do <xref:System.Windows.Forms.TableLayoutPanel> são expostos pelo <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> propriedade. Você deve converter o <xref:System.Windows.Forms.LayoutSettings> de classe para um <xref:System.Windows.Forms.TableLayoutSettings> classe.  
  
- Você pode usar o <xref:System.Windows.Forms.ToolStripItem.Dock%2A> e <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> propriedades no código para alinhar os itens dentro da célula de tabela.  
  
- A propriedade <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é ignorada.  
  
- No <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> evento, você pode inspecionar a <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriedade para determinar se um item foi colocado no principal <xref:System.Windows.Forms.ToolStrip> ou não se ajusta.  
  
- A alça não é processada e, portanto, uma <xref:System.Windows.Forms.ToolStrip> na <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> estilo de layout em um <xref:System.Windows.Forms.ToolStripPanel> não pode ser movido.  
  
- O <xref:System.Windows.Forms.ToolStrip> botão de estouro não é processado, e <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> é ignorado.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 Os tópicos a seguir descrevem <xref:System.Windows.Forms.ToolStripItem> e os controles que derivam dela.  
  
 <xref:System.Windows.Forms.ToolStripItem> é a classe base abstrata para todos os itens que vão para um <xref:System.Windows.Forms.ToolStrip>. O seguinte objeto de modelo mostra o <xref:System.Windows.Forms.ToolStripItem> hierarquia de herança.  
  
 ![Diagrama que mostra o modelo de objeto ToolStripItem.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)  
  
 <xref:System.Windows.Forms.ToolStripItem> classes de qualquer um pode herdar diretamente de <xref:System.Windows.Forms.ToolStripItem>, ou eles herdam indiretamente <xref:System.Windows.Forms.ToolStripItem> por meio <xref:System.Windows.Forms.ToolStripControlHost> ou <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem> controles devem estar contidos em um <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, ou <xref:System.Windows.Forms.ContextMenuStrip> e não podem ser adicionados diretamente a um formulário. As várias classes de contêiner foram projetadas para conter um subconjunto apropriado de <xref:System.Windows.Forms.ToolStripItem> controles.  
  
 A tabela a seguir lista o estoque <xref:System.Windows.Forms.ToolStripItem> controles e os contêineres no qual eles têm a melhores aparência. Embora qualquer <xref:System.Windows.Forms.ToolStrip> item pode ser hospedado em qualquer <xref:System.Windows.Forms.ToolStrip>-derivado recipiente, esses itens foram projetados para uma aparência melhor nos seguintes contêineres:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> não aparece na caixa de ferramentas do designer.  
  
|Item contido|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|Sim|Não|Não|Não|Sim|  
|<xref:System.Windows.Forms.ToolStripComboBox>|Sim|Sim|Sim|Não|Sim|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Sim|Não|Não|Sim|Sim|  
|<xref:System.Windows.Forms.ToolStripLabel>|Sim|Não|Não|Sim|Sim|  
|<xref:System.Windows.Forms.ToolStripSeparator>|Sim|Sim|Sim|Não|Sim|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Sim|Não|Não|Sim|Sim|  
|<xref:System.Windows.Forms.ToolStripTextBox>|Sim|Sim|Sim|Não|Sim|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Não|Sim|Sim|Não|Não|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Não|Não|Não|Sim|Não|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Sim|Não|Não|Sim|Não|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Sim|Sim|Não|Sim|Sim|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> é o item de botão para <xref:System.Windows.Forms.ToolStrip>. Você pode exibi-lo com vários estilos de borda e pode usá-lo para representar e ativar estados operacionais. Você também pode defini-lo para ter o foco por padrão.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 O <xref:System.Windows.Forms.ToolStripLabel> fornece a funcionalidade de rótulo no <xref:System.Windows.Forms.ToolStrip> controles. O <xref:System.Windows.Forms.ToolStripLabel> é como um <xref:System.Windows.Forms.ToolStripButton> que não obtém foco por padrão e que não renderiza como pressionado nem realçado.  
  
 <xref:System.Windows.Forms.ToolStripLabel> como um item hospedado dá suporte a chaves de acesso.  
  
 Use o <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, e <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriedades em um <xref:System.Windows.Forms.ToolStripLabel> para dar suporte a controle de link em um <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> é uma versão do <xref:System.Windows.Forms.ToolStripLabel> projetado especificamente para uso em <xref:System.Windows.Forms.StatusStrip>. Os recursos especiais incluem <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, e <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 O <xref:System.Windows.Forms.ToolStripSeparator> adiciona uma linha vertical ou horizontal a uma barra de ferramentas ou menu, dependendo da orientação. Ele fornece o agrupamento de ou a distinção entre itens, assim como aqueles em um menu.  
  
 Você pode adicionar um <xref:System.Windows.Forms.ToolStripSeparator> em tempo de design escolhendo-a em uma lista suspensa. No entanto, você pode também criar automaticamente um <xref:System.Windows.Forms.ToolStripSeparator> digitando um hífen (-) no nó designer de modelo ou no <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> método.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> é a classe base abstrata para <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, e <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost> pode hospedar outros controles, incluindo controles personalizados, de duas maneiras:  
  
- Construir uma <xref:System.Windows.Forms.ToolStripControlHost> com uma classe que deriva de <xref:System.Windows.Forms.Control>. Para acessar totalmente o controle hospedado e propriedades, você deve converter o <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> propriedade como verdadeira classe que ele representa.  
  
- Estender <xref:System.Windows.Forms.ToolStripControlHost>e no construtor de padrão da classe herdada, chame o construtor de classe base passando uma classe que deriva de <xref:System.Windows.Forms.Control>. Essa opção permite que você encapsule métodos comuns de controle e propriedades para facilitar o acesso em um <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> é o <xref:System.Windows.Forms.ComboBox> otimizado para hospedagem em um <xref:System.Windows.Forms.ToolStrip>. Um subconjunto de propriedades e eventos do controle hospedado são expostos na <xref:System.Windows.Forms.ToolStripComboBox> nível, mas subjacente <xref:System.Windows.Forms.ComboBox> controle é totalmente acessível por meio de <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> propriedade.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> é o <xref:System.Windows.Forms.TextBox> otimizado para hospedagem em um <xref:System.Windows.Forms.ToolStrip>. Um subconjunto de propriedades e eventos do controle hospedado são expostos na <xref:System.Windows.Forms.ToolStripTextBox> nível, mas subjacente <xref:System.Windows.Forms.TextBox> controle é totalmente acessível por meio de <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> propriedade.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> é o <xref:System.Windows.Forms.ProgressBar> otimizado para hospedagem em um <xref:System.Windows.Forms.ToolStrip>. Um subconjunto de propriedades e eventos do controle hospedado são expostos na <xref:System.Windows.Forms.ToolStripProgressBar> nível, mas subjacente <xref:System.Windows.Forms.ProgressBar> controle é totalmente acessível por meio de <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> propriedade.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> é a classe base abstrata para <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, e <xref:System.Windows.Forms.ToolStripSplitButton>, que pode hospedar itens diretamente ou hospedar itens adicionais em um contêiner de lista suspensa. Fazer isso definindo a <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> propriedade para um <xref:System.Windows.Forms.ToolStripDropDown> e definindo o <xref:System.Windows.Forms.ToolStrip.Items%2A> propriedade do <xref:System.Windows.Forms.ToolStripDropDown>. Acessar esses itens suspensos diretamente por meio de <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> propriedade.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> é um <xref:System.Windows.Forms.ToolStripDropDownItem> que funciona com <xref:System.Windows.Forms.ToolStripDropDownMenu> e <xref:System.Windows.Forms.ContextMenuStrip> para lidar com a disposição de coluna, layout e realce especial para menus.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> é semelhante a <xref:System.Windows.Forms.ToolStripButton>, mas ele mostra uma área suspensa quando o usuário clica nele. Ocultar ou mostrar a seta suspensa definindo o <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> propriedade. <xref:System.Windows.Forms.ToolStripDropDownButton> hosts de um <xref:System.Windows.Forms.ToolStripOverflowButton> que exibe itens que estouram o <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> combina um botão e a funcionalidade do botão suspenso.  
  
 Use o <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> propriedade para sincronizar o <xref:System.Windows.Forms.Control.Click> evento do item suspenso escolhido com o item exibido no botão.  
  
### <a name="toolstripitem-generic-features"></a>Recursos genéricos de ToolStripItem  
 <xref:System.Windows.Forms.ToolStripItem> fornece os seguintes recursos genéricos e opções para herdar controles:  
  
- Eventos principais  
  
- Tratamento de imagem  
  
- Alinhamento  
  
- Relação de texto e imagem  
  
- Estilo de exibição  
  
#### <a name="core-events"></a>Eventos Principais  
 <xref:System.Windows.Forms.ToolStripItem> controles de recebem seus próprios clique, mouse e eventos de pintura e podem executar algum pré-processamento também de teclado.  
  
#### <a name="image-handling"></a>Tratamento de Imagem  
 O <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, e <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> propriedades pertencem aos vários aspectos da manipulação de imagem. Usar imagens no <xref:System.Windows.Forms.ToolStrip> controles, definir essas propriedades diretamente ou definindo a execução tempo – somente <xref:System.Windows.Forms.ToolStrip.ImageList%2A> propriedade.  
  
 Escala da imagem é determinado pela interação de propriedades em ambos <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.ToolStripItem>, da seguinte maneira:  
  
- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> é a escala da imagem final, conforme determinado pela combinação da imagem <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> configuração e o contêiner <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> configuração.  
  
    - Se <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> está `true` (o padrão) e <xref:System.Windows.Forms.ToolStripItemImageScaling> é <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, nenhum dimensionamento de imagem ocorre e o <xref:System.Windows.Forms.ToolStrip> é do tamanho do maior item ou um tamanho mínimo definido.  
  
    - Se <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> está `false` e <xref:System.Windows.Forms.ToolStripItemImageScaling> é <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, nenhuma imagem nem <xref:System.Windows.Forms.ToolStrip> dimensionamento ocorre.  
  
#### <a name="alignment"></a>Alinhamento  
 O valor da <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade determina o final do <xref:System.Windows.Forms.ToolStrip> em que um item aparece. O <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade funciona somente quando o estilo de layout do <xref:System.Windows.Forms.ToolStrip> é definido como um dos valores de estouro de pilha.  
  
 Itens são colocados no <xref:System.Windows.Forms.ToolStrip> na ordem em que os itens aparecem na coleção de itens. Para alterar programaticamente o onde um item é apresentado, use o <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> método para mover o item na coleção. Esse método move o item, mas não o duplica.  
  
#### <a name="text-and-image-relationship"></a>Relação de Texto e Imagem  
 O <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriedade define o posicionamento relativo da imagem em relação ao texto em um <xref:System.Windows.Forms.ToolStripItem>. Itens que não têm uma imagem, texto ou ambos são tratados como casos especiais, de modo que o <xref:System.Windows.Forms.ToolStripItem> não exibirá um espaço vazio para o elemento ou elementos ausentes.  
  
#### <a name="display-style"></a>Estilo de Exibição  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> permite que você defina os valores das propriedades de texto e imagem de um item ao exibir apenas o que você deseja. Isso normalmente é usado para alterar o estilo de exibição ao mostrar o mesmo item em um contexto diferente.  
  
## <a name="accessory-classes"></a>Classes acessórias  
 Classes que fornecem várias outras funcionalidades incluem:  
  
- <xref:System.Windows.Forms.ToolStripManager> dá suporte a <xref:System.Windows.Forms.ToolStrip>-tarefas para aplicativos inteiros, como opções de mesclagem, configurações e renderizador relacionadas.  
  
- <xref:System.Windows.Forms.ToolStripRenderer> permite que você aplique um estilo específico ou um tema a um <xref:System.Windows.Forms.ToolStrip> facilmente.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer> cria canetas e pincéis com base em uma tabela de cores substituíveis (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer> aplica-se as cores do sistema e um estilo visual simples para <xref:System.Windows.Forms.ToolStrip> aplicativos.  
  
- <xref:System.Windows.Forms.ToolStripContainer> é semelhante ao <xref:System.Windows.Forms.SplitContainer>. Ele usa quatro painéis laterais encaixados (instâncias de <xref:System.Windows.Forms.ToolStripPanel>) e um painel central (uma instância de <xref:System.Windows.Forms.ToolStripContentPanel>) para criar uma disposição típica. Não é possível remover os painéis laterais, mas você pode ocultá-los. Não é possível remover nem ocultar o painel central. Você pode organizar um ou mais <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ou <xref:System.Windows.Forms.StatusStrip> controles em painéis laterais e você podem usar o painel central para outros controles. O <xref:System.Windows.Forms.ToolStripContentPanel> também fornece uma maneira de obter suporte do renderizador no corpo do formulário para uma aparência consistente. <xref:System.Windows.Forms.ToolStripContainer> não oferece suporte a interface de documentos múltiplos (MDI).  
  
- <xref:System.Windows.Forms.ToolStripPanel> Fornece espaço para mover e organizar <xref:System.Windows.Forms.ToolStrip> controles. Você pode usar somente um painel se preferir, e <xref:System.Windows.Forms.ToolStripPanel> funciona bem em cenários MDI.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
- [Controle MenuStrip](menustrip-control-windows-forms.md)
- [Controle StatusStrip](statusstrip-control.md)
- [Controle ContextMenuStrip](contextmenustrip-control.md)
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
