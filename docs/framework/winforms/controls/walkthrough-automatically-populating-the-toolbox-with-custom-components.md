---
title: 'Passo a passo: Preencher de forma automática a caixa de ferramentas com componentes personalizados'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211156"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Passo a passo: Preencher de forma automática a caixa de ferramentas com componentes personalizados

Se seus componentes forem definidos por um projeto na solução aberta no momento, eles aparecerão automaticamente na **Caixa de Ferramentas** sem exigir que você execute nenhuma ação. Você também pode preencher manualmente a **Caixa de Ferramentas** com seus componentes personalizados usando a [Caixa de Diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), mas a **Caixa de Ferramentas** leva em conta itens nas saídas de build da sua solução com todas as seguintes características:

- Implementa <xref:System.ComponentModel.IComponent>;

- Não tem <xref:System.ComponentModel.ToolboxItemAttribute> definido como `false`;

- Não tem <xref:System.ComponentModel.DesignTimeVisibleAttribute> definido como `false`.

> [!NOTE]
> O **caixa de ferramentas** não segue cadeias de referência, portanto, ele não exibirá itens que não são criados por um projeto em sua solução.

Este passo a passo demonstra como um componente personalizado aparece automaticamente na **Caixa de Ferramentas** depois que o componente é criado. As tarefas ilustradas neste passo a passo incluem:

- Criando um projeto dos Windows Forms.

- Criando um componente personalizado.

- Criando uma instância de um componente personalizado.

- Descarregando e recarregando um componente personalizado.

Quando tiver terminado, verá que a **Caixa de Ferramentas** é preenchida com um componente que você criou.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado `ToolboxExample` (**arquivo** > **New** > **projeto**  >  **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > **Windows Forms Aplicativo**).

2. Adicione um novo componente ao projeto. Chame `DemoComponent`.

     Para obter mais informações, confira [Como: Adicionar novos itens de projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).

3. Compile o projeto.

4. No menu **Ferramentas**, clique no item **Opções**. Clique em **Geral** no item **Designer de Formulários do Windows** e certifique-se de que a opção **AutoToolboxPopulate** esteja definida como **True**.

## <a name="create-an-instance-of-a-custom-component"></a>Criar uma instância de um componente personalizado

A próxima etapa é criar uma instância do componente personalizado no formulário. Uma vez que a **Caixa de Ferramentas** automaticamente conta para o novo componente, isso é tão fácil quanto criar qualquer outro componente ou controle.

1. Abra o formulário do projeto no **Designer de Formulários**.

2. Na **Caixa de Ferramentas**, clique na nova guia chamada **Componentes de ToolboxExample**.

     Ao clicar na guia, você verá **DemoComponent**.

    > [!NOTE]
    > Por motivos de desempenho de componentes na área preenchida automaticamente dos **caixa de ferramentas** não exibem bitmaps personalizados e o <xref:System.Drawing.ToolboxBitmapAttribute> não tem suporte. Para exibir um ícone para um componente personalizado na **Caixa de Ferramentas**, use a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** para carregar seu componente.

3. Arraste o componente para seu formulário.

     Uma instância do componente é criada e adicionada à **Bandeja de Componentes**.

## <a name="unload-and-reload-a-custom-component"></a>Descarregar e recarregar um componente personalizado

A **Caixa de Ferramentas** considera os componentes em cada projeto carregado e, quando um projeto é descarregado, ela remove referências aos componentes do projeto.

1. Descarregue o projeto da solução.

     Para obter mais informações sobre descarregar projetos, consulte [como: Descarregar e recarregar projetos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)). Se você for solicitado a salvar, escolha **Sim**.

2. Adicione um novo projeto de **Aplicativos do Windows** à solução. Abra o formulário no **Designer**.

     A guia **Componentes de ToolboxExample** do projeto anterior agora está ausente.

3. Recarregue o projeto `ToolboxExample`.

     A guia **Componentes de ToolboxExample** agora será exibida novamente.

## <a name="next-steps"></a>Próximas etapas

Este passo a passo demonstra que a **Caixa de Ferramentas** leva em conta componentes do projeto, mas a **Caixa de Ferramentas** também leva em os controles. Experimente seus próprios controles personalizados adicionando e removendo projetos de controle de sua solução.

## <a name="see-also"></a>Consulte também

- [Geral, Designer de formulários do Windows, caixa de diálogo Opções](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [Como: Manipular guias da caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Colocando controles nos Windows Forms](putting-controls-on-windows-forms.md)
