---
title: Aprendendo com explicações passo a passo
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 1386d0e8fadddab5cd15818cb616bf331262e654
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46518227"
---
# <a name="learning-by-walkthroughs"></a>Aprendendo com explicações passo a passo
O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação fornece várias explicações passo a passo. Este tópico aborda alguns problemas gerais da explicação passo a passo (incluindo solução de problemas) e fornece links para várias explicações passo a passo para iniciantes aprenderem sobre o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  As explicações passo a passo desta seção de Introdução expõem o código básico que dá suporte à tecnologia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Na prática real, você normalmente usará o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] e projetos do Windows Forms para implementar seus aplicativos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. O [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] documentação fornece exemplos e explicações passo a passo para essa finalidade.  
  
## <a name="getting-started-walkthroughs"></a>Tutoriais passo a passo de introdução  
 Várias explicações passo a passo estão disponíveis nesta seção. Essas explicações passo a passo são baseados no banco de dados de exemplo Northwind e apresentam os recursos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em um ritmo tranquilo com complexidades mínimas.  
  
 Uma progressão típica a ser seguida seria:  
  
|Objetivo|Visual Basic|C#|  
|---------------|------------------|---------|  
|Criar uma classe de entidade e executar uma consulta simples.|[Passo a passo: modelo de objeto simples e consulta (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[Passo a passo: modelo de objeto simples e consulta (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|Adicionar uma segunda classe e executar uma consulta mais complexa.<br /><br /> Requer a conclusão do passo a passo anterior.|[Passo a passo: consultando através de relações (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[Passo a passo: consultando através de relações (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|Adicionar, alterar e excluir itens no banco de dados.|[Passo a passo: manipulando dados (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[Passo a passo: manipulando dados (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|Usar procedimentos armazenados.|[Passo a passo: usando somente procedimentos armazenados (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[Passo a passo: usando somente procedimentos armazenados (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Geral  
 Em geral, as seguintes informações aplicam-se a essas explicações passo a passo:  
  
-   Ambiente: Cada [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] passo a passo usa o Visual Studio como ambiente de desenvolvimento integrado (IDE).  
  
-   Mecanismos SQL: essas explicações passo a passo são escritos para serem implementados usando o SQL Server Express. Se você não tiver o SQL Server Express, poderá baixá-lo gratuitamente. Para obter mais informações, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
    > [!NOTE]
    >  As explicações passo a passo do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usam um nome de arquivo como uma cadeia de conexão. Simplesmente especificar um nome de arquivo é uma conveniência que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece para usuários do SQL Server Express. Sempre preste atenção aos problemas de segurança. Para obter mais informações, consulte [segurança em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] instruções passo a passo geralmente exige o banco de dados de exemplo Northwind. Para obter mais informações, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
-   As caixas de diálogo e comandos de menu que você vê no passo a passo podem diferir dos descritos na Ajuda, dependendo de suas configurações ativas ou edição do Visual Studio. Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
-   Para as explicações passo a passo que abordam cenários de várias camadas, um servidor deve estar localizado em um computador que seja diferente do computador de desenvolvimento, e você deve ter as permissões apropriadas para acessar o servidor.  
  
-   O nome da classe que normalmente representa a tabela Orders no banco de dados de exemplo Northwind é `[Order]`. O escape é necessário porque `Order` é uma palavra-chave no Visual Basic.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Erros em tempo de execução podem ocorrer porque você não tem permissões suficientes para acessar os bancos de dados usados nessas explicações passo a passo. Consulte as seguintes etapas para ajudar a resolver os problemas mais comuns.  
  
### <a name="log-on-issues"></a>Problemas de logon  
 Seu aplicativo pode estar tentando acessar o banco de dados por meio de um logon de banco de dados que não é aceito.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Para verificar ou alterar o logon no banco de dados  
  
1.  Sobre o Windows **inicie** , aponte para **todos os programas**, **Microsoft SQL Server 2005**, aponte para **ferramentas de configuração**e, em seguida, clique em **SQL Server Configuration Manager**.  
  
2.  No painel esquerdo do **SQL Server Configuration Manager**, clique em **SQL Server 2005 Services**.  
  
3.  No painel direito, clique com botão direito **SQL Server (SQLEXPRESS)** e, em seguida, clique em **propriedades**.  
  
4.  Clique o **fazer logon** guia e verifique como você está tentando fazer logon servidor.  
  
     Na maioria dos casos, **sistema Local** funciona.  
  
     Se você fizer uma alteração, clique em **reiniciar** para reiniciar o serviço.  
  
### <a name="protocols"></a>Protocolos  
 Às vezes, os protocolos podem não ser definidos corretamente para que seu aplicativo acesse o banco de dados. Por exemplo, o **Pipes nomeados** protocolo, que é necessário para instruções passo a passo no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], não é habilitado por padrão.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Para habilitar o protocolo Pipes Nomeados  
  
1.  No painel esquerdo do **SQL Server Configuration Manager**, expanda **configuração de rede do SQL Server 2005**e, em seguida, clique em **protocolos para SQLEXPRESS**.  
  
2.  No painel direito, verifique se o **Pipes nomeados** protocolo está habilitado. Se não estiver, clique com botão direito **Pipes nomeados** e, em seguida, clique em **habilitar**.  
  
     Você precisará parar e reiniciar o serviço. Siga as etapas no próximo bloco.  
  
### <a name="stopping-and-restarting-the-service"></a>Parando e reiniciando o serviço  
 Você deve parar e reiniciar os serviços para que suas alterações entrem em vigor.  
  
##### <a name="to-stop-and-restart-the-service"></a>Para parar e reiniciar o serviço.  
  
1.  No painel esquerdo do **SQL Server Configuration Manager**, clique em **SQL Server 2005 Services**.  
  
2.  No painel direito, clique com botão direito **SQL Server (SQLEXPRESS)** e, em seguida, clique em **parar**.  
  
3.  Clique com botão direito **SQL Server (SQLEXPRESS)** e, em seguida, clique em **reiniciar**.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
