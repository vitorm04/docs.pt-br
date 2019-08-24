---
title: 'Passo a passo: Executando tarefas comuns usando marcas inteligentes nos controles do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015757"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Passo a passo: Executar tarefas comuns usando marcas inteligentes

Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente. Estas são algumas das tarefas realizadas com frequência que você encontrará:

- Adicionando ou removendo uma guia em <xref:System.Windows.Forms.TabControl>um.

- Encaixando um controle ao pai.

- Alterando a orientação de <xref:System.Windows.Forms.SplitContainer> um controle.

Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design. Essas tarefas são chamadas *verbos de marcas inteligentes*.

Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.

## <a name="create-the-project"></a>Criar o projeto

A primeira etapa é criar o projeto e configurar o formulário.

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado **SmartTagsExample**.

2. Selecione o formulário no **Designer de Formulários do Windows**.

## <a name="use-smart-tags"></a>Usar marcas inteligentes

Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.

1. Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário. Observe o glifo de marca inteligente (![glifo](./media/vs-winformsmttagglyph.gif)de marca inteligente) que aparece <xref:System.Windows.Forms.TabControl>no lado do.

2. Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**. Observe que uma nova página da guia é adicionada ao <xref:System.Windows.Forms.TabControl>.

3. Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.

4. Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**. Observe que uma nova coluna é adicionada ao <xref:System.Windows.Forms.TableLayoutPanel> controle.

5. Arraste um <xref:System.Windows.Forms.SplitContainer> controle da **caixa de ferramentas** para seu formulário.

6. Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**. Observe que a <xref:System.Windows.Forms.SplitContainer> barra de divisão do controle agora é orientada horizontalmente.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
