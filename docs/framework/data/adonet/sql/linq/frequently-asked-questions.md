---
title: Perguntas frequentes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 5f556c46823bd867709e8c53b59f7ac53201d242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="frequently-asked-questions"></a>Perguntas frequentes
As seções a seguir respondem a alguns problemas comuns que você pode encontrar ao implementar o [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Problemas adicionais serão tratados nas [solução de problemas](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Não é possível conectar  
 P. Não consigo me conectar a meu banco de dados.  
  
 R. Verifique se a cadeia de conexão está correta e se a instância do SQL Server está em execução. Observe também que o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige que o protocolo de pipes nomeados esteja ativado. Para obter mais informações, consulte [aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Alterações perdidas do banco de dados  
 P. Fiz uma alteração nos dados no banco de dados, mas, quando executei o aplicativo, a alteração não estava mais lá.  
  
 R. Verifique se você chamou <xref:System.Data.Linq.DataContext.SubmitChanges%2A> para salvar os resultados no banco de dados.  
  
## <a name="database-connection-open-how-long"></a>Conexão do banco de dados: há quanto tempo está aberta?  
 P. Quanto tempo a conexão do banco de dados permanece aberta?  
  
 R. Uma conexão geralmente permanece aberta até você consumir os resultados da consulta. Se você pretende processar todos os resultados e não se opõe a armazenar em cache os resultados, aplique <xref:System.Linq.Enumerable.ToList%2A> à consulta. Em cenários comuns onde cada objeto é processado somente uma vez, o modelo de streaming é superior no `DataReader` e no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Os detalhes exatos do uso da conexão dependem do seguinte:  
  
-   Status da conexão se <xref:System.Data.Linq.DataContext> for construído com um objeto de conexão.  
  
-   Configurações da cadeia de conexão (por exemplo, permitindo MARS, Multiple Active Result Sets). Para obter mais informações, confira [MARS (Conjunto de Resultados Ativos Múltiplos)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Atualizar sem consultar  
 P. Posso atualizar os dados da tabela sem primeiro consultar o banco de dados?  
  
 R. Embora o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não tenha comandos de atualização baseados em conjunto, você pode usar qualquer uma das seguintes técnicas para atualizar sem consultar primeiro:  
  
-   Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> para enviar o código SQL.  
  
-   Crie uma nova instância do objeto e inicialize todos os valores atuais (campos) que afetam a atualização. Anexe o objeto ao <xref:System.Data.Linq.DataContext> usando <xref:System.Data.Linq.Table%601.Attach%2A> e modifique o campo que você deseja alterar.  
  
## <a name="unexpected-query-results"></a>Resultados inesperados da consulta  
 P. Minha consulta está retornando resultados inesperados. Como posso inspecionar o que está ocorrendo?  
  
 R. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece várias ferramentas para inspecionar o código SQL que produz. Um dos mais importantes é <xref:System.Data.Linq.DataContext.Log%2A>. Para obter mais informações, consulte [suporte de depuração](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Resultados inesperados de procedimentos armazenados  
 P. Tenho um procedimento armazenado cujo valor de retorno é calculado por `MAX()`. Quando eu arrasto o procedimento armazenado para a superfície do [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)], o valor de retorno não está correto.  
  
 R. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece duas maneiras de retornar valores gerados por banco de dados por meio de procedimentos armazenados:  
  
-   Nomeando o resultado de saída.  
  
-   Especificando explicitamente um parâmetro de saída.  
  
 O código a seguir é um exemplo de saída incorreta. Como o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não pode mapear os resultados, ele sempre retorna 0:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 O código a seguir é um exemplo de saída correta usando um parâmetro de saída:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 O código a seguir é um exemplo de saída correta nomeando o resultado de saída:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Para obter mais informações, consulte [personalizando operações, usando procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Erros de serialização  
 P. Ao tentar serializar, recebo o seguinte erro: "digite 'System.Data.Linq.ChangeTracker+StandardChangeTracker'... não é marcado como serializável."  
  
 R. A geração de código no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte à serialização do <xref:System.Runtime.Serialization.DataContractSerializer>. Ela não dá suporte a <xref:System.Xml.Serialization.XmlSerializer> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Para obter mais informações, consulte [Serialização](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Vários arquivos DBML  
 P. Quando eu tenho vários arquivos DBML que compartilham algumas tabelas em comum, eu obtenho um erro do compilador.  
  
 R. Definir o **contexto Namespace** e **entidade Namespace** propriedades do [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para um valor distinto para cada arquivo DBML. Essa abordagem elimina a colisão nome/namespace.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Evitando a configuração explícita de valores gerados por banco de dados em Insert ou Update  
 P. Tenho uma tabela de banco de dados com uma coluna `DateCreated` que usa como padrão o `Getdate()` do SQL. Quando tento inserir um novo registro usando o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o valor é definido como `NULL`. Eu gostaria que ele fosse definido como o padrão do banco de dados.  
  
 R. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] trata essa situação automaticamente para colunas de identidade (incremento automático) e rowguidcol (GUID gerado por banco de dados) e carimbo de data/hora. Em outros casos, você deve definir manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> propriedades.  
  
## <a name="multiple-dataloadoptions"></a>Vários DataLoadOptions  
 P. Posso especificar opções de carregamento adicionais sem substituir as primeiras?  
  
 R. Sim. A primeira não é substituída, como no exemplo a seguir:  
  
```vb  
Dim dlo As New DataLoadOptions()  
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)  
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)  
```  
  
```csharp  
DataLoadOptions dlo = new DataLoadOptions();  
dlo.LoadWith<Order>(o => o.Customer);  
dlo.LoadWith<Order>(o => o.OrderDetails);  
```  
  
## <a name="errors-using-sql-compact-35"></a>Erros ao usar o SQL Compact 3.5  
 P. Recebo um erro quando arrasto as tabelas para fora de um banco de dados do [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)].  
  
 R. O [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] não oferece suporte ao [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], embora o tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o faça. Nesta situação, você deve criar suas próprias classes de entidade e adicionar os atributos apropriados.  
  
## <a name="errors-in-inheritance-relationships"></a>Erros nas relações de herança  
 P. Usei o formato de herança da caixa de ferramentas no [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para conectar duas entidades, mas obtive erros.  
  
 R. Criar a relação não é suficiente. Você deve fornecer informações como a coluna do discriminador, o valor do discriminador da classe base e o valor do discriminador da classe derivada.  
  
## <a name="provider-model"></a>Modelo do provedor  
 P. Um modelo de provedor público está disponível?  
  
 R. Nenhum modelo de provedor público está disponível. Neste momento, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte ao SQL Server e [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] apenas.  
  
## <a name="sql-injection-attacks"></a>Ataques de injeção de SQL  
 P. Como o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é protegido contra ataques de injeção de SQL?  
  
 R. A injeção de SQL tem sido um risco significativo para consultas tradicionais de SQL formadas por meio da concatenação da entrada do usuário. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] evita essa injeção usando o <xref:System.Data.SqlClient.SqlParameter> em consultas. A entrada do usuário é transformada em valores de parâmetro. Essa abordagem impede que os comandos mal-intencionados sejam usados da entrada do cliente.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>Alterando o sinalizador somente leitura em arquivos DBML  
 P. Como posso eliminar configuradores de algumas propriedades quando crio um modelo de objeto de um arquivo DBML?  
  
 R. Siga as etapas a seguir para este cenário avançado:  
  
1.  No arquivo .dbml, modifique a propriedade alterando o sinalizador do <xref:System.Data.Linq.ITable.IsReadOnly%2A> para `True`.  
  
2.  Adicione uma classe parcial. Crie um construtor com parâmetros para os membros somente leitura.  
  
3.  Examine o valor padrão <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) para determinar se este é o valor correto para seu aplicativo.  
  
    > [!CAUTION]
    >  Se você estiver usando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] no Visual Studio, as alterações poderão ser substituídas.  
  
## <a name="aptca"></a>APTCA  
 P. O System.Data.Linq está marcado para ser usado pelo código parcialmente confiável?  
  
 R. Sim, o conjunto System.Data.Linq.dll está entre os assemblies do [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] marcados com o atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Sem esta marcação, os assemblies no [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] são destinados para o uso somente pelo código totalmente confiável.  
  
 O cenário principal [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para permitir parcialmente confiável é permitir que os chamadores a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly seja acessado por aplicativos Web, onde o *confiança* configuração é médio.  
  
## <a name="mapping-data-from-multiple-tables"></a>Dados de mapeamento de várias tabelas  
 P. Os dados na minha entidade vêm de várias tabelas. Como posso mapeá-los?  
  
 R. Você pode criar uma exibição em um banco de dados e mapear a entidade para a exibição. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera o mesmo SQL para exibições da mesma forma que faz para tabelas.  
  
> [!NOTE]
>  O uso de exibições nesse cenário tem limitações. Essa abordagem funciona com mais segurança quando as operações realizadas no <xref:System.Data.Linq.Table%601> têm suporte pela exibição subjacente. Somente você sabe quais operações são desejadas. Por exemplo, a maioria dos aplicativos são somente leitura e executar outro número considerável `Create` / `Update` / `Delete` operações usando somente procedimentos armazenados em modos de exibição.  
  
## <a name="connection-pooling"></a>Pool de conexões  
 P. Há uma construção que possa ajudar com o pool de <xref:System.Data.Linq.DataContext>?  
  
 R. Não tente reutilizar instâncias do <xref:System.Data.Linq.DataContext>. Cada <xref:System.Data.Linq.DataContext> mantém o estado (incluindo um cache de identidade) para uma determinada sessão de edição/consulta. Para obter as novas instâncias com base no estado atual do banco de dados, use um novo <xref:System.Data.Linq.DataContext>.  
  
 Você ainda pode usar o pool de conexões do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] subjacente. Para obter mais informações, confira [Pooling de conexão do SQL Server (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>O segundo DataContext não é atualizado  
 P. Eu usei uma instância do <xref:System.Data.Linq.DataContext> para armazenar valores no banco de dados. No entanto, um segundo <xref:System.Data.Linq.DataContext> no mesmo banco de dados não reflete os valores atualizados. A segunda instância do <xref:System.Data.Linq.DataContext> parece retornar os valores armazenados em cache.  
  
 R. Esse comportamento é padrão. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] continua a retornar as mesmas instâncias/valores que você viu na primeira instância. Quando você faz atualizações, usa a simultaneidade otimista. Os dados originais são usados para verificar o estado atual do banco de dados e declarar que ainda estão de fato inalterados. Se eles forem alterados, um conflito ocorre e seu aplicativo deve resolvê-lo. Uma opção do aplicativo é redefinir o estado original para o estado atual do banco de dados e tentar novamente a atualização. Para obter mais informações, consulte [como: gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Você também pode definir o <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> como falso, o que desativa o cache e o controle de alterações. Você pode então recuperar os valores mais recentes toda vez que consultar.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Não é possível chamar SubmitChanges no modo somente leitura  
 P. Quando eu tento chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no modo somente leitura, obtenho um erro.  
  
 R. O modo somente leitura desativa a capacidade de o contexto controlar as alterações.  
  
## <a name="see-also"></a>Consulte também  
 [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Solução de problemas](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)  
 [Segurança em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
