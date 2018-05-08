---
title: 'Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms
Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente. Estas são algumas das tarefas realizadas com frequência que você encontrará:  
  
-   Adição ou remoção de uma guia em um <xref:System.Windows.Forms.TabControl>.  
  
-   Encaixando um controle ao pai.  
  
-   Alterar a orientação de um <xref:System.Windows.Forms.SplitContainer> controle.  
  
 Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design. Essas tarefas são chamadas *verbos de marcas inteligentes*.  
  
 Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criação de um projeto dos Windows Forms  
  
-   Usando smart tags  
  
-   Habilitar e desabilitar smart tags  
  
 Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto de aplicativo do Windows chamado “SmartTagsExample”. Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Selecione o formulário no **Designer de Formulários do Windows**.  
  
## <a name="using-smart-tags"></a>Usando Smart Tags  
 Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.  
  
#### <a name="to-use-smart-tags"></a>Usar smart tags  
  
1.  Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário. Observe o símbolo de marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) que aparece no lado do <xref:System.Windows.Forms.TabControl>.  
  
2.  Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**. Observe que uma página da guia novo é adicionada para o <xref:System.Windows.Forms.TabControl>.  
  
3.  Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.  
  
4.  Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**. Observe que uma nova coluna é adicionada para o <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
5.  Arraste um <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** para seu formulário.  
  
6.  Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**. Observe que o <xref:System.Windows.Forms.SplitContainer> barra de divisão do controle agora está orientado na horizontal.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [Instruções passo a passo: adicionando smart tags a um componente dos Windows Forms](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
