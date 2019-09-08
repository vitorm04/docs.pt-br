---
title: Aprendendo com explicações passo a passo
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: 4beb9944a13fd2f76d7305b4d84230fcc33483be
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781320"
---
# <a name="learning-by-walkthroughs"></a>Aprendendo com explicações passo a passo
A [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação fornece vários passo a passos. Este tópico aborda alguns problemas gerais da explicação passo a passo (incluindo solução de problemas) e fornece links para várias explicações passo a passo para iniciantes aprenderem sobre o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
> As explicações passo a passo desta seção de Introdução expõem o código básico que dá suporte à tecnologia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Na prática real, você normalmente usará os projetos Object Relational Designer e Windows Forms para implementar seus [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos. A documentação o/R Designer fornece exemplos e orientações para essa finalidade.  
  
## <a name="getting-started-walkthroughs"></a>Tutoriais passo a passo de introdução  
 Várias explicações passo a passo estão disponíveis nesta seção. Essas explicações passo a passo são baseados no banco de dados de exemplo Northwind e apresentam os recursos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em um ritmo tranquilo com complexidades mínimas.  
  
 Uma progressão típica a ser seguida seria:  
  
|Objetivo|Visual Basic|C#|  
|---------------|------------------|---------|  
|Criar uma classe de entidade e executar uma consulta simples.|[Passo a passo: Modelo de objeto simples e consulta (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md)|[Passo a passo: Modelo de objeto simples e consultaC#()](walkthrough-simple-object-model-and-query-csharp.md)|  
|Adicionar uma segunda classe e executar uma consulta mais complexa.<br /><br /> Requer a conclusão do passo a passo anterior.|[Passo a passo: Consultando entre relações (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)|[Passo a passo: Consultando entre relações (C#)](walkthrough-querying-across-relationships-csharp.md)|  
|Adicionar, alterar e excluir itens no banco de dados.|[Passo a passo: Manipulando dados (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)|[Passo a passo: Manipulando dados (C#)](walkthrough-manipulating-data-csharp.md)|  
|Usar procedimentos armazenados.|[Passo a passo: Usando apenas procedimentos armazenados (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)|[Passo a passo: Usando apenas procedimentos armazenados (C#)](walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>Geral  
 Em geral, as seguintes informações aplicam-se a essas explicações passo a passo:  
  
- Ambiente Cada [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] instrução usa o Visual Studio como seu IDE (ambiente de desenvolvimento integrado).  
  
- Mecanismos SQL: Essas instruções são escritas para serem implementadas usando SQL Server Express. Se você não tiver o SQL Server Express, poderá baixá-lo gratuitamente. Para obter mais informações, consulte [baixar bancos de dados de exemplo](downloading-sample-databases.md).  
  
    > [!NOTE]
    > As explicações passo a passo do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usam um nome de arquivo como uma cadeia de conexão. Simplesmente especificar um nome de arquivo é uma conveniência que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece para usuários do SQL Server Express. Sempre preste atenção aos problemas de segurança. Para obter mais informações, consulte [segurança em LINQ to SQL](security-in-linq-to-sql.md).  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]os passo a passos normalmente exigem o banco de dados de exemplo Northwind. Para obter mais informações, consulte [baixar bancos de dados de exemplo](downloading-sample-databases.md).  
  
- As caixas de diálogo e os comandos de menu que você vê nos passo a passos podem ser diferentes daqueles descritos na ajuda, dependendo de suas configurações ativas ou da edição do Visual Studio. Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
- Para as explicações passo a passo que abordam cenários de várias camadas, um servidor deve estar localizado em um computador que seja diferente do computador de desenvolvimento, e você deve ter as permissões apropriadas para acessar o servidor.  
  
- O nome da classe que normalmente representa a tabela Orders no banco de dados de exemplo Northwind é `[Order]`. A saída é necessária porque `Order` é uma palavra-chave no Visual Basic.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Erros em tempo de execução podem ocorrer porque você não tem permissões suficientes para acessar os bancos de dados usados nessas explicações passo a passo. Consulte as seguintes etapas para ajudar a resolver os problemas mais comuns.  
  
### <a name="log-on-issues"></a>Problemas de logon  
 Seu aplicativo pode estar tentando acessar o banco de dados por meio de um logon de banco de dados que não é aceito.  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>Para verificar ou alterar o logon no banco de dados  
  
1. No menu **Iniciar** do Windows, aponte para **todos os programas**, **Microsoft SQL Server 2005**, aponte para **ferramentas de configuração**e clique em **SQL Server Configuration Manager**.  
  
2. No painel esquerdo da **SQL Server Configuration Manager**, clique em **SQL Server serviços 2005**.  
  
3. No painel direito, clique com o botão direito do mouse em **SQL Server (SQLExpress)** e clique em **Propriedades**.  
  
4. Clique na guia **fazer logon** e verifique como você está tentando fazer logon no servidor.  
  
     Na maioria dos casos, o **sistema local** funciona.  
  
     Se você fizer uma alteração, clique em **reiniciar** para reiniciar o serviço.  
  
### <a name="protocols"></a>Protocolos  
 Às vezes, os protocolos podem não ser definidos corretamente para que seu aplicativo acesse o banco de dados. Por exemplo, o protocolo de **pipes nomeados** , que é necessário para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]orientações no, não está habilitado por padrão.  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>Para habilitar o protocolo Pipes Nomeados  
  
1. No painel esquerdo da **SQL Server Configuration Manager**, expanda **SQL Server configuração de rede 2005**e clique em **protocolos para SQLExpress**.  
  
2. No painel direito, verifique se o protocolo **pipes nomeados** está habilitado. Se não estiver, clique com o botão direito do mouse em **pipes de nome** e clique em **habilitar**.  
  
     Você precisará parar e reiniciar o serviço. Siga as etapas no próximo bloco.  
  
### <a name="stopping-and-restarting-the-service"></a>Parando e reiniciando o serviço  
 Você deve parar e reiniciar os serviços para que suas alterações entrem em vigor.  
  
##### <a name="to-stop-and-restart-the-service"></a>Para parar e reiniciar o serviço.  
  
1. No painel esquerdo da **SQL Server Configuration Manager**, clique em **SQL Server serviços 2005**.  
  
2. No painel direito, clique com o botão direito do mouse em **SQL Server (SQLExpress)** e clique em **parar**.  
  
3. Clique com o botão direito do mouse em **SQL Server (SQLExpress)** e clique em **reiniciar**.  
  
## <a name="see-also"></a>Consulte também

- [Introdução](getting-started.md)
