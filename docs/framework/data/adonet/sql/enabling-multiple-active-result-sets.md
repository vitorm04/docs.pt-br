---
title: Habilitando vários conjuntos de resultados ativos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 70e589fcff241a664ef470dfeb746412cde6b515
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570194"
---
# <a name="enabling-multiple-active-result-sets"></a>Habilitando vários conjuntos de resultados ativos
O Multiple Active Result Sets (MARS) é um recurso que funciona com o SQL Server para permitir a execução de vários lotes em uma única conexão. Quando MARS está ativado para uso com o SQL Server, cada objeto de comando usado adiciona uma sessão à conexão.  
  
> [!NOTE]
>  Uma sessão única de MARS abre uma conexão lógica para MARS para uso e, em seguida, uma conexão lógica para cada comando ativo.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Habilitando e desabilitando MARS na cadeia de conexão  
  
> [!NOTE]
>  As seguintes cadeias de caracteres de conexão usam a amostra **AdventureWorks** banco de dados incluído com o SQL Server. As cadeias de conexão fornecidas supõem que o banco de dados esteja instalado em um servidor chamado MSSQL1. Modifique a cadeia de conexão conforme o necessário para seu ambiente.  
  
 O recurso MARS é desabilitado por padrão. Ele pode ser ativado adicionando o par de palavras-chave de "MultipleActiveResultSets=True" à cadeia de conexão. "True" é o único valor válido para habilitar MARS. O exemplo a seguir demonstra como conectar-se a uma instância do SQL Server e como especificar que o MARS deve ser habilitado.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 Você pode desabilitar MARS adicionando o par de palavras-chave de "MultipleActiveResultSets=False" à cadeia de conexão. "False" é o único valor válido para desabilitar MARS. A cadeia de conexão a seguir demonstra como desabilitar MARS.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>Considerações especiais ao usar MARS  
 Geralmente, os aplicativos existentes não devem precisar de nenhuma alteração para usar uma conexão habilitada para MARS. Entretanto, se você quiser usar os recursos do MARS em seus aplicativos, deverá compreender as seguintes considerações especiais.  
  
### <a name="statement-interleaving"></a>Interpolação de instrução  
 As operações de MARS são executadas de maneira síncrona no servidor. A interpolação das instruções SELECT e BULK INSERT é permitida. No entanto, as instruções da linguagem DML e de DDL (linguagem de definição de dados) são executadas atomicamente. As instruções que tentarem ser executadas enquanto um lote atômico é executado serão bloqueadas. A execução paralela no servidor não é um recurso do MARS.  
  
 Se dois lotes forem enviados em uma conexão de MARS, um deles contendo uma instrução SELECT e o outro contendo uma instrução de DML, o DML pode iniciar a execução dentro da execução da instrução SELECT. No entanto, a instrução de DML deve ser executada para ser concluída antes de a instrução SELECT poder continuar. Se as duas instruções estiverem em execução na mesma transação, as alterações feitas por uma instrução de DML após a declaração SELECT ter começado a execução não serão visíveis para a operação de leitura.  
  
 Uma instrução WAITFOR dentro de uma instrução SELECT não produz a transação enquanto aguarda, ou seja, até que a primeira linha seja gerada. Isso significa que nenhum outro lote pode ser executado dentro da mesma conexão enquanto uma instrução WAITFOR estiver aguardando.  
  
### <a name="mars-session-cache"></a>Cache de sessão de MARS  
 Quando uma conexão é aberta com o MARS habilitado, uma sessão lógica é criada, o que adiciona uma sobrecarga adicional. Para minimizar a sobrecarga e melhorar o desempenho, **SqlClient** armazena em cache a sessão de MARS dentro de uma conexão. O cache contém no máximo 10 sessões de MARS. Este valor não é ajustável pelo usuário. Se o limite de sessão for alcançado, uma nova sessão será criada. Um erro não será gerado. O cache e as sessões contidas nela são por conexão; não são compartilhados entre as conexões. Quando uma sessão é lançada, é retornada para o pool a menos que o limite superior do pool tenha sido alcançado. Se o pool do cache estiver concluído, a sessão será fechada. As sessões do MARS não expiram. Elas somente são limpas quando o objeto de conexão é descartado. O cache de sessão de MARS não é pré-carregado. Ele é carregado quando o aplicativo exige mais sessões.  
  
### <a name="thread-safety"></a>Segurança de threads  
 As operações de MARS não são thread-safe.  
  
### <a name="connection-pooling"></a>Pool de conexões  
 As conexões habilitadas para MARS são agrupadas como qualquer outra conexão. Se um aplicativo abrir duas conexões, uma com MARS habilitado e outra com MARS desabilitado, as duas conexões estarão em pools separados. Para obter mais informações, confira [Pooling de conexão do SQL Server (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Ambiente de execução em lotes do SQL Server  
 Quando uma conexão é aberta, um ambiente padrão é definido. Esse ambiente é, em seguida, copiado em uma sessão lógica do MARS.  
  
 O ambiente de execução em lotes inclui os seguintes componentes:  
  
-   Opções de conjunto (por exemplo, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)  
  
-   Contexto de segurança (usuário/função do aplicativo)  
  
-   Contexto de banco de dados (o banco de dados atual)  
  
-   Variáveis de estado de execução (por exemplo, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Tabelas temporárias de nível superior  
  
 Com o MARS, um ambiente padrão de execução está associado a uma conexão. Cada novo lote que inicia sendo executado em uma determinada conexão recebe uma cópia do ambiente padrão. Sempre que o código é executado em um determinado lote, todas as alterações feitas ao ambiente são do escopo do lote específico. Quando a execução estiver concluída, as configurações de execução serão copiadas no ambiente padrão. No caso de um único lote que emite vários comandos para serem executados em sequência na mesma transação, a semântica é a mesma que as expostas por conexões que envolvem clientes ou servidores anteriores.  
  
### <a name="parallel-execution"></a>Execução paralela  
 O MARS não é criado para remover todos os requisitos para várias conexões em um aplicativo. Se um aplicativo precisar de execução paralela verdadeira de comandos em um servidor, várias conexões deverão ser usadas.  
  
 Por exemplo, considere o seguinte cenário. Dois objetos de comando são criados, um para processar um conjunto de resultados e outro para atualizar dados; eles compartilham uma conexão comum através do MARS. Nesse cenário, o `Transaction`.`Commit` Falha na atualização até que todos os resultados tenham sido lidos no primeiro objeto de comando, gerando a seguinte exceção:  
  
 Mensagem: Contexto de transação em uso por outra sessão.  
  
 Origem: provedor de dados .Net SqlClient  
  
 Esperado: (null)  
  
 Recebido: System.Data.SqlClient.SqlException  
  
 Há três opções para tratar esse cenário:  
  
1.  Inicie a transação após o leitor ter sido criado, de modo que não faça parte da transação. Cada atualização em seguida se torna sua própria transação.  
  
2.  Confirme todo o trabalho depois que o leitor for fechado. Isso tem o potencial para um lote significativo de atualizações.  
  
3.  Não use MARS; em vez disso, use uma conexão separada para cada objeto de comando, da mesma forma que você faria antes do MARS.  
  
### <a name="detecting-mars-support"></a>Detectando o suporte de MARS  
 Um aplicativo pode verificar o suporte de MARS lendo o valor `SqlConnection.ServerVersion`. O número principal deve ser 9 para o SQL Server 2005 e 10 para o SQL Server 2008.  
  
## <a name="see-also"></a>Consulte também
- [MARS (Conjunto de Resultados Ativos Múltiplos)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
