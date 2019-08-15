---
title: 'Como: Associar controles do Windows Forms ao componente BindingSource usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040027"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Como: Associar controles do Windows Forms ao componente BindingSource usando o designer
Depois de adicionar controles ao formulário e determinar a interface do usuário para seu aplicativo, você pode associar os controles a uma fonte de dados, para que os usuários possam alterar e salvar dados relacionados ao aplicativo no tempo de execução.

 Associar um controle ou uma série de controles em Windows Forms é facilmente feito usando o <xref:System.Windows.Forms.BindingSource> controle como uma ponte entre os controles no formulário e a fonte de dados.

 Um ou mais controles em um formulário podem ser associados a dados; no procedimento a seguir, um <xref:System.Windows.Forms.TextBox> controle está associado a uma fonte de dados.

 Para concluir o procedimento, presume-se que você associará a uma fonte de dados derivada de um banco de dados. Para obter mais informações sobre como criar fontes de dados de outros armazenamentos de dados, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).

## <a name="to-bind-a-control-at-design-time"></a>Associar um controle no tempo de design

1. Arraste um <xref:System.Windows.Forms.TextBox> controle para o formulário.

2. Na janela **Propriedades**:

    1. Expanda o nó **(DataBindings)** .

    2. Clique na seta ao lado da <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.

         O editor de tipo de interface do usuário **DataSource** abre.

         Se uma fonte de dados tiver sido configurada anteriormente para o projeto ou formulário, ela será exibida.

3. Clique em **Adicionar fonte de dados do projeto** para conectar aos dados e criar uma fonte de dados.

4. Na página de boas-vindas do **Assistente de Configuração de Fonte de Dados**, clique em **Avançar**.

5. Na página **Escolher um tipo de fonte de dados**, selecione **Banco de dados**.

6. Na página **Escolha sua conexão de dados**, selecione uma conexão de dados da lista de conexões disponíveis. Se a conexão de dados desejada não estiver disponível, selecione **Nova Conexão** para criar uma nova conexão de dados.

7. Selecione **Sim, salvar a conexão** para salvar a cadeia de conexão no arquivo de configuração de aplicativo.

8. Selecione os objetos de banco de dados para trazer para o seu aplicativo. Nesse caso, selecione um campo em uma tabela que você deseja que o <xref:System.Windows.Forms.TextBox> exiba.

9. Substitua o nome do conjunto de dados padrão, se quiser.

10. Clique em **Finalizar**.

11. Na janela **Propriedades** , clique na seta ao lado da <xref:System.Windows.Forms.TextBox.Text%2A> Propriedade novamente. No editor de tipo de interface do usuário do **DataSource** , selecione o nome do campo <xref:System.Windows.Forms.TextBox> ao qual associar o.

     O editor de tipo de interface do usuário da **fonte** de <xref:System.Windows.Forms.BindingSource> dados é fechado e o conjunto e o adaptador de tabela específico para essa conexão de dados são adicionados ao formulário.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources)
- [Janela Fontes de Dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
