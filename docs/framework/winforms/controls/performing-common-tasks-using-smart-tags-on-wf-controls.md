---
title: 'Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459579"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Walkthrough: executar tarefas comuns usando marcas inteligentes

Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente. Estas são algumas das tarefas realizadas com frequência que você encontrará:

- Adicionar ou remover uma guia em um <xref:System.Windows.Forms.TabControl>.

- Encaixando um controle ao pai.

- Alterar a orientação de um controle de <xref:System.Windows.Forms.SplitContainer>.

Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design. Essas tarefas são chamadas *verbos de marcas inteligentes*.

Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.

## <a name="create-the-project"></a>Criar o projeto

A primeira etapa é criar o projeto e configurar o formulário.

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado **SmartTagsExample**.

2. Selecione o formulário no **Designer de Formulários do Windows**.

## <a name="use-smart-tags"></a>Usar marcas inteligentes

Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.

1. Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário. Observe o glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif)) que aparece no lado do <xref:System.Windows.Forms.TabControl>.

2. Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**. Observe que uma nova página da guia é adicionada à <xref:System.Windows.Forms.TabControl>.

3. Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.

4. Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**. Observe que uma nova coluna é adicionada ao controle de <xref:System.Windows.Forms.TableLayoutPanel>.

5. Arraste um controle de <xref:System.Windows.Forms.SplitContainer> da **caixa de ferramentas** para seu formulário.

6. Clique no glifo de marca inteligente. No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**. Observe que a barra de divisão do controle de <xref:System.Windows.Forms.SplitContainer> agora é orientada horizontalmente.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
