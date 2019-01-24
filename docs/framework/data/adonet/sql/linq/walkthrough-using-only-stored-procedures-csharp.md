---
title: 'Passo a passo: Usando somente procedimentos armazenados (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 5234b4a2743effa4282fb8c211c42511c6432dfa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650819"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Passo a passo: Usando somente procedimentos armazenados (C#)
Este passo a passo fornece um cenário completo do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para acessar dados executando somente procedimentos armazenados. Essa abordagem é frequentemente usada por administradores de banco de dados para limitar como o repositório de dados é acessado.  
  
> [!NOTE]
>  Você também pode usar procedimentos armazenados nos aplicativos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir o comportamento padrão, especialmente para os processos `Create`, `Update` e `Delete`. Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Para fins deste passo a passo, você usará dois métodos que foram mapeados para procedimentos armazenados no banco de dados de exemplo Northwind: CustOrdersDetail e CustOrderHist. O mapeamento ocorre quando você executa a ferramenta de linha de comando SqlMetal para gerar um arquivo C#. Para obter mais informações, consulte a seção Pré-requisitos posteriormente neste passo a passo.  
  
 Este passo a passo não se baseia no [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Os desenvolvedores usando o Visual Studio também podem usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] para implementar a funcionalidade do procedimento armazenado. Ver [ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo requer o seguinte:  
  
-   Este passo a passo usa uma pasta dedicada ("c:\linqtest7") para armazenar arquivos. Crie essa pasta antes de iniciar o passo a passo.  
  
-   O banco de dados de exemplo Northwind.  
  
     Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft. Para obter instruções, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest7.  
  
-   Um arquivo de código C# gerado no banco de dados Northwind.  
  
     Este passo a passo foi escrito usando a ferramenta SqlMetal com a seguinte linha de comando:  
  
     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**  
  
     Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Visão geral  
 Este passo a passo consiste em seis tarefas principais:  
  
-   Configurando o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solução no Visual Studio.  
  
-   Adicionar o assembly System.Data.Linq ao projeto.  
  
-   Adicionar o arquivo do código de banco de dados ao projeto.  
  
-   Criar uma conexão com o banco de dados.  
  
-   Configurar a interface do usuário.  
  
-   Executar e testar o aplicativo.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Criando uma solução LINQ to SQL  
 A primeira tarefa, você cria uma solução do Visual Studio que contém as referências necessárias para compilar e executar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Para criar uma solução LINQ to SQL  
  
1.  No Visual Studio **arquivo** , aponte para **New**e, em seguida, clique em **projeto**.  
  
2.  No **tipos de projeto** painel na **novo projeto** caixa de diálogo, clique em **Visual C#** .  
  
3.  No **modelos** painel, clique em **aplicativo de formulários do Windows**.  
  
4.  No **nome** , digite **SprocOnlyApp**.  
  
5.  No **local** , verifique se onde você deseja armazenar seus arquivos de projeto.  
  
6.  Clique em **OK**.  
  
     O Designer de Formulários do Windows é aberto.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Adicionando a referência do assembly do LINQ to SQL  
 O assembly do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é incluído no modelo padrão do Aplicativo do Windows Forms. Você mesmo precisará adicionar o assembly, conforme explicado nas etapas a seguir:  
  
#### <a name="to-add-systemdatalinqdll"></a>Para adicionar o System.Data.Linq.dll  
  
1.  Na **Gerenciador de soluções**, clique com botão direito **referências**e, em seguida, clique em **Add Reference**.  
  
2.  No **adicionar referência** caixa de diálogo, clique em **.NET**, clique no assembly System e, em seguida, clique em **Okey**.  
  
     O assembly é adicionado ao projeto.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Adicionando o arquivo do código Northwind ao projeto  
 Esta etapa presume que você usou a ferramenta SqlMetal para gerar um arquivo de código do banco de dados de exemplo Northwind. Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Para adicionar o arquivo do código Northwind ao projeto  
  
1.  Sobre o **Project** menu, clique em **Add Existing Item**.  
  
2.  No **Adicionar Item existente** caixa de diálogo, mova para c:\linqtest7\northwind.cs e, em seguida, clique em **Add**.  
  
     O arquivo northwind.cs é adicionado ao projeto.  
  
## <a name="creating-a-database-connection"></a>Criando uma conexão de banco de dados  
 Nesta etapa, você define a conexão com o banco de dados de exemplo Northwind. Este passo a passo usa "c:\linqtest7\northwnd.mdf" como caminho.  
  
#### <a name="to-create-the-database-connection"></a>Par criar a conexão de banco de dados  
  
1.  Na **Gerenciador de soluções**, clique com botão direito **Form1.cs**e, em seguida, clique em **Exibir código**.  
  
2.  Digite o código a seguir na classe `Form1`:  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a>Configurando a interface do usuário  
 Nesta tarefa, você configura uma interface de modo que os usuários possam executar procedimentos armazenados para acessar dados no banco de dados. Nos aplicativos que você está desenvolvendo através deste passo a passo, os usuários só podem acessar dados no banco de dados usando os procedimentos armazenados inseridos no aplicativo.  
  
#### <a name="to-set-up-the-user-interface"></a>Para configurar a interface do usuário  
  
1.  Retorne para o Windows Forms Designer (**Form1.cs[Design]**).  
  
2.  No menu **Exibir**, clique em **Caixa de Ferramentas**.  
  
     A caixa de ferramentas é aberta.  
  
    > [!NOTE]
    >  Clique o **ocultar automaticamente** pino para manter a caixa de ferramentas aberta enquanto você executa o restante das etapas nesta seção.  
  
3.  Arraste dois botões, duas caixas de texto e dois rótulos da toolbox **Form1**.  
  
     Organize os controles conforme mostrado na ilustração de acompanhamento. Expandir **Form1** para que os controles se encaixem facilmente.  
  
4.  Clique com botão direito **label1**e, em seguida, clique em **propriedades**.  
  
5.  Alterar o **texto** propriedade de **label1** para **Enter OrderID:**.  
  
6.  Da mesma forma para **label2**, altere o **texto** propriedade de **label2** para **Enter CustomerID:**.  
  
7.  Da mesma forma, altere o **texto** propriedade **button1** para **detalhes do pedido**.  
  
8.  Alterar o **texto** propriedade **button2** para **histórico de pedidos**.  
  
     Amplie os controles de botão de modo que todo o texto fique visível.  
  
#### <a name="to-handle-button-clicks"></a>Para manipular cliques de botão  
  
1.  Clique duas vezes em **detalhes do pedido** nos **Form1** para abrir o manipulador de eventos de button1 no editor de códigos.  
  
2.  Digite o código a seguir no manipulador `button1`:  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  Agora clique duas vezes **button2** nos **Form1** para abrir o `button2` manipulador  
  
4.  Digite o código a seguir no manipulador `button2`:  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora é hora de testar o aplicativo. Observe que o contato com o repositório de dados limita-se a qualquer ação que os dois procedimentos armazenados podem executar. Essas ações retornarão os produtos para qualquer orderID inserida ou retornarão um histórico do produtos solicitados para qualquer CustomerID inserida.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Pressione F5 para iniciar a depuração.  
  
     Form1 aparecerá.  
  
2.  No **Enter OrderID** , digite `10249`e, em seguida, clique em **detalhes do pedido**.  
  
     Uma caixa de mensagem lista os produtos incluídos no pedido 10249.  
  
     Clique em **Okey** para fechar a caixa de mensagem.  
  
3.  No **Enter CustomerID** , digite `ALFKI`e, em seguida, clique em **histórico de pedidos**.  
  
     Uma caixa de mensagem aparecerá, listando o histórico do pedido do cliente ALFKI.  
  
     Clique em **Okey** para fechar a caixa de mensagem.  
  
4.  No **Enter OrderID** , digite `123`e, em seguida, clique em **detalhes do pedido**.  
  
     Uma caixa de mensagem exibirá "Nenhum resultado".  
  
     Clique em **Okey** para fechar a caixa de mensagem.  
  
5.  Sobre o **Debug** menu, clique em **parar a depuração**.  
  
     A sessão de depuração é fechada.  
  
6.  Se você tiver terminado o teste, você pode clicar em **fechar projeto** sobre o **arquivo** menu e salvar o projeto quando solicitado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprimorar esse projeto fazendo algumas alterações. Por exemplo, você pode listar os procedimentos armazenados disponíveis em uma caixa de listagem e fazer com que o usuário selecione os procedimentos que serão executados. Você também pode transmitir a saída dos relatórios para um arquivo de texto.  
  
## <a name="see-also"></a>Consulte também
- [Aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
