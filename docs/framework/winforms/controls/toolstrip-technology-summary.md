---
title: Resumo da tecnologia de ToolStrip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4777a6cb30f641faf2305bc6d8bca55d243c94b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-technology-summary"></a>Resumo da tecnologia de ToolStrip
Este tópico resume as informações sobre o controle `ToolStrip` e as classes que dão suporte ao seu uso.  
  
 O controle `ToolStrip` e suas classes associadas fornecem uma solução completa para a criação de menus, barras de ferramentas e barras de status.  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Informações preliminares  
 Com o controle `ToolStrip` e suas classes associadas, você pode criar a funcionalidade de ferramentas avançada com aparência e comportamento profissional e consistente. O controle `ToolStrip` e as classes oferecem os seguintes aperfeiçoamentos em relação aos controles anteriores:  
  
-   Um modelo de evento mais consistente.  
  
-   Um comportamento de tempo de design mais consistente que contém listas de tarefas e editores de coleção de item.  
  
-   Renderização personalizada com `ToolStripManager` e `ToolStripRenderer`.  
  
-   Reposicionamento interno (compartilhamento de espaço horizontal ou vertical dentro da área de ferramenta quando encaixado) com `ToolStripContainer` e `ToolStripPanel`.  
  
-   Tempo de design e tempo de execução de reorganização de itens com o <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> propriedade.  
  
-   Realocação de itens a um menu de estouro com o <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> propriedade.  
  
-   Local do controle completamente configurável com `ToolStripContainer`, `ToolStripPanel` e `ToolStripContentPanel`.  
  
-   Hospedagem controles `ToolStrip`, tradicionais ou personalizados usando `ToolStripControlHost`.  
  
-   Mesclagem de controles `ToolStrip` usando `ToolStripPanel`.  
  
 `ToolStrip` é a classe base extensível para `MenuStrip`, `ContextMenuStrip` e `StatusStrip`. Esses controles estão <xref:System.Windows.Forms.ToolStripItem> contêineres que herdam o comportamento comum e manipulação de eventos estendidos para que cada implementação lida com o comportamento que é apropriado para ele. Controles que derivam de <xref:System.Windows.Forms.ToolStripItem> são listados na tabela a seguir. A classe `ToolStrip` base manipula eventos do tipo "arrastar e soltar", entrada do usuário e pintura para esses controles.  
  
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
 O <xref:System.Windows.Forms.ToolStrip> família de controles fornece um rico conjunto de ferramentas e modelos para o local de edição e definindo a base da interface do usuário para que você pode criar rapidamente um aplicativo de trabalho.  
  
### <a name="task-dialog-boxes"></a>Caixas de diálogo da tarefa  
 No Visual Studio, clicar na smart tag em um controle no designer exibe uma lista de tarefas para ter acesso fácil a muitos comandos usados com frequência.  
  
