---
title: Resumo da tecnologia de ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: d447f78a6b6d8a71ea2e67d4c991655eb4712199
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654703"
---
# <a name="toolstrip-technology-summary"></a>Resumo da tecnologia de ToolStrip
Este tópico resume as informações sobre o controle `ToolStrip` e as classes que dão suporte ao seu uso.  
  
 O controle `ToolStrip` e suas classes associadas fornecem uma solução completa para a criação de menus, barras de ferramentas e barras de status.  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Informações preliminares  
 Com o controle `ToolStrip` e suas classes associadas, você pode criar a funcionalidade de ferramentas avançada com aparência e comportamento profissional e consistente. O controle `ToolStrip` e as classes oferecem os seguintes aperfeiçoamentos em relação aos controles anteriores:  
  
- Um modelo de evento mais consistente.  
  
- Um comportamento de tempo de design mais consistente que contém listas de tarefas e editores de coleção de item.  
  
- Renderização personalizada com `ToolStripManager` e `ToolStripRenderer`.  
  
- Reposicionamento interno (compartilhamento de espaço horizontal ou vertical dentro da área de ferramenta quando encaixado) com `ToolStripContainer` e `ToolStripPanel`.  
  
- Tempo de design e tempo de execução de reordenação de itens com o <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> propriedade.  
  
- Realocação de itens a um menu de estouro com o <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> propriedade.  
  
- Local do controle completamente configurável com `ToolStripContainer`, `ToolStripPanel` e `ToolStripContentPanel`.  
  
- Hospedagem controles `ToolStrip`, tradicionais ou personalizados usando `ToolStripControlHost`.  
  
- Mesclagem de controles `ToolStrip` usando `ToolStripPanel`.  
  
 `ToolStrip` é a classe base extensível para `MenuStrip`, `ContextMenuStrip` e `StatusStrip`. Esses controles são <xref:System.Windows.Forms.ToolStripItem> contêineres que herdam comportamento comum e manipulação de eventos estendidos para que cada implementação lide com o comportamento que é apropriado para ele. Controles que derivam de <xref:System.Windows.Forms.ToolStripItem> são listados na tabela a seguir. A classe `ToolStrip` base manipula eventos do tipo "arrastar e soltar", entrada do usuário e pintura para esses controles.  
  
 Os controles `ToolStrip`, `MenuStrip`, `ContextMenuStrip` e `StatusStrip` substituem a barra de ferramentas anterior, menu, menu de atalho e controles da barra de status, embora esses controles sejam mantidos para compatibilidade com versões anteriores.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Visão geral das classes de ToolStrip  
 A tabela a seguir mostra as classes de ToolStrip agrupadas por área de tecnologia.  
  
|Área de tecnologia|Classe|  
|---------------------|-----------|  
|Contêineres de Menu, status e barra de ferramentas|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|Itens de ToolStrip|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Local|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Apresentação e renderização|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>Recursos de tempo de design de ToolStrip  
 O <xref:System.Windows.Forms.ToolStrip> família de controles oferece um rico conjunto de ferramentas e modelos no lugar de edição e definição de base da interface do usuário para que você pode criar rapidamente um aplicativo de trabalho.  
  
### <a name="task-dialog-boxes"></a>Caixas de diálogo da tarefa  
 No Visual Studio, clicar na smart tag em um controle no designer exibe uma lista de tarefas para ter acesso fácil a muitos comandos usados com frequência.  
  
- [Caixa de diálogo de tarefas do MenuStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233645(v=vs.100))  
  
- [Caixa de diálogo de tarefas do ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233648(v=vs.100))  
  
- [Caixa de diálogo de tarefas do ContextMenuStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233646(v=vs.100))  
  
- [Caixa de diálogo de tarefas do StatusStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100))  
  
- [Caixa de diálogo de tarefas do ToolStripContainer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233647(v=vs.100))  
  
### <a name="items-collection-editors"></a>Editores de coleção de itens  
 No Visual Studio, quando você clica em **Editar itens** na lista de tarefas ou clica com o botão direito do mouse no controle e seleciona **Editar Itens** no menu de atalho, o editor de coleção para o controle é exibido. Editores de coleção permitem adicionar, remover e reordenar os itens que o controle contém. Você também pode exibir e alterar as propriedades para o controle e os itens do controle.  
  
- [Editor de coleção de itens do MenuStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233625(v=vs.100))  
  
- [Editor de coleção de itens StatusStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100))  
  
- [Editor de coleção de itens ContextMenuStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233641(v=vs.100))  
  
- [Editor de coleção de itens ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))  
  
