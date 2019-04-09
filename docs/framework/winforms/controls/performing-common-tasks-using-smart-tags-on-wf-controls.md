---
title: 'Passo a passo: Executando tarefas comuns usando marcas inteligentes nos controles do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 3b20e903ce7eef7c69f55328f459d52537a1e85d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132049"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Passo a passo: Executando tarefas comuns usando marcas inteligentes nos controles do Windows Forms
Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente. Estas são algumas das tarefas realizadas com frequência que você encontrará:  
  
-   Adicionando ou removendo uma guia em um <xref:System.Windows.Forms.TabControl>.  
  
-   Encaixando um controle ao pai.  
  
-   Alterando a orientação de um <xref:System.Windows.Forms.SplitContainer> controle.  
  
 Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design. Essas tarefas são chamadas *verbos de marcas inteligentes*.  
  
 Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criação de um projeto dos Windows Forms  
  
-   Usando smart tags  
  
-   Habilitar e desabilitar smart tags  
  
 Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Criar um projeto de aplicativo baseado no Windows chamado "SmartTagsExample" (**arquivo** > **New** > **projeto**  >   **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).  
  
2.  Selecione o formulário no **Designer de Formulários do Windows**.  
  
## <a name="using-smart-tags"></a>Usando Smart Tags  
 Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.  
  
#### <a name="to-use-smart-tags"></a>Usar smart tags  
  
1.  Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário. Observe o glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) que aparece no lado do <xref:System.Windows.Forms.TabControl>.  
  
2.  Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**. Observe que uma nova página de guia é adicionada para o <xref:System.Windows.Forms.TabControl>.  
  
3.  Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
4.  Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**. Observe que uma nova coluna é adicionada para o <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
5.  Arraste uma <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** para seu formulário.  
  
6.  Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**. Observe que o <xref:System.Windows.Forms.SplitContainer> barra divisora do controle é agora orientado horizontalmente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [Passo a passo: Adicionar marcas inteligentes a um componente do Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))