-   [Caixa de diálogo de tarefas do MenuStrip](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [Caixa de diálogo de tarefas do ToolStrip](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [Caixa de diálogo de tarefas do ContextMenuStrip](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [Caixa de diálogo de tarefas do StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [Caixa de diálogo de tarefas do ToolStripContainer](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Editores de coleção de itens  
 No Visual Studio, quando você clica em **Editar itens** na lista de tarefas ou clica com o botão direito do mouse no controle e seleciona **Editar Itens** no menu de atalho, o editor de coleção para o controle é exibido. Editores de coleção permitem adicionar, remover e reordenar os itens que o controle contém. Você também pode exibir e alterar as propriedades para o controle e os itens do controle.  
  
-   [Editor de coleção de itens do MenuStrip](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [Editor de coleção de itens StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [Editor de coleção de itens ContextMenuStrip](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [Editor de coleção de itens ToolStrip](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Hospedagem de controles  
 O <xref:System.Windows.Forms.ToolStripControlHost> classe fornece wrappers internos para <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, e <xref:System.Windows.Forms.ToolStripProgressBar> controles. Você também pode hospedar qualquer outro existente ou COM controle em um <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Para um exemplo de hospedagem de controle, consulte [Como encapsular um controle dos Windows Forms com ToolStripControlHost](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>Renderização  
 <xref:System.Windows.Forms.ToolStrip>classes de implementar um esquema de renderização é significativamente diferente de outros controles de formulários do Windows. Com esse esquema, você pode facilmente aplicar estilos e temas.  
  
 Para aplicar um estilo para um <xref:System.Windows.Forms.ToolStrip> e todos os a <xref:System.Windows.Forms.ToolStripItem> objetos que ela contém, você não precisa lidar com o <xref:System.Windows.Forms.ToolStripItem.Paint> evento para cada item. Em vez disso, você pode definir o <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> propriedade para um do <xref:System.Windows.Forms.ToolStripRenderMode> valores diferentes de <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Como alternativa, você pode definir o <xref:System.Windows.Forms.ToolStrip.Renderer%2A> diretamente a qualquer classe que herda de <xref:System.Windows.Forms.ToolStripRenderer> classe. Configuração para essa propriedade define automaticamente o <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Você pode aplicar o mesmo estilo a vários <xref:System.Windows.Forms.ToolStrip> objetos no mesmo aplicativo, definindo o <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> para <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> e configuração de <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> ou <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> propriedade <xref:System.Windows.Forms.ToolStripManagerRenderMode> que você deseja ou <xref:System.Windows.Forms.ToolStripRenderer> valor, respectivamente.  
  
 Para exemplos de renderização, consulte [Como criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Estilos e temas  
 <xref:System.Windows.Forms.ToolStrip>e classes associadas fornecem uma maneira fácil de dar suporte a estilos visuais e aparência personalizada que não exigem substituindo o <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> métodos para cada item. Use o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> e <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> e <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriedades.  
  
## <a name="rafting-and-docking"></a>Reposicionamento e encaixe  
 Você pode reposicionamento, encaixar ou posicionar absolutamente <xref:System.Windows.Forms.ToolStrip> controles. <xref:System.Windows.Forms.ToolStrip>os itens são apresentados <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> do contêiner.  
  
 O *reposicionamento* é a capacidade das barras de ferramenta de compartilhar espaço horizontal ou vertical. Um formulário do Windows pode ter um <xref:System.Windows.Forms.ToolStripContainer> que por sua vez tem painéis do formulário esquerda, direita, superior e lados da parte inferior para posicionamento e rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles. Vários <xref:System.Windows.Forms.ToolStrip> controles de pilha verticalmente se colocá-los na esquerda ou direita <xref:System.Windows.Forms.ToolStripContainer>. Horizontalmente pilha se colocá-los na parte superior ou inferior <xref:System.Windows.Forms.ToolStripContainer>. Você pode usar o centro <xref:System.Windows.Forms.ToolStripContentPanel> do <xref:System.Windows.Forms.ToolStripContainer> para posicionar tradicionais controles no formulário.  
  
 Todos os <xref:System.Windows.Forms.ToolStripContainer> controles são selecionáveis diretamente em tempo de design e pode ser excluídos. Um <xref:System.Windows.Forms.ToolStripContainer> é expansíveis e recolhíveis e redimensiona com os controles que ele contém.  
  
 O *encaixe* é a especificação de local de um controle simples na esquerda, direita, acima ou abaixo do formulário.  
  
 A vantagem de rafting sobre encaixe é que <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> controles podem compartilhar o espaço horizontal ou vertical com outros controles.  
  
 A maioria do <xref:System.Windows.Forms.ToolStrip> controles podem ser encaixados para a forma como outros controles em vez de usar rafting. Você também pode especificar que um <xref:System.Windows.Forms.ToolStrip> controle livremente posicionado no formulário, removendo-o de seu <xref:System.Windows.Forms.ToolStripContainer> e configuração de seu `Dock` propriedade `None`, ou você pode especificar sua posição absoluta, definindo os respectivos <xref:System.Windows.Forms.Control.Location%2A> propriedade. Consulte [Como remover um ToolStrip de um ToolStripContainer para um formulário](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Use um ou mais <xref:System.Windows.Forms.ToolStripPanel> controles mais flexibilidade, especialmente para aplicativos de Interface de documentos múltiplos (MDI), ou se você não precisa de um <xref:System.Windows.Forms.ToolStripContainer>. Um <xref:System.Windows.Forms.ToolStripPanel> fornece um espaço encaixável para localizar e rafting <xref:System.Windows.Forms.ToolStrip> controles mas controles não tradicionais. Por padrão, o <xref:System.Windows.Forms.ToolStripPanel> não aparecem no designer de **caixa de ferramentas**, mas você pode colocá-lo lá clicando com o **caixa de ferramentas**e, em seguida, clique em **escolher itens**. Você também pode acessar programaticamente o <xref:System.Windows.Forms.ToolStripPanel> como qualquer outra classe.  
  
 O <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, e <xref:System.Windows.Forms.StatusStrip> permitem estouro de itens. Isso é semelhante à forma como esses itens se comportam em barras de ferramentas do Microsoft Office.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Arquitetura de controle do ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