## <a name="hosting-controls"></a>Hospedagem de controles  
 O <xref:System.Windows.Forms.ToolStripControlHost> classe fornece wrappers internos para <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, e <xref:System.Windows.Forms.ToolStripProgressBar> controles. Você também pode hospedar qualquer outro controle existente ou COM em um <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Para obter um exemplo de hospedagem de controle, consulte [como: Encapsular um controle dos Windows Forms com ToolStripControlHost](how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>Renderização  
 <xref:System.Windows.Forms.ToolStrip> classes implementam um esquema de renderização é significativamente diferente de outros controles dos Windows Forms. Com esse esquema, você pode facilmente aplicar estilos e temas.  
  
 Para aplicar um estilo para um <xref:System.Windows.Forms.ToolStrip> e todos os as <xref:System.Windows.Forms.ToolStripItem> objetos que ele contém, você não precisa lidar com o <xref:System.Windows.Forms.ToolStripItem.Paint> evento para cada item. Em vez disso, você pode definir as <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> propriedade para um dos <xref:System.Windows.Forms.ToolStripRenderMode> valores diferentes de <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Como alternativa, você pode definir as <xref:System.Windows.Forms.ToolStrip.Renderer%2A> diretamente para qualquer classe que herda o <xref:System.Windows.Forms.ToolStripRenderer> classe. Configuração para essa propriedade define automaticamente o <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Você pode aplicar o mesmo estilo a vários <xref:System.Windows.Forms.ToolStrip> objetos no mesmo aplicativo, definindo o <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> para <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> e definindo o <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> ou <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> propriedade a ser <xref:System.Windows.Forms.ToolStripManagerRenderMode> que você deseja ou <xref:System.Windows.Forms.ToolStripRenderer> valor, respectivamente.  
  
 Para obter exemplos de renderização, consulte [como: Criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Estilos e temas  
 <xref:System.Windows.Forms.ToolStrip> e as classes associadas fornecem uma maneira fácil de dar suporte a estilos visuais e aparência personalizada que não exigem a substituição de <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> métodos para cada item. Use o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> e o <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> e <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriedades.  
  
## <a name="rafting-and-docking"></a>Reposicionamento e encaixe  
 Você pode reposicionar, encaixar ou posicionar absolutamente <xref:System.Windows.Forms.ToolStrip> controles. <xref:System.Windows.Forms.ToolStrip> itens são apresentados pelo <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> do contêiner.  
  
 O *reposicionamento* é a capacidade das barras de ferramenta de compartilhar espaço horizontal ou vertical. Um formulário do Windows pode ter um <xref:System.Windows.Forms.ToolStripContainer> que por sua vez tem painéis à esquerda, direita, superior e lados da parte inferior para posicionamento e reposicionamento do formulário <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles. Vários <xref:System.Windows.Forms.ToolStrip> controles são empilhados verticalmente ao colocá-los na esquerda ou direita <xref:System.Windows.Forms.ToolStripContainer>. Eles são empilhados horizontalmente se colocá-los na parte superior ou inferior <xref:System.Windows.Forms.ToolStripContainer>. Você pode usar a central <xref:System.Windows.Forms.ToolStripContentPanel> do <xref:System.Windows.Forms.ToolStripContainer> para posicionar controles tradicionais no formulário.  
  
 Uma ou todas as <xref:System.Windows.Forms.ToolStripContainer> controles são selecionáveis diretamente no tempo de design e pode ser excluídos. Um <xref:System.Windows.Forms.ToolStripContainer> é expansível e recolhível e redimensiona com os controles que ele contém.  
  
 O *encaixe* é a especificação de local de um controle simples na esquerda, direita, acima ou abaixo do formulário.  
  
 A vantagem do reposicionamento em relação ao encaixe é que <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles podem compartilhar espaço horizontal ou vertical com outros controles.  
  
 A maioria do <xref:System.Windows.Forms.ToolStrip> controles podem ser encaixados ao formulário como outros controles em vez de usar reposicionamento. Você também pode especificar que um <xref:System.Windows.Forms.ToolStrip> controle livremente posicionado no formulário removendo-o de seu <xref:System.Windows.Forms.ToolStripContainer> e configuração de seu `Dock` propriedade a ser `None`, ou você pode especificar sua posição absoluta Configurando os respectivos <xref:System.Windows.Forms.Control.Location%2A> propriedade. Confira [Como Remover um ToolStrip de um ToolStripContainer para um formulário](how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Use um ou mais <xref:System.Windows.Forms.ToolStripPanel> controles para obter mais flexibilidade, especialmente para aplicativos de Interface de documentos múltiplos (MDI), ou se você não precisa de um <xref:System.Windows.Forms.ToolStripContainer>. Um <xref:System.Windows.Forms.ToolStripPanel> fornece um espaço encaixável para localizar e reposicionamento <xref:System.Windows.Forms.ToolStrip> controles, mas não controles tradicionais. Por padrão, o <xref:System.Windows.Forms.ToolStripPanel> não aparece no designer de **caixa de ferramentas**, mas você pode colocá-lo lá clicando com o **caixa de ferramentas**e, em seguida, clique em **escolher itens**. Você pode também acessar programaticamente o <xref:System.Windows.Forms.ToolStripPanel> como qualquer outra classe.  
  
 O <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> permitem que os itens de estouro. Isso é semelhante à forma como esses itens se comportam em barras de ferramentas do Microsoft Office.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
