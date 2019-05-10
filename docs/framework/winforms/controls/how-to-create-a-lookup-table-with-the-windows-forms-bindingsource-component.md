---
title: 'Como: Criar uma tabela de pesquisa com o componente BindingSource do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 33b9e4e98a8a3f8c0d5dd6433ebbf15c049b608e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643068"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Como: Criar uma tabela de pesquisa com o componente BindingSource do Windows Forms
A tabela de pesquisa é uma tabela de dados que tem uma coluna que exibe dados de registros em uma tabela relacionada. Nos procedimentos a seguir, um controle <xref:System.Windows.Forms.ComboBox> é usado para exibir o campo com a relação de chave estrangeira da tabela pai para a tabela filho.  
  
 Para ajudar a visualizar essas duas tabelas e essa relação, veja a seguir um exemplo de uma tabela pai e filho:  
  
 CustomersTable (tabela pai)  
  
|CustomerID|CustomerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (tabela filho)  
  
|OrderID|OrderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|12.02.04|712|  
|904|13.02.04|713|  
  
 Neste cenário, uma tabela, CustomersTable, armazena a informação real que você deseja exibir e salvar. Mas, para economizar espaço, a tabela deixa de fora dados que adicionam clareza. A outra tabela, OrdersTable, contém apenas informações relacionadas à aparência sobre qual número da ID do cliente é equivalente a qual data de pedido e ID do pedido. Não há nenhuma menção dos nomes dos clientes.  
  
 Quatro propriedades importantes são definidas no [Controle ComboBox](combobox-control-windows-forms.md) para criar a tabela de pesquisa.  
  
- A propriedade <xref:System.Windows.Forms.ComboBox.DataSource%2A> contém o nome da tabela.  
  
- A propriedade <xref:System.Windows.Forms.ListControl.DisplayMember%2A> contém a coluna de dados da tabela que você deseja exibir para o texto de controle (nome do cliente).  
  
- A propriedade <xref:System.Windows.Forms.ListControl.ValueMember%2A> contém a coluna de dados dessa tabela com as informações armazenadas (o número de ID na tabela pai).  
  
- A propriedade <xref:System.Windows.Forms.ListControl.SelectedValue%2A> fornece o valor de pesquisa da tabela filho, com base no <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Os procedimentos a seguir mostram como dispor um formulário como uma tabela de pesquisa e vincular dados aos controles nele. Para concluir com êxito os procedimentos, você deve ter uma fonte de dados com as tabelas pai e filho que tenham uma relação de chave estrangeira, como mencionado anteriormente.  
  
### <a name="to-create-the-user-interface"></a>Para criar a interface do usuário  
  
1. Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ComboBox> controle para o formulário.  
  
     Esse controle exibirá a coluna da tabela pai.  
  
2. Arraste outros controles para exibir detalhes da tabela filho. O formato dos dados na tabela deve determinar quais controles você escolhe. Para obter mais informações, consulte [Controles dos Windows Forms por função](windows-forms-controls-by-function.md).  
  
3. Arraste um controle <xref:System.Windows.Forms.BindingNavigator> para o formulário; isso permitirá que você navegue os dados na tabela filho.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Para conectar-se aos dados e vinculá-lo aos controles  
  
1. Selecione o <xref:System.Windows.Forms.ComboBox> e clique no glifo da Tarefa Inteligente para exibir a caixa de diálogo Tarefa Inteligente.  
  
2. Selecione **Usar itens vinculados aos dados**.  
  
3. Clique na seta ao lado da caixa suspensa **Fonte de Dados**. Se uma fonte de dados foi configurada anteriormente para o projeto ou formulário, ela aparecerá; caso contrário, siga as seguintes etapas (Este exemplo usa as tabelas Clientes e Pedidos do banco de dados de amostra Northwind e refere-se a elas nos parênteses).  
  
    1. Clique em **Adicionar Fonte de Dados do Projeto** para conectar-se aos dados e criar uma fonte de dados.  
  
    2. Na página de boas-vindas do **Assistente de Configuração de Fonte de Dados**, clique em **Avançar**.  
  
    3. Selecione **Banco de dados** na página **Escolher um tipo de fonte de dados**.  
  
    4. Escolha uma conexão de dados na lista de conexões disponíveis na página **Escolha a conexão de dados**. Se sua conexão de dados desejada não estiver disponível, selecione **Nova Conexão** para criar uma nova conexão de dados.  
  
    5. Clique em **Sim, salvar a conexão** para salvar a cadeia de conexão no arquivo de configuração de aplicativo.  
  
    6. Selecione os objetos de banco de dados para trazer para o seu aplicativo. Neste caso, selecione uma tabela pai e uma tabela filho (por exemplo, clientes e pedidos) com uma relação de chave estrangeira.  
  
    7. Substitua o nome do conjunto de dados padrão, se quiser.  
  
    8. Clique em **Finalizar**.  
  
4. Na caixa suspensa **Exibir Membro**, selecione o nome da coluna (por exemplo, ContactName) a ser exibida na caixa de combinação.  
  
5. Na caixa suspensa **Membro do Valor**, selecione a coluna (por exemplo, CustomerID) para executar a operação de pesquisa na tabela filho.  
  
6. Na caixa suspensa **Valor Selecionado**, navegue até **Fontes de Dados do Projeto** e o conjunto de dados que você criou que contém as tabelas pai e filho. Selecione a mesma propriedade da tabela filho que é o Membro do Valor da tabela pai (por exemplo, Orders.CustomerID). Os <xref:System.Windows.Forms.BindingSource>, componentes do conjunto de dados e do adaptador de tabela adequado, serão criados e adicionados ao formulário.  
  
7. Vincule o controle <xref:System.Windows.Forms.BindingNavigator> para o <xref:System.Windows.Forms.BindingSource> da tabela filho (por exemplo, `OrdersBindingSource`).  
  
8. Vincule os controles diferentes dos controles <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.BindingNavigator> aos campos de detalhes do <xref:System.Windows.Forms.BindingSource> da tabela filho (Por exemplo, `OrdersBindingSource`) que você deseja exibir.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
- [Controle ComboBox](combobox-control-windows-forms.md)
- [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
