---
title: Arquitetura de controle ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363830"
---
# <a name="toolstrip-control-architecture"></a>Arquitetura de controle ToolStrip

As <xref:System.Windows.Forms.ToolStrip> classes <xref:System.Windows.Forms.ToolStripItem> e fornecem um sistema flexível e extensível para exibir a barra de ferramentas, o status e os itens de menu. Essas classes estão todas contidas no <xref:System.Windows.Forms> namespace e elas são normalmente nomeadas com o prefixo "ToolStrip" ( <xref:System.Windows.Forms.ToolStripOverflow>como) ou com o sufixo "strip <xref:System.Windows.Forms.MenuStrip>" (como).

## <a name="toolstrip"></a>ToolStrip

Os tópicos a seguir <xref:System.Windows.Forms.ToolStrip> descrevem e os controles que derivam dele.

<xref:System.Windows.Forms.ToolStrip>é a classe base abstrata para <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>e <xref:System.Windows.Forms.ContextMenuStrip>. O modelo de objeto a seguir <xref:System.Windows.Forms.ToolStrip> mostra a hierarquia de herança.

![Diagrama que mostra o modelo de objeto ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

Você pode acessar todos os itens em um <xref:System.Windows.Forms.ToolStrip> por meio <xref:System.Windows.Forms.ToolStrip.Items%2A> da coleção. Você pode acessar todos os itens em um <xref:System.Windows.Forms.ToolStripDropDownItem> por meio <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> da coleção. Em uma classe derivada de <xref:System.Windows.Forms.ToolStrip>, você também pode usar a <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> propriedade para acessar somente os itens que são exibidos no momento. Estes são os itens que não estão atualmente em um menu de estouro.

Os itens a seguir foram projetados especificamente para funcionar diretamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para <xref:System.Windows.Forms.ToolStrip> o controle:

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>é o contêiner de nível superior que substitui <xref:System.Windows.Forms.MainMenu>. Ele também oferece os recursos de manipulação de chaves e MDI (interface de múltiplos documentos). Funcionalmente <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.MenuStrip>e funcionam juntamente com o, embora sejam derivados de <xref:System.Windows.Forms.ToolStripItem>. <xref:System.Windows.Forms.ToolStripDropDownItem>

Os itens a seguir foram projetados especificamente para funcionar diretamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para <xref:System.Windows.Forms.MenuStrip> o controle:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip>Substitui o <xref:System.Windows.Forms.StatusBar> controle. Os recursos especiais <xref:System.Windows.Forms.StatusStrip> do incluem um layout de tabela personalizado, suporte para as alças de dimensionamento e movimentação do `Spring` formulário e a propriedade, <xref:System.Windows.Forms.ToolStripStatusLabel> que permite que um preencha automaticamente o espaço disponível.

Os itens a seguir foram projetados especificamente para funcionar diretamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para <xref:System.Windows.Forms.StatusStrip> o controle:

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip> substitui <xref:System.Windows.Forms.ContextMenu>. Você pode associar um <xref:System.Windows.Forms.ContextMenuStrip> a qualquer controle e um clique com o botão direito do mouse exibe automaticamente o menu de contexto (ou menu de atalho). Você pode mostrar um <xref:System.Windows.Forms.ContextMenuStrip> programaticamente usando <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> o método. <xref:System.Windows.Forms.ContextMenuStrip>dá suporte <xref:System.Windows.Forms.ToolStripDropDown.Opening> a <xref:System.Windows.Forms.ToolStripDropDown.Closing> cancelamento e eventos para manipular cenários de preenchimento dinâmico e de vários cliques. <xref:System.Windows.Forms.ContextMenuStrip>dá suporte a imagens, estado de verificação de item de menu, texto, chaves de acesso, atalhos e menus em cascata.

Os itens a seguir foram projetados especificamente para funcionar diretamente com ambos <xref:System.Windows.Forms.ToolStripSystemRenderer> e <xref:System.Windows.Forms.ToolStripProfessionalRenderer> em todas as orientações. Eles estão disponíveis por padrão em tempo de design para <xref:System.Windows.Forms.ContextMenuStrip> o controle:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>Recursos genéricos de ToolStrip

Os tópicos a seguir descrevem os recursos e o comportamento que são <xref:System.Windows.Forms.ToolStrip> genéricos para os controles e derivados.

#### <a name="painting"></a>Pintura

Você pode fazer pintura personalizada em <xref:System.Windows.Forms.ToolStrip> controles de várias maneiras. Assim como ocorre com outros controles Windows Forms <xref:System.Windows.Forms.ToolStrip> , <xref:System.Windows.Forms.ToolStripItem> o e ambos `OnPaint` têm métodos `Paint` e eventos substituíveis. Assim como ocorre com pintura regular, o sistema de coordenadas é relativo à área de cliente do controle, ou seja, o canto superior esquerdo do controle é 0, 0. O `Paint` evento e `OnPaint` o método para <xref:System.Windows.Forms.ToolStripItem> um comportamento como outros eventos de pintura de controle.

Os <xref:System.Windows.Forms.ToolStrip> controles também fornecem acesso mais preciso à renderização dos itens e do contêiner por meio <xref:System.Windows.Forms.ToolStripRenderer> da classe, que tem métodos substituíveis para pintar o plano de fundo, o plano de fundo do item, a imagem do item, a seta do item, o texto do item e a borda do <xref:System.Windows.Forms.ToolStrip>. Os argumentos de evento para esses métodos expõem várias propriedades como retângulos, cores e formatos de texto que você pode ajustar conforme desejado.

Para ajustar apenas alguns aspectos de como um item é pintado, você normalmente substitui o <xref:System.Windows.Forms.ToolStripRenderer>.

Se você estiver escrevendo um novo item e desejar controlar todos os aspectos de pintura, substitua o método `OnPaint`. De dentro `OnPaint`do, você pode usar métodos <xref:System.Windows.Forms.ToolStripRenderer>do.

Por padrão, o <xref:System.Windows.Forms.ToolStrip> é armazenado em buffer duplo, aproveitando a <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> configuração.

#### <a name="parenting"></a>Gerenciamento do domínio pai

O conceito de propriedade de contêiner e pai é mais complexo em <xref:System.Windows.Forms.ToolStrip> controles do que em outros controles de contêiner Windows Forms. Isso é necessário para dar suporte a cenários dinâmicos, como estouro, compartilhamento de itens suspensos em vários <xref:System.Windows.Forms.ToolStrip> itens e suporte à geração de um <xref:System.Windows.Forms.ContextMenuStrip> de um controle.

A lista a seguir descreve os membros relacionados ao gerenciamento do domínio pai e explica o seu uso.

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>acessa o item que é a origem do item suspenso. Isso é semelhante a <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, mas em vez de retornar um controle, ele retorna <xref:System.Windows.Forms.ToolStripItem>um.

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>determina qual controle é a origem do <xref:System.Windows.Forms.ContextMenuStrip> quando vários controles compartilham o mesmo. <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>é um acessador somente leitura para <xref:System.Windows.Forms.ToolStripItem.Parent%2A> a propriedade. Um pai difere de um proprietário no qual um pai denota o atual <xref:System.Windows.Forms.ToolStrip> retornado no qual o item é exibido, o que pode estar na área de estouro.

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>Retorna a <xref:System.Windows.Forms.ToolStrip> coleção cujos itens contém o atual <xref:System.Windows.Forms.ToolStripItem>. Essa é a melhor maneira de referenciar <xref:System.Windows.Forms.ToolStrip.ImageList%2A> ou de outras propriedades no nível <xref:System.Windows.Forms.ToolStrip> superior sem escrever código especial para lidar com o estouro.

#### <a name="behavior-of-inherited-controls"></a>Comportamento de controles herdados

Os seguintes controles são bloqueados sempre que eles são usados em herança:

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>Isso inclui os painéis em um <xref:System.Windows.Forms.ToolStripContainer> e também controles <xref:System.Windows.Forms.ToolStripPanel> individuais.

Por exemplo, crie um novo aplicativo dos Windows Forms usando um ou mais dos controles na lista anterior. Defina o modificador de acesso de um ou mais controles para `public` ou `protected` e, em seguida, compile o projeto. Adicione um formulário que herda do primeiro formulário e, em seguida, selecione um controle herdado. O controle aparece bloqueado, comportando-se como se o seu modificador de acesso fosse `private`.

#### <a name="toolstripcontainer-support-of-inheritance"></a>Suporte Herança de ToolStripContainer

O <xref:System.Windows.Forms.ToolStripContainer> controle dá suporte a cenários herdados limitados, semelhante ao exemplo a seguir:

1. Criar um novo aplicativo Windows Form.

2. Adicione um <xref:System.Windows.Forms.ToolStripContainer> ao formulário.

3. Defina o modificador de acesso <xref:System.Windows.Forms.ToolStripContainer> de `public` para `protected`ou.

4. Adicione qualquer combinação de <xref:System.Windows.Forms.ToolStrip>controles <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.ContextMenuStrip> às <xref:System.Windows.Forms.ToolStripPanel> regiões do <xref:System.Windows.Forms.ToolStripContainer>.

5. Compile o projeto.

6. Adicione um formulário que herda do primeiro formulário.

7. Selecione o herdado <xref:System.Windows.Forms.ToolStripContainer> no formulário.

#### <a name="inherited-behavior-of-child-controls"></a>Comportamento herdado de controles filho

Depois de você concluir as etapas anteriores, ocorre o seguinte comportamento herdado:

- No designer, o controle aparece com um ícone herdado.

- Os <xref:System.Windows.Forms.ToolStripPanel> controles estão bloqueados; você não pode selecionar ou reorganizar seu conteúdo.

- Você pode adicionar controles ao <xref:System.Windows.Forms.ToolStripContentPanel>, mover os controles e torná-los controles filho <xref:System.Windows.Forms.ToolStripContentPanel>do.

- Suas alterações persistem após compilar o formulário.

  > [!NOTE]
  > Remova os modificadores de acesso de <xref:System.Windows.Forms.ToolStripPanel> todos os controles que fazem parte <xref:System.Windows.Forms.ToolStripContainer>de um. O modificador de acesso <xref:System.Windows.Forms.ToolStripContainer> do governa o controle inteiro.

#### <a name="partial-trust"></a>Confiança parcial

As limitações de `ToolStrip`s sob confiança parcial são projetadas para impedir entrada acidental de informações pessoais que possam ser usadas por pessoas ou serviços não autorizados. As medidas de proteção são as seguintes:

- `ToolStripDropDown`os controles <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> precisam exibir itens em um <xref:System.Windows.Forms.ToolStripControlHost>. Isso se aplica a ambos os controles <xref:System.Windows.Forms.ToolStripTextBox> <xref:System.Windows.Forms.ToolStripComboBox>intrínsecos, como <xref:System.Windows.Forms.ToolStripProgressBar> , e, bem como para controles criados pelo usuário. Se esse requisito não for atendido, esses itens não serão exibidos. Nenhuma exceção é lançada.

- Não é <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> permitido definir `false` a propriedade como, e o parâmetro <xref:System.Windows.Forms.ToolStripDropDown.Closing> de evento cancelável é ignorado. Isso torna impossível realizar mais de um pressionamento da tecla sem fechar o item suspenso. Se esse requisito não for atendido, esses itens não serão exibidos. Nenhuma exceção é lançada.

- Muitos eventos de tratamento de teclas não serão gerados se ocorrerem em contextos de confiança parcial <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>diferentes de.

- As chaves de acesso não são <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> processadas quando não é concedido.

#### <a name="usage"></a>Uso

Os seguintes padrões de uso têm uma influência <xref:System.Windows.Forms.ToolStrip> sobre layout, interação do teclado e comportamento do usuário final:

- Ingressado em um<xref:System.Windows.Forms.ToolStripPanel>

  O <xref:System.Windows.Forms.ToolStrip> pode ser reposicionado dentro do <xref:System.Windows.Forms.ToolStripPanel> e em <xref:System.Windows.Forms.ToolStripPanel>s. A `Dock` propriedade é ignorada e, se <xref:System.Windows.Forms.ToolStrip.Stretch%2A> a propriedade `false`for, o tamanho do <xref:System.Windows.Forms.ToolStrip> aumentará à medida que os itens <xref:System.Windows.Forms.ToolStripPanel>forem adicionados ao. Normalmente, o <xref:System.Windows.Forms.ToolStrip> não participa da ordem de tabulação.

- Encaixado

  O <xref:System.Windows.Forms.ToolStrip> é colocado em um lado de um contêiner em uma posição fixa e seu tamanho se expande sobre toda a borda para a qual ele está encaixado. Normalmente, o <xref:System.Windows.Forms.ToolStrip> não participa da ordem de tabulação.

- Posição absoluta

  O <xref:System.Windows.Forms.ToolStrip> é como outros controles, pois é colocado <xref:System.Windows.Forms.Control.Location%2A> pela propriedade, tem um tamanho fixo e normalmente participa da ordem de tabulação.

#### <a name="keyboard-interaction"></a>Interação do teclado

##### <a name="access-keys"></a>Teclas de acesso

Combinadas com ou após a tecla ALT, as teclas de acesso são uma maneira de ativar um controle usando o teclado. <xref:System.Windows.Forms.ToolStrip>dá suporte a chaves de acesso explícitas e implícitas. A definição explícita usa um caractere e comercial (&) que precede a letra. A definição implícita usa um algoritmo que tenta encontrar um item correspondente com base na ordem de caracteres em uma determinada propriedade `Text`.

##### <a name="shortcut-keys"></a>Teclas de Atalho

As teclas de atalho usadas por <xref:System.Windows.Forms.MenuStrip> um usam uma combinação <xref:System.Windows.Forms.Keys> da enumeração (que não é específica de ordem) para definir a tecla de atalho. Você também pode usar a <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> propriedade para exibir uma tecla de atalho somente com texto, como exibir "del" em vez de "excluir".

##### <a name="navigation"></a>Navegação

A tecla ALT ativa a <xref:System.Windows.Forms.MenuStrip> apontada para by. <xref:System.Windows.Forms.Form.MainMenuStrip%2A> A partir daí, Ctrl + Tab navega entre <xref:System.Windows.Forms.ToolStrip> os controles `ToolStripPanel`dentro de s. A tecla TAB e as teclas de direção no teclado numérico navegam entre os itens <xref:System.Windows.Forms.ToolStrip>em um. Um algoritmo especial manipula a navegação na região de estouro. A barra de <xref:System.Windows.Forms.ToolStripButton>espaços <xref:System.Windows.Forms.ToolStripDropDownButton>seleciona um <xref:System.Windows.Forms.ToolStripSplitButton>, ou.

##### <a name="focus-and-validation"></a>Foco e validação

Quando ativado pela tecla Alt, o <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ToolStrip> normalmente não demora nem remove o foco do controle que atualmente tem o foco. Se houver um controle hospedado no <xref:System.Windows.Forms.MenuStrip> ou em uma lista suspensa <xref:System.Windows.Forms.MenuStrip>do, o controle ganha foco quando o usuário pressiona a tecla Tab. Em geral, os <xref:System.Windows.Forms.Control.GotFocus> <xref:System.Windows.Forms.Control.Leave> eventos <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, e de <xref:System.Windows.Forms.MenuStrip> podem não ser gerados quando são ativados pelo teclado. Nesses casos, use os <xref:System.Windows.Forms.MenuStrip.MenuActivate> eventos e <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> em vez disso.

Por padrão, <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> é `false`. Chame <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitamente no formulário para executar a validação.

#### <a name="layout"></a>Layout

Você controla <xref:System.Windows.Forms.ToolStrip> o layout escolhendo um dos membros de <xref:System.Windows.Forms.ToolStripLayoutStyle> com a <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> propriedade.

##### <a name="stack-layouts"></a>Layouts de pilha

O empilhamento é a organização de itens ao lado de ambos em ambas as <xref:System.Windows.Forms.ToolStrip>extremidades do. A lista a seguir descreve os layouts de pilha.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> é o padrão. Essa configuração faz com <xref:System.Windows.Forms.ToolStrip> que o altere seu layout automaticamente de acordo com <xref:System.Windows.Forms.ToolStrip.Orientation%2A> a propriedade para lidar com cenários de arrastar e encaixar.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>renderiza os itens <xref:System.Windows.Forms.ToolStrip> ao lado um do outro verticalmente.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>renderiza os itens <xref:System.Windows.Forms.ToolStrip> ao lado um do outro horizontalmente.

##### <a name="other-features-of-stack-layouts"></a>Outros recursos de layouts de pilha

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>determina o final do <xref:System.Windows.Forms.ToolStrip> até o qual o item é alinhado.

Quando os itens não se ajustam <xref:System.Windows.Forms.ToolStrip>no, um botão de estouro é exibido automaticamente. A <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> configuração de propriedade determina se um item aparece na área de estouro sempre, conforme necessário ou nunca.

No evento, você pode inspecionar a <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriedade para determinar se um item foi colocado no principal <xref:System.Windows.Forms.ToolStrip>, o estouro <xref:System.Windows.Forms.ToolStrip>ou se ele não está sendo exibido no momento. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> Os motivos típicos para um item não ser exibido são que o item não se ajustou ao <xref:System.Windows.Forms.ToolStrip> Main e <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> sua propriedade foi definida <xref:System.Windows.Forms.ToolStripItemOverflow.Never>como.

Torne um <xref:System.Windows.Forms.ToolStrip> móvel, colocando-o em <xref:System.Windows.Forms.ToolStripPanel> um e definindo <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> seu <xref:System.Windows.Forms.ToolStripGripStyle.Visible>como.

##### <a name="other-layout-options"></a>Outras opções de layout

As outras opções de layout <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> são <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>e.

##### <a name="flow-layout"></a>Layout de fluxo

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>layout é o padrão para <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>e <xref:System.Windows.Forms.ToolStripOverflow>. É semelhante ao <xref:System.Windows.Forms.FlowLayoutPanel>. Os recursos de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> layout são os seguintes:

- Todos os recursos do <xref:System.Windows.Forms.FlowLayoutPanel> são expostos <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> pela propriedade. Você deve converter a <xref:System.Windows.Forms.LayoutSettings> classe em uma <xref:System.Windows.Forms.FlowLayoutSettings> classe.

- Você pode usar as <xref:System.Windows.Forms.ToolStripItem.Dock%2A> propriedades <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> e no código para alinhar os itens dentro da linha.

- A propriedade <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é ignorada.

- No evento, você pode inspecionar a <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriedade para determinar se um item foi colocado no principal <xref:System.Windows.Forms.ToolStrip> ou se não se ajustou. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- A alça não é renderizada e, portanto <xref:System.Windows.Forms.ToolStrip> , <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> um estilo de layout <xref:System.Windows.Forms.ToolStripPanel> in em um não pode ser movido.

- O <xref:System.Windows.Forms.ToolStrip> botão de estouro não é renderizado <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> e é ignorado.

##### <a name="table-layout"></a>Layout da tabela

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>layout é o padrão para <xref:System.Windows.Forms.StatusStrip>. É semelhante a <xref:System.Windows.Forms.TableLayoutPanel>. Os recursos de <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> layout são os seguintes:

- Todos os recursos do <xref:System.Windows.Forms.TableLayoutPanel> são expostos <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> pela propriedade. Você deve converter a <xref:System.Windows.Forms.LayoutSettings> classe em uma <xref:System.Windows.Forms.TableLayoutSettings> classe.

- Você pode usar as <xref:System.Windows.Forms.ToolStripItem.Dock%2A> propriedades <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> e no código para alinhar os itens na célula da tabela.

- A propriedade <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> é ignorada.

- No evento, você pode inspecionar a <xref:System.Windows.Forms.ToolStripItem.Placement%2A> propriedade para determinar se um item foi colocado no principal <xref:System.Windows.Forms.ToolStrip> ou se não se ajustou. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- A alça não é renderizada e, portanto <xref:System.Windows.Forms.ToolStrip> , <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> um estilo de layout <xref:System.Windows.Forms.ToolStripPanel> in em um não pode ser movido.

- O <xref:System.Windows.Forms.ToolStrip> botão de estouro não é renderizado <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> e é ignorado.

## <a name="toolstripitem"></a>ToolStripItem

Os tópicos a seguir <xref:System.Windows.Forms.ToolStripItem> descrevem e os controles que derivam dele.

<xref:System.Windows.Forms.ToolStripItem>é a classe base abstrata para todos os itens que entram em um <xref:System.Windows.Forms.ToolStrip>. O modelo de objeto a seguir <xref:System.Windows.Forms.ToolStripItem> mostra a hierarquia de herança.

![Diagrama que mostra o modelo de objeto de ToolStripItem.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>as classes herdam diretamente <xref:System.Windows.Forms.ToolStripItem>do ou herdam indiretamente de <xref:System.Windows.Forms.ToolStripControlHost> por <xref:System.Windows.Forms.ToolStripDropDownItem>meio de <xref:System.Windows.Forms.ToolStripItem> ou.

<xref:System.Windows.Forms.ToolStripItem>os controles devem estar contidos em <xref:System.Windows.Forms.ToolStrip>um <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, ou <xref:System.Windows.Forms.ContextMenuStrip> e não podem ser adicionados diretamente a um formulário. As várias classes de contêiner foram projetadas para conter um subconjunto apropriado de <xref:System.Windows.Forms.ToolStripItem> controles.

A tabela a seguir lista os <xref:System.Windows.Forms.ToolStripItem> controles de estoque e os contêineres em que eles parecem melhores. Embora qualquer <xref:System.Windows.Forms.ToolStrip> item possa ser hospedado em qualquer <xref:System.Windows.Forms.ToolStrip>contêiner derivado, esses itens foram projetados para parecer melhor nos seguintes contêineres:

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>Não aparece na caixa de ferramentas do designer.

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

<xref:System.Windows.Forms.ToolStripButton>é o item de botão <xref:System.Windows.Forms.ToolStrip>para. Você pode exibi-lo com vários estilos de borda e pode usá-lo para representar e ativar estados operacionais. Você também pode defini-lo para ter o foco por padrão.

### <a name="toolstriplabel"></a>ToolStripLabel

O <xref:System.Windows.Forms.ToolStripLabel> fornece a funcionalidade de <xref:System.Windows.Forms.ToolStrip> rótulo em controles. O <xref:System.Windows.Forms.ToolStripLabel> é como um <xref:System.Windows.Forms.ToolStripButton> que não tem o foco por padrão e que não é renderizado como Push ou realçado.

<xref:System.Windows.Forms.ToolStripLabel>como um item hospedado dá suporte a chaves de acesso.

Use as <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>propriedades <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, e <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> em um <xref:System.Windows.Forms.ToolStripLabel> para dar suporte ao controle de link <xref:System.Windows.Forms.ToolStrip>em um.

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>é uma versão do <xref:System.Windows.Forms.ToolStripLabel> projetada especificamente para uso no <xref:System.Windows.Forms.StatusStrip>. Os recursos especiais incluem <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>e <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.

### <a name="toolstripseparator"></a>ToolStripSeparator

O <xref:System.Windows.Forms.ToolStripSeparator> adiciona uma linha vertical ou horizontal a uma barra de ferramentas ou menu, dependendo da orientação. Ele fornece o agrupamento de ou a distinção entre itens, assim como aqueles em um menu.

Você pode adicionar um <xref:System.Windows.Forms.ToolStripSeparator> em tempo de design escolhendo-o em uma lista suspensa. No entanto, você também pode criar <xref:System.Windows.Forms.ToolStripSeparator> automaticamente um digitando um hífen (-) no nó do modelo do designer ou <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> no método.

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>é a classe base abstrata para <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>e <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost>pode hospedar outros controles, incluindo controles personalizados, de duas maneiras:

- Construa um <xref:System.Windows.Forms.ToolStripControlHost> com uma classe derivada de <xref:System.Windows.Forms.Control>. Para acessar totalmente o controle hospedado e as propriedades, você deve converter <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> a propriedade de volta para a classe real que ela representa.

- Estenda <xref:System.Windows.Forms.ToolStripControlHost>e, no construtor sem parâmetros da classe Inherited, chame o construtor da classe base passando uma classe derivada de <xref:System.Windows.Forms.Control>. Essa opção permite que você envolva métodos e propriedades de controle comuns para facilitar o <xref:System.Windows.Forms.ToolStrip>acesso em um.

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>é otimizado para hospedagem em um <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ComboBox> Um subconjunto das propriedades e dos eventos do controle hospedado é exposto no <xref:System.Windows.Forms.ToolStripComboBox> nível, mas o controle <xref:System.Windows.Forms.ComboBox> subjacente é totalmente acessível por meio <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> da propriedade.

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>é otimizado para hospedagem em um <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.TextBox> Um subconjunto das propriedades e dos eventos do controle hospedado é exposto no <xref:System.Windows.Forms.ToolStripTextBox> nível, mas o controle <xref:System.Windows.Forms.TextBox> subjacente é totalmente acessível por meio <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> da propriedade.

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>é otimizado para hospedagem em um <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ProgressBar> Um subconjunto das propriedades e dos eventos do controle hospedado é exposto no <xref:System.Windows.Forms.ToolStripProgressBar> nível, mas o controle <xref:System.Windows.Forms.ProgressBar> subjacente é totalmente acessível por meio <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> da propriedade.

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>é a classe base abstrata para <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>e <xref:System.Windows.Forms.ToolStripSplitButton>, que pode hospedar itens diretamente ou hospedar itens adicionais em um contêiner suspenso. Você faz isso definindo <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> a propriedade <xref:System.Windows.Forms.ToolStripDropDown> como a e <xref:System.Windows.Forms.ToolStripDropDown>definindo a <xref:System.Windows.Forms.ToolStrip.Items%2A> Propriedade do. Acesse esses itens suspensos diretamente por meio <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> da propriedade.

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>é um <xref:System.Windows.Forms.ToolStripDropDownItem> que funciona com <xref:System.Windows.Forms.ToolStripDropDownMenu> o <xref:System.Windows.Forms.ContextMenuStrip> e o para lidar com o realce especial, o layout e a organização de colunas para menus.

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>é semelhante <xref:System.Windows.Forms.ToolStripButton>a, mas mostra uma área suspensa quando o usuário clica nele. Oculte ou mostre a seta suspensa definindo a <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> propriedade. <xref:System.Windows.Forms.ToolStripDropDownButton>hospeda um <xref:System.Windows.Forms.ToolStripOverflowButton> que exibe itens que estouram o <xref:System.Windows.Forms.ToolStrip>.

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>combina o botão e a funcionalidade do botão suspenso.

Use a <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> propriedade para sincronizar o <xref:System.Windows.Forms.Control.Click> evento do item suspenso escolhido com o item mostrado no botão.

### <a name="toolstripitem-generic-features"></a>Recursos genéricos de ToolStripItem

<xref:System.Windows.Forms.ToolStripItem>fornece os seguintes recursos genéricos e opções para herdar controles:

- Eventos principais

- Tratamento de imagem

- Alinhamento

- Relação de texto e imagem

- Estilo de exibição

#### <a name="core-events"></a>Eventos Principais

<xref:System.Windows.Forms.ToolStripItem>os controles recebem seus próprios eventos Click, mouse e Paint e também podem executar alguns pré-processamento de teclado.

#### <a name="image-handling"></a>Tratamento de Imagem

As <xref:System.Windows.Forms.ToolStripItem.Image%2A>propriedades <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, ,<xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A> ,<xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>e pertencem<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> a vários aspectos da manipulação de imagens. Use imagens em <xref:System.Windows.Forms.ToolStrip> controles definindo essas propriedades diretamente ou definindo a propriedade de tempo de execução – somente <xref:System.Windows.Forms.ToolStrip.ImageList%2A> .

O dimensionamento de imagem é determinado pela interação das propriedades <xref:System.Windows.Forms.ToolStrip> no <xref:System.Windows.Forms.ToolStripItem>e no, da seguinte maneira:

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>é a escala da imagem final, conforme determinado pela combinação da configuração da <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> imagem e da configuração do <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> contêiner.

  - Se <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStripItemImageScaling> é `true` (o padrão) e é <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, nenhum dimensionamento de imagem ocorre, <xref:System.Windows.Forms.ToolStrip> e o tamanho é o do maior item ou um tamanho mínimo prescrito.

  - Se <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> for `false` e for<xref:System.Windows.Forms.ToolStripItemImageScaling> <xref:System.Windows.Forms.ToolStrip> , nenhumaimagemouescalaocorrerá<xref:System.Windows.Forms.ToolStripItemImageScaling.None>.

#### <a name="alignment"></a>Alinhamento

O valor da <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriedade determina o final <xref:System.Windows.Forms.ToolStrip> do qual um item aparece. A <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Propriedade funciona somente quando o estilo <xref:System.Windows.Forms.ToolStrip> de layout de é definido como um dos valores de stack overflow.

Os itens são colocados <xref:System.Windows.Forms.ToolStrip> no na ordem em que os itens aparecem na coleção de itens. Para alterar programaticamente onde um item é disposto, use <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> o método para mover o item na coleção. Esse método move o item, mas não o duplica.

#### <a name="text-and-image-relationship"></a>Relação de Texto e Imagem

A <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriedade define o posicionamento relativo da imagem em relação ao texto em um <xref:System.Windows.Forms.ToolStripItem>. Itens que não têm uma imagem, texto ou ambos são tratados como casos especiais para que o <xref:System.Windows.Forms.ToolStripItem> não exiba um ponto em branco para o elemento ou elementos ausentes.

#### <a name="display-style"></a>Estilo de Exibição

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>permite definir os valores das propriedades de texto e imagem de um item enquanto exibe apenas o que você deseja. Isso normalmente é usado para alterar o estilo de exibição ao mostrar o mesmo item em um contexto diferente.

## <a name="accessory-classes"></a>Classes acessórias

Classes que fornecem várias outras funcionalidades incluem:

- <xref:System.Windows.Forms.ToolStripManager>oferece <xref:System.Windows.Forms.ToolStrip>suporte a tarefas relacionadas a aplicativos inteiros, como opções de mesclagem, configurações e processador.

- <xref:System.Windows.Forms.ToolStripRenderer>permite que você aplique um estilo ou tema específico a uma <xref:System.Windows.Forms.ToolStrip> facilidade.

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>cria canetas e pincéis com base em uma tabela de<xref:System.Windows.Forms.ProfessionalColorTable>cores substituível ().

- <xref:System.Windows.Forms.ToolStripSystemRenderer>aplica cores do sistema e um estilo visual plano <xref:System.Windows.Forms.ToolStrip> a aplicativos.

- <xref:System.Windows.Forms.ToolStripContainer>é semelhante a <xref:System.Windows.Forms.SplitContainer>. Ele usa quatro painéis laterais encaixados (instâncias <xref:System.Windows.Forms.ToolStripPanel>de) e um painel central (uma instância <xref:System.Windows.Forms.ToolStripContentPanel>do) para criar uma organização típica. Não é possível remover os painéis laterais, mas você pode ocultá-los. Não é possível remover nem ocultar o painel central. Você pode organizar um ou mais <xref:System.Windows.Forms.ToolStrip>controles <xref:System.Windows.Forms.MenuStrip>, ou <xref:System.Windows.Forms.StatusStrip> nos painéis laterais, e pode usar o painel central para outros controles. O <xref:System.Windows.Forms.ToolStripContentPanel> também fornece uma maneira de obter suporte ao processador no corpo do formulário para uma aparência consistente. <xref:System.Windows.Forms.ToolStripContainer>o não oferece suporte a interface de vários documentos (MDI).

- <xref:System.Windows.Forms.ToolStripPanel>fornece espaço para mover e organizar <xref:System.Windows.Forms.ToolStrip> controles. Você pode usar apenas um painel, se preferir, e <xref:System.Windows.Forms.ToolStripPanel> funciona bem em cenários de MDI.

## <a name="see-also"></a>Consulte também

- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
- [Controle MenuStrip](menustrip-control-windows-forms.md)
- [Controle StatusStrip](statusstrip-control.md)
- [Controle ContextMenuStrip](contextmenustrip-control.md)
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
