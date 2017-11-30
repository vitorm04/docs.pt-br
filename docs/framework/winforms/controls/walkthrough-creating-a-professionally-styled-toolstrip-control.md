---
title: "Instruções passo a passo: criando um controle ToolStrip com estilo profissional"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fbc03ad16bcc0d63a75df5478f7da8abbf19193
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>Instruções passo a passo: criando um controle ToolStrip com estilo profissional
Você pode dar a seu aplicativo <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional e o comportamento ao escrever sua própria classe que deriva de <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tipo.  
  
 Este passo a passo demonstra como usar <xref:System.Windows.Forms.ToolStrip> controles para criar um controle composto é semelhante a **painel de navegação** fornecidas pelo Microsoft® Outlook. As seguintes tarefas são ilustradas nesta instrução passo a passo:  
  
-   Criar um projeto da Biblioteca de Controle do Windows.  
  
-   Projetar o controle StackView.  
  
-   Implementar um renderizador personalizado.  
  
 Quando tiver terminado, você terá um controle de cliente personalizado reutilizável com a aparência profissional de um controle do Microsoft Office XP.  
  
 Para copiar o código neste tópico como uma única lista, consulte [Como criar um controle ToolStrip com estilo profissional](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Permissões suficientes para poder criar e executar projetos de Aplicativo dos Windows Forms no computador no qual [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] está instalado.  
  
## <a name="creating-a-windows-control-library-project"></a>Criar um projeto da Biblioteca de Controle do Windows  
 A primeira etapa é criar o projeto de biblioteca de controles.  
  
#### <a name="to-create-the-control-library-project"></a>Para criar o projeto de biblioteca de controles  
  
1.  Crie um novo projeto da Biblioteca de Controle do Windows chamado `StackViewLibrary`.  
  
2.  No **Gerenciador de Soluções**, exclua o controle padrão do projeto excluindo o arquivo de origem denominado "UserControl1.cs" ou "UserControl1.vb", dependendo da linguagem de sua escolha.  
  
     Para obter mais informações, consulte [NIB: como remover, apagar e excluir itens](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Adicionar um novo <xref:System.Windows.Forms.UserControl> item para o **StackViewLibrary** projeto. Dê ao novo arquivo de origem o nome base `StackView`.  
  
## <a name="designing-the-stackview-control"></a>Projetar o controle StackView  
 O `StackView` é um controle composto com um filho <xref:System.Windows.Forms.ToolStrip> controle. Para obter mais informações sobre controles de composição, consulte [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### <a name="to-design-the-stackview-control"></a>Para projetar o controle StackView  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ToolStrip> controle à superfície de design.  
  
2.  No **propriedades** janela, defina o <xref:System.Windows.Forms.ToolStrip> propriedades do controle de acordo com a tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |Nome|`stackStrip`|  
    |CanOverflow|`false`|  
    |Encaixar|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |Fonte|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |Enchimento|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  No Designer de formulários do Windows, clique no <xref:System.Windows.Forms.ToolStrip> do controle **adicionar** botão e adicione um <xref:System.Windows.Forms.ToolStripButton> para o `stackStrip` controle.  
  
4.  No **propriedades** janela, defina o <xref:System.Windows.Forms.ToolStripButton> propriedades do controle de acordo com a tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |Nome|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Margem|`0, 0, 0, 0`|  
    |Enchimento|`3, 3, 3, 3`|  
    |Texto|**Email**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  Repita a etapa 7 para três mais <xref:System.Windows.Forms.ToolStripButton> controles.  
  
     Nomeie os controles como `calendarStackButton`, `contactsStackButton` e `tasksStackButton`. Defina o valor da <xref:System.Windows.Forms.Control.Text%2A> propriedade **calendário**, **contatos**, e **tarefas**, respectivamente.  
  
## <a name="handling-events"></a>Tratando eventos  
 Dois eventos são importantes para fazer com que o controle `StackView` se comporte corretamente. Manipular o <xref:System.Windows.Forms.UserControl.Load> evento para posicionar o controle corretamente. Manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para cada <xref:System.Windows.Forms.ToolStripButton> para dar o `StackView` controlar o comportamento semelhante do estado a <xref:System.Windows.Forms.RadioButton> controle.  
  
#### <a name="to-handle-events"></a>Para manipular eventos  
  
1.  No Designer de Formulários do Windows, selecione o controle `StackView`.  
  
2.  Na janela **Propriedades**, clique em **Eventos**.  
  
3.  Clique duas vezes no evento Carregar para gerar o manipulador de eventos `StackView_Load`.  
  
4.  No manipulador de eventos `StackView_Load`, copie e cole o código a seguir.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  No Designer de Formulários do Windows, selecione o controle `mailStackButton`.  
  
6.  Na janela **Propriedades**, clique em **Eventos**.  
  
7.  Clique duas vezes no evento Clique.  
  
     O Designer de Formulários do Windows gera o manipulador de eventos `mailStackButton_Click`.  
  
8.  Renomeie o manipulador de eventos `mailStackButton_Click` como `stackButton_Click`.  
  
     Para obter mais informações, consulte [Como renomear um identificador (Visual Basic)](http://msdn.microsoft.com/en-us/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Adicione o seguinte código ao manipulador de eventos `stackButton_Click`.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. No Designer de Formulários do Windows, selecione o controle `calendarStackButton`.  
  
11. Na janela **Propriedades**, defina o evento Clique para o manipulador de eventos `stackButton_Click`.  
  
12. Repita as etapas 10 e 11 para os controles `contactsStackButton` e `tasksStackButton`.  
  
## <a name="defining-icons"></a>Definindo ícones  
 Cada botão `StackView` tem um ícone associado. Para sua conveniência, cada ícone é representado como uma cadeia de caracteres codificada em Base64, que é desserializado antes de um <xref:System.Drawing.Bitmap> é criado a partir dele. Em um ambiente de produção, armazene dados de bitmap como um recurso e seus ícones serão exibidos no Designer de Formulários do Windows. Para obter mais informações, consulte [Como adicionar imagens de tela de fundo ao Windows Forms](http://msdn.microsoft.com/en-us/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### <a name="to-define-icons"></a>Para definir ícones  
  
1.  No Editor de Códigos, insira o seguinte código na definição de classe `StackView`. Esse código inicializa os bitmaps para o <xref:System.Windows.Forms.ToolStripButton> ícones.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Adicione uma chamada ao método `InitializeImages` no construtor de classe `StackView`.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>Implementar um renderizador personalizado  
 Você pode personalizar a maioria dos elementos do `StackView` controle meu implementando uma classe que deriva de <xref:System.Windows.Forms.ToolStripRenderer> classe. Neste procedimento, você irá implementar um <xref:System.Windows.Forms.ToolStripProfessionalRenderer> classe que personaliza a alça e desenha gradientes planos de fundo para o <xref:System.Windows.Forms.ToolStripButton> controles.  
  
#### <a name="to-implement-a-custom-renderer"></a>Para implementar um renderizador personalizado  
  
1.  Insira o seguinte código na definição de controle `StackView`.  
  
     Esta é a definição para o `StackRenderer` de classe que substitui o <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, e <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> métodos para produzir uma aparência personalizada.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  No `StackView` construtor do controle, crie uma nova instância do `StackRenderer` classe e atribuir essa instância para o `stackStrip` do controle <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriedade.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>Testando o controle StackView  
 O `StackView` controle deriva o <xref:System.Windows.Forms.UserControl> classe. Portanto, você pode testar o controle com o **Contêiner de teste do UserControl**. Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).  
  
#### <a name="to-test-the-stackview-control"></a>Para testar o controle StackView  
  
1.  Pressione F5 para compilar o projeto e iniciar o **Contêiner de teste do UserControl**.  
  
2.  Mova o ponteiro sobre os botões do controle `StackView` e, em seguida, clique em um botão para ver a aparência de seu estado selecionado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Neste passo a passo, você criou controle de cliente personalizado reutilizável com a aparência profissional de um controle do Office XP. Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:  
  
-   Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>. Para obter mais informações, consulte [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Criar um formulário com um menu padrão preenchido automaticamente. Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Criar um formulário de interface MDI vários documentos com encaixe <xref:System.Windows.Forms.ToolStrip> controles. Para obter mais informações, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Como fornecer itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
