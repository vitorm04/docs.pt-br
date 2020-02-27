---
title: Executar tarefas comuns usando ações de designer em controles
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634879"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a>Walkthrough: executar tarefas comuns usando ações de designer

À medida que você constrói formulários e controles para seu aplicativo Windows Forms, há muitas tarefas que você executará repetidamente. A lista a seguir mostra algumas das tarefas executadas com frequência que você virá:

- Adicionar ou remover uma guia em um <xref:System.Windows.Forms.TabControl>.
- Encaixando um controle ao pai.
- Alterar a orientação de um controle de <xref:System.Windows.Forms.SplitContainer>.

Para agilizar o desenvolvimento, muitos controles oferecem ações de designer, que são menus sensíveis ao contexto que permitem executar tarefas comuns como essas em um único gesto no tempo de design. Essas tarefas são chamadas de *verbos de ações do designer*.

As ações do designer permanecem anexadas a uma instância de controle durante seu tempo de vida no designer e estão sempre disponíveis.

## <a name="create-the-project"></a>Criar o projeto

A primeira etapa é criar o projeto e configurar o formulário.

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado **DesignerActionsExample**.

2. Selecione o formulário no **Designer de Formulários do Windows**.

## <a name="use-designer-actions"></a>Usar ações do designer

As ações do designer estão sempre disponíveis em tempo de design em controles que as oferecem.

1. Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário. Observe o glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) que aparece no lado do <xref:System.Windows.Forms.TabControl>.

2. Clique no glifo ações do designer. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**. Observe que uma nova página da guia é adicionada à <xref:System.Windows.Forms.TabControl>.

3. Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.

4. Clique no glifo ações do designer. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**. Observe que uma nova coluna é adicionada ao controle de <xref:System.Windows.Forms.TableLayoutPanel>.

5. Arraste um controle de <xref:System.Windows.Forms.SplitContainer> da **caixa de ferramentas** para seu formulário.

6. Clique no glifo ações do designer. No menu de atalho que aparece ao lado do glifo, selecione o item de **orientação de divisor horizontal** . Observe que a barra de divisão do controle de <xref:System.Windows.Forms.SplitContainer> agora é orientada horizontalmente.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
