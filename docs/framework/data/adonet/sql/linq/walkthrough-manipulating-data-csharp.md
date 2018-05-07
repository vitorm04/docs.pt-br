---
title: 'Passo a passo: manipulando dados (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: b9b19d4f9a1fb56ddabbf3584c1fb7bb29cd6d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-manipulating-data-c"></a>Passo a passo: manipulando dados (C#)
Essa explicação passo a passo fornece um cenário completo fundamental do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para adicionar, modificar e excluir dados em um banco de dados. Você usará uma cópia do banco de dados de exemplo Northwind para adicionar um cliente, alterar o nome de um cliente e excluir um pedido.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo requer o seguinte:  
  
-   Este passo a passo usa uma pasta dedicada ("c:\linqtest6") para armazenar arquivos. Crie essa pasta antes de iniciar o passo a passo.  
  
-   O banco de dados de exemplo Northwind.  
  
     Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft. Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest6.  
  
-   Um arquivo de código C# gerado no banco de dados Northwind.  
  
     Você pode gerar esse arquivo usando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou a ferramenta SQLMetal. Este passo a passo foi escrito usando a ferramenta SQLMetal com a seguinte linha de comando:  
  
     **sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**  
  
     Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Visão geral  
 Este passo a passo consiste em seis tarefas principais:  
  
-   Criando o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solução no Visual Studio.  
  
-   Adicionar o arquivo do código de banco de dados ao projeto.  
  
-   Criar um novo objeto do cliente.  
  
-   Alterar o nome de contato de um cliente.  
  
-   Excluir um pedido.  
  
-   Enviar essas alterações para o banco de dados Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Criando uma solução LINQ to SQL  
 Na primeira tarefa, você cria uma solução do Visual Studio que contém as referências necessárias para compilar e executar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Para criar uma solução LINQ to SQL  
  
1.  No Visual Studio **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.  
  
2.  No **tipos de projeto** painel o **novo projeto** caixa de diálogo, clique em **Visual C#**.  
  
3.  No painel **Modelos**, clique em **Aplicativo de Console**.  
  
4.  No **nome** , digite **LinqDataManipulationApp**.  
  
5.  No **local** , verifique se onde você deseja armazenar os arquivos de projeto.  
  
6.  Clique em **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Adicionando referências e diretivas LINQ  
 Este passo a passo usa assemblies que não podem ser instalados por padrão em seu projeto. Se System.Data.Linq não estiver listado como uma referência em seu projeto, adicione-o, conforme explicado nas seguintes etapas:  
  
#### <a name="to-add-systemdatalinq"></a>Para adicionar System.Data.Linq  
  
1.  Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.  
  
     O assembly é adicionado ao projeto.  
  
3.  Adicione as seguintes diretivas na parte superior de Program.cs:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Adicionando o arquivo do código Northwind ao projeto  
 Estas etapas presumem que você tenha usado a ferramenta SQLMetal para gerar um arquivo de código do banco de dados de exemplo Northwind. Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Para adicionar o arquivo do código Northwind ao projeto  
  
1.  Sobre o **projeto** menu, clique em **Add Existing Item**.  
  
2.  No **Add Existing Item** caixa de diálogo, navegue até c:\linqtest6\northwind.cs e, em seguida, clique em **adicionar**.  
  
     O arquivo northwind.cs é adicionado ao projeto.  
  
## <a name="setting-up-the-database-connection"></a>Configurando a conexão de banco de dados  
 Primeiro, teste sua conexão com o banco de dados. Observe especialmente se o banco de dados, Northwnd, não tem nenhum caractere i. Se você gerar erros nas próximas etapas, revise o arquivo northwind.cs para determinar como a classe parcial do Northwind é soletrada.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Para configurar e testar a conexão com o banco de dados  
  
1.  Digite ou cole o código a seguir no método `Main` na classe Program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  Pressione F5 para testar o aplicativo neste ponto.  
  
     Um **Console** janela será aberta.  
  
     Você pode fechar o aplicativo pressionando Enter no **Console** janela, ou clicando em **parar depuração** no Visual Studio **depurar** menu.  
  
## <a name="creating-a-new-entity"></a>Criando uma nova entidade  
 Criar uma nova entidade é simples. Você pode criar objetos (como `Customer`) usando a palavra-chave `new`.  
  
 Nessa seção e nas seguintes, você está fazendo alterações somente no cache local. Nenhuma alteração será enviada para o banco de dados até que você chame <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no final dessa explicação passo a passo.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Para adicionar um novo objeto de entidade de cliente  
  
1.  Crie um novo `Customer` adicionando o seguinte código antes de `Console.ReadLine();` no método `Main`:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  Pressione F5 para depurar a solução.  
  
3.  Pressione Enter no **Console** janela para parar a depuração e continuar o passo a passo.  
  
## <a name="updating-an-entity"></a>Atualizando uma entidade  
 Nas etapas a seguir, você recuperará um objeto `Customer` e alterará uma de suas propriedades.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Para alterar o nome de um cliente  
  
-   Adicione o seguinte código acima de `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Excluindo uma entidade  
 Usando o mesmo objeto de cliente, você poderá excluir o primeiro pedido.  
  
 O código a seguir demonstra como separar relações entre linhas, e como excluir uma linha do banco de dados. Adicione o seguinte código antes de `Console.ReadLine` para ver como os objetos podem ser excluídos:  
  
#### <a name="to-delete-a-row"></a>Para excluir uma linha  
  
-   Adicione o seguinte código bem acima de `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Enviando alterações para o banco de dados  
 A etapa final necessária para criar, atualizar e excluir objetos é realmente enviar as alterações para o banco de dados. Sem esta etapa, suas alterações serão somente locais e não aparecerão nos resultados da consulta.  
  
#### <a name="to-submit-changes-to-the-database"></a>Para enviar alterações para o banco de dados  
  
1.  Insira o seguinte código bem acima de `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  Insira o código a seguir (após `SubmitChanges`) para mostrar os efeitos de antes e depois de enviar as alterações:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  Pressione F5 para depurar a solução.  
  
4.  Pressione Enter no **Console** janela para fechar o aplicativo.  
  
> [!NOTE]
>  Depois de adicionar o novo cliente enviando as alterações, você não poderá executar esta solução novamente como está. Para executar novamente a solução, altere o nome do cliente e a ID do cliente a ser adicionada.  
  
## <a name="see-also"></a>Consulte também  
 [Aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
