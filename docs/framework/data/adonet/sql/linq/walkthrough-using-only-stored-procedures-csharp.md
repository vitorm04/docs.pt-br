---
title: 'Passo a passo: Usando somente procedimentos armazenados (C#)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: befc1cbafa7e2ab0a6f6ceeddf1170090f13f92d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>Passo a passo: Usando somente procedimentos armazenados (C#)
Este passo a passo fornece um cenário completo do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para acessar dados executando somente procedimentos armazenados. Essa abordagem é frequentemente usada por administradores de banco de dados para limitar como o repositório de dados é acessado.  
  
> [!NOTE]
>  Você também pode usar procedimentos armazenados nos aplicativos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir o comportamento padrão, especialmente para os processos `Create`, `Update` e `Delete`. Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Neste passo a passo, você usará dois métodos que foram mapeados para os procedimentos armazenados no banco de dados de exemplo Northwind: CustOrdersDetail e CustOrderHist. O mapeamento ocorre quando você executa a ferramenta de linha de comando SqlMetal para gerar um arquivo C#. Para obter mais informações, consulte a seção Pré-requisitos posteriormente neste passo a passo.  
  
 Este passo a passo não se baseia no [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Os desenvolvedores que usam o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] também podem usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] para implementar a funcionalidade do procedimento armazenado. Consulte [LINQ to SQL Tools no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo requer o seguinte:  
  
-   Este passo a passo usa uma pasta dedicada ("c:\linqtest7") para armazenar arquivos. Crie essa pasta antes de iniciar o passo a passo.  
  
-   O banco de dados de exemplo Northwind.  
  
     Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft. Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest7.  
  
-   Um arquivo de código C# gerado no banco de dados Northwind.  
  
     Este passo a passo foi escrito usando a ferramenta SqlMetal com a seguinte linha de comando:  
  
     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**  
  
     Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Visão geral  
 Este passo a passo consiste em seis tarefas principais:  
  
-   Configurar a solução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Adicionar o assembly System.Data.Linq ao projeto.  
  
-   Adicionar o arquivo do código de banco de dados ao projeto.  
  
-   Criar uma conexão com o banco de dados.  
  
-   Configurar a interface do usuário.  
  
-   Executar e testar o aplicativo.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Criando uma solução LINQ to SQL  
 Nesta primeira tarefa, você cria uma solução do [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] que contém as referências necessárias para criar e executar um projeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Para criar uma solução LINQ to SQL  
  
1.  Sobre o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.  
  
2.  No **tipos de projeto** painel o **novo projeto** caixa de diálogo, clique em **Visual C#**.  
  
3.  No **modelos** painel, clique em **aplicativo do Windows Forms**.  
  
4.  No **nome** , digite **SprocOnlyApp**.  
  
5.  No **local** , verifique se onde você deseja armazenar os arquivos de projeto.  
  
6.  Clique em **OK**.  
  
     O Designer de Formulários do Windows é aberto.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>Adicionando a referência do assembly do LINQ to SQL  
 O assembly do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é incluído no modelo padrão do Aplicativo do Windows Forms. Você mesmo precisará adicionar o assembly, conforme explicado nas etapas a seguir:  
  
#### <a name="to-add-systemdatalinqdll"></a>Para adicionar o System.Data.Linq.dll  
  
1.  Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.  
  
     O assembly é adicionado ao projeto.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Adicionando o arquivo do código Northwind ao projeto  
 Esta etapa presume que você usou a ferramenta SqlMetal para gerar um arquivo de código do banco de dados de exemplo Northwind. Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Para adicionar o arquivo do código Northwind ao projeto  
  
1.  Sobre o **projeto** menu, clique em **Add Existing Item**.  
  
2.  No **Add Existing Item** caixa de diálogo, mova para c:\linqtest7\northwind.cs e, em seguida, clique em **adicionar**.  
  
     O arquivo northwind.cs é adicionado ao projeto.  
  
## <a name="creating-a-database-connection"></a>Criando uma conexão de banco de dados  
 Nesta etapa, você define a conexão com o banco de dados de exemplo Northwind. Este passo a passo usa "c:\linqtest7\northwnd.mdf" como caminho.  
  
#### <a name="to-create-the-database-connection"></a>Par criar a conexão de banco de dados  
  
1.  Em **Solution Explorer**, clique com botão direito **Form1.cs**e, em seguida, clique em **Exibir código**.  
  
2.  Digite o código a seguir na classe `Form1`:  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a>Configurando a interface do usuário  
 Nesta tarefa, você configura uma interface de modo que os usuários possam executar procedimentos armazenados para acessar dados no banco de dados. Nos aplicativos que você está desenvolvendo através deste passo a passo, os usuários só podem acessar dados no banco de dados usando os procedimentos armazenados inseridos no aplicativo.  
  
#### <a name="to-set-up-the-user-interface"></a>Para configurar a interface do usuário  
  
1.  Voltar para o Windows Forms Designer (**Form1.cs[Design]**).  
  
2.  Sobre o **exibição** menu, clique em **caixa de ferramentas**.  
  
     A caixa de ferramentas é aberta.  
  
    > [!NOTE]
    >  Clique o **AutoOcultar** pino para manter a caixa de ferramentas aberta enquanto você executa o restante das etapas nesta seção.  
  
3.  Arraste dois rótulos, duas caixas de texto e dois botões da caixa de ferramentas para **Form1**.  
  
     Organize os controles conforme mostrado na ilustração de acompanhamento. Expanda **Form1** para que os controles se ajustar facilmente.  
  
4.  Clique com botão direito **label1**e, em seguida, clique em **propriedades**.  
  
5.  Alterar o **texto** propriedade **label1** para **insira OrderID:**.  
  
6.  Da mesma forma para **label2**, alterar o **texto** propriedade **label2** para **digite CustomerID:**.  
  
7.  Da mesma forma, alterar o **texto** propriedade **button1** para **detalhes do pedido**.  
  
8.  Alterar o **texto** propriedade **button2** para **histórico de pedidos**.  
  
     Amplie os controles de botão de modo que todo o texto fique visível.  
  
#### <a name="to-handle-button-clicks"></a>Para manipular cliques de botão  
  
1.  Clique duas vezes em **Order Details** na **Form1** para abrir o manipulador de eventos button1 no editor de códigos.  
  
2.  Digite o código a seguir no manipulador `button1`:  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  Agora clique duas vezes em **button2** na **Form1** para abrir o `button2` manipulador  
  
4.  Digite o código a seguir no manipulador `button2`:  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora é hora de testar o aplicativo. Observe que o contato com o repositório de dados limita-se a qualquer ação que os dois procedimentos armazenados podem executar. Essas ações retornarão os produtos para qualquer orderID inserida ou retornarão um histórico do produtos solicitados para qualquer CustomerID inserida.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Pressione F5 para iniciar a depuração.  
  
     Form1 aparecerá.  
  
2.  No **OrderID insira** , digite `10249`e, em seguida, clique em **detalhes do pedido**.  
  
     Uma caixa de mensagem lista os produtos incluídos no pedido 10249.  
  
     Clique em **Okey** para fechar a caixa de mensagem.  
  
3.  No **digite CustomerID** , digite `ALFKI`e, em seguida, clique em **histórico de pedidos**.  
  
     Uma caixa de mensagem aparecerá, listando o histórico do pedido do cliente ALFKI.  
  
     Clique em **Okey** para fechar a caixa de mensagem.  
  
4.  No **OrderID insira** , digite `123`e, em seguida, clique em **detalhes do pedido**.  
  
     Uma caixa de mensagem exibirá "Nenhum resultado".  
  
     Clique em **Okey** para fechar a caixa de mensagem.  
  
5.  Sobre o **depurar** menu, clique em **parar a depuração**.  
  
     A sessão de depuração é fechada.  
  
6.  Se você concluiu a experimentar, você pode clicar em **fechar projeto** no **arquivo** menu e salve o projeto quando você for solicitado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprimorar esse projeto fazendo algumas alterações. Por exemplo, você pode listar os procedimentos armazenados disponíveis em uma caixa de listagem e fazer com que o usuário selecione os procedimentos que serão executados. Você também pode transmitir a saída dos relatórios para um arquivo de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
