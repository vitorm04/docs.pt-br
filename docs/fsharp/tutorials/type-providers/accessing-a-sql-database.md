---
title: "Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos (F#)"
description: "Saiba como usar o provedor de tipos SqlDataConnection (LINQ to SQL) em F # 3.0 para gerar tipos para um banco de dados SQL quando você tem uma conexão de banco de dados ao vivo."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: 7177eca33ded712308bbc6198040d833b7364d55
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.  Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

> [!NOTE]
Os links de referência de API levará você para o MSDN.  A referência da API docs.microsoft.com não está completa.

Este passo a passo explica como usar o provedor de tipos SqlDataConnection (LINQ to SQL) que está disponível em F # 3.0 para gerar tipos de dados em um banco de dados SQL quando você tem uma conexão ao vivo para um banco de dados. Se você não tiver uma conexão ao vivo para um banco de dados, mas você tem um LINQ para SQL esquema (arquivo DBML), consulte [passo a passo: gerando tipos F # em um arquivo DBML](generating-fsharp-types-from-dbml.md).

Esta explicação passo a passo mostra as seguintes tarefas. Essas tarefas devem ser executadas nesta ordem para a passo a passo para ter êxito:


- Preparar um banco de dados de teste

- Criando o projeto

- Configurando um provedor de tipos

- Consultando os dados

- Trabalhando com campos anuláveis

- Chamando um procedimento armazenado

- Atualizando o banco de dados

- Execução de código Transact-SQL

- Usando o contexto de dados completo

- Excluindo dados

- Criar um banco de dados de teste (conforme necessário)

## <a name="preparing-a-test-database"></a>Preparar um banco de dados de teste
Em um servidor que executa o SQL Server, crie um banco de dados para fins de teste. Você pode usar o banco de dados criar script na parte inferior desta página, na seção [criando um banco de dados de teste](#creating-a-test-database) para fazer isso.


#### <a name="to-prepare-a-test-database"></a>Para preparar um banco de dados de teste

Para executar o Script de criar MyDatabase, abra o **exibição** menu e, em seguida, escolha **Pesquisador de objetos do SQL Server** ou escolha Ctrl +\, teclas Ctrl + S. Em **Pesquisador de objetos do SQL Server** janela, abra o menu de atalho para a instância apropriada, escolha **nova consulta**, copie o script na parte inferior desta página e, em seguida, cole o script no editor. Para executar o script SQL, escolha o ícone da barra de ferramentas com o símbolo triangular ou escolha as teclas Ctrl + Q. Para obter mais informações sobre **Pesquisador de objetos do SQL Server**, consulte [desenvolvimento de banco de dados conectado](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).


## <a name="creating-the-project"></a>Criando o projeto
Em seguida, você pode criar um projeto de aplicativo do F #.


#### <a name="to-create-and-set-up-the-project"></a>Criar e configurar o projeto

1. Crie um novo projeto de aplicativo do F #.

2. Adicione referências a [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), bem como `System.Data`, e `System.Data.Linq`.

3. Abra os namespaces apropriados, adicionando as seguintes linhas de código para a parte superior do seu arquivo de código F # Program.fs.

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. Assim como acontece com a maioria dos programas F #, você pode executar o código neste passo a passo como um programa compilado ou isso pode ser executado interativamente como um script. Se você preferir usar scripts, abra o menu de atalho para o nó do projeto, selecione **Adicionar Novo Item**, adicione um arquivo de script F # e adicione o código de cada etapa no script. Você precisará adicionar as seguintes linhas na parte superior do arquivo para carregar as referências de assembly.

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  Você pode selecionar cada bloco de código e adicioná-lo e pressione Alt + Enter para executá-lo no F # interativo.

## <a name="setting-up-a-type-provider"></a>Configurando um provedor de tipos
Nesta etapa, você pode criar um provedor de tipos para o esquema de banco de dados.


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>Para configurar o provedor de tipo de uma conexão direta do banco de dados

Há duas linhas críticas de código que você precisa para criar os tipos que você pode usar para consultar um banco de dados SQL usando o provedor de tipo. Primeiro, você pode instanciar o provedor de tipos. Para fazer isso, crie a aparência de uma abreviação de tipo de um `SqlDataConnection` com um parâmetro genérico estático. `SqlDataConnection`é um provedor de tipo SQL e não deve ser confundido com `SqlConnection` tipo que é usado na programação do ADO.NET. Se você tiver um banco de dados que você deseja se conectar e ter uma cadeia de caracteres de conexão, use o seguinte código para chamar o provedor de tipo. Substitua por sua própria cadeia de caracteres de conexão para a cadeia de caracteres de exemplo fornecida. Por exemplo, se seu servidor MYSERVER e a instância de banco de dados é a instância, o nome do banco de dados é MyDatabase, e você deseja usar a autenticação do Windows para acessar o banco de dados e, em seguida, a cadeia de caracteres de conexão seria como fornecido no código de exemplo a seguir.

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

Agora você tem um tipo, `dbSchema`, que é um tipo de pai que contém todos os tipos gerados que representam as tabelas de banco de dados. Você também tem um objeto `db`, que tenha como seus membros todas as tabelas no banco de dados. Os nomes de tabela são propriedades e o tipo dessas propriedades é gerado pelo compilador F #. Os tipos de si mesmos aparecem como tipos aninhados em `dbSchema.ServiceTypes`. Portanto, quaisquer dados recuperados para linhas dessas tabelas serão uma instância do tipo apropriado que foi gerado para aquela tabela. É o nome do tipo `ServiceTypes.Table1`.

Para se familiarizar com como a linguagem F # interpreta consultas em consultas SQL, examine a linha que define o `Log` propriedade no contexto de dados.

Para explorar os tipos criados pelo provedor de tipo, adicione o código a seguir.

```fsharp
let table1 = db.Table1
```

Passe o mouse sobre `table1` para ver seu tipo. Seu tipo é `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` e o argumento genérico implica que o tipo de cada linha é o tipo gerado, `dbSchema.ServiceTypes.Table1`. O compilador cria um tipo semelhante para cada tabela no banco de dados.

## <a name="querying-the-data"></a>Consultando os dados
Nesta etapa, você escreve uma consulta usando expressões de consulta do F #.


#### <a name="to-query-the-data"></a>Para consultar os dados

1. Agora, crie uma consulta para essa tabela no banco de dados. Adicione o código a seguir.

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  A aparência da palavra `query` indica que esta é uma expressão de consulta, um tipo de expressão de computação que gera um conjunto de resultados semelhantes de uma consulta de banco de dados típico. Se você focaliza a consulta, você verá que ele é uma instância de [classe LINQ. querybuilder](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), um tipo que define a expressão de computação de consulta. Se você focalizar `query1`, você verá que ele é uma instância de `System.Linq.IQueryable`. Como o nome sugere, `System.Linq.IQueryable` representa os dados que podem ser consultados, não o resultado de uma consulta. Uma consulta está sujeita a avaliação lenta, o que significa que o banco de dados só é consultado quando a consulta é avaliada. A linha final passa a consulta por meio de `Seq.iter`. As consultas são enumeráveis e podem ser iteradas como sequências. Para obter mais informações, consulte [expressões de consulta](../../language-reference/query-expressions.md).

2. Agora, adicione um operador de consulta à consulta. Há um número de operadores de consulta disponíveis que você pode usar para construir consultas mais complexas. Este exemplo também mostra que você pode eliminar a variável de consulta e use um operador de pipeline em vez disso.

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. Adicione uma consulta mais complexa com uma junção de duas tabelas.

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. No código do mundo real, os parâmetros na consulta são geralmente valores ou variáveis, constantes de tempo de compilação não. Adicione o seguinte código que encapsula uma consulta em uma função que aceita um parâmetro e, em seguida, chama a função com valor de 10.

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>Trabalhando com campos anuláveis
Em bancos de dados, os campos geralmente permitem valores nulos. No sistema de tipo .NET, você não pode usar os tipos de dados numérico comum para dados que permite valores nulos porque esses tipos não têm nulo como um valor possível. Portanto, esses valores são representados por instâncias do `System.Nullable` tipo. Em vez de acessar o valor desses campos diretamente com o nome do campo, você precisa adicionar algumas etapas adicionais. Você pode usar o `System.Nullable.Value` propriedade para acessar o valor subjacente de um tipo anulável. O `System.Nullable.Value` propriedade gera uma exceção se o objeto é nulo em vez de um valor. Você pode usar o `System.Nullable.HasValue` método booliano para determinar se existe um valor ou use `System.Nullable.GetValueOrDefault()` para garantir que você tenha um valor real em todos os casos. Se você usar `System.Nullable.GetValueOrDefault()` e houver um valor nulo no banco de dados, ele será substituído com um valor como uma cadeia de caracteres vazia para tipos de cadeia de caracteres, 0 para tipos integrais 0,0 para flutuante ponto ou tipos.

Quando você precisa executar testes de igualdade ou comparações em valores anuláveis em um `where` cláusula em uma consulta, você pode usar os operadores permitem valor nulos encontrados na [módulo LINQ. nullableoperators](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d). Esses são como os operadores de comparação regular `=`, `>`, `<=`e assim por diante, exceto que um ponto de interrogação é exibido à esquerda ou à direita do operador onde estão os valores nulos. Por exemplo, o operador `>?` é maior-que o operador com um valor nulo à direita. A maneira como esses operadores trabalha é que, se ambos os lados da expressão for null, a expressão é avaliada como `false`. Em um `where` cláusula, isso geralmente significa que as linhas que contêm campos nulos não são selecionadas e não retornadas nos resultados da consulta.


#### <a name="to-work-with-nullable-fields"></a>Para trabalhar com campos anuláveis

O código a seguir mostra o trabalho com valores anuláveis. Suponha que **TestData1** é um campo de número inteiro que permite valores nulos.

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a>Chamando um procedimento armazenado
Todos os procedimentos armazenados no banco de dados podem ser chamados do F #. Você deve definir o parâmetro static `StoredProcedures` para `true` em uma instância de provedor de tipo. O provedor de tipo `SqlDataConnection` contém vários métodos estáticos que você pode usar para configurar os tipos que são gerados. Para obter uma descrição completa dessas, consulte [provedor de tipo SqlDataConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d). Um método no tipo de contexto de dados é gerado para cada procedimento armazenado.


#### <a name="to-call-a-stored-procedure"></a>Para chamar um procedimento armazenado

Se os procedimentos armazenados usa parâmetros que permitem valor nulo, você precisa passar um apropriado `System.Nullable` valor. O valor de retorno de um método de procedimento armazenado que retorna um valor escalar ou uma tabela é `System.Data.Linq.ISingleResult`, que contém propriedades que permitem que você acesse os dados retornados. O argumento de tipo para `System.Data.Linq.ISingleResult` depende do procedimento específico e também é um dos tipos que gera o provedor de tipos. Para um procedimento armazenado denominado `Procedure1`, o tipo é `Procedure1Result`. O tipo `Procedure1Result` contém os nomes das colunas em uma tabela retornada, ou, para um procedimento armazenado que retorna um valor escalar, ele representa o valor de retorno.

O código a seguir supõe que há um procedimento `Procedure1` no banco de dados que usa dois inteiros anuláveis como parâmetros, executa uma consulta que retorna uma coluna denominada `TestData1`e retorna um inteiro.

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a>Atualizando o banco de dados
O tipo DataContext LINQ contém métodos que facilitam a executar atualizações transacionadas do banco de dados de maneira totalmente digitada com os tipos gerados.


#### <a name="to-update-the-database"></a>Para atualizar o banco de dados

1. No código a seguir, várias linhas são adicionadas ao banco de dados. Se você só estiver adicionando uma linha, você pode usar `System.Data.Linq.Table.InsertOnSubmit()` para especificar a nova linha para adicionar. Se você estiver inserindo várias linhas, você deve colocá-los em uma coleção e chamada `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`. Quando você chamar qualquer um desses métodos, o banco de dados não é alterado imediatamente. Você deve chamar `System.Data.Linq.DataContext.SubmitChanges` para confirmar as alterações. Por padrão, tudo o que fazer antes de chamar `System.Data.Linq.DataContext.SubmitChanges` implicitamente faz parte da mesma transação.

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. Limpe agora as linhas chamando uma operação de exclusão.

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a>Execução de código Transact-SQL
Você também pode especificar o Transact-SQL diretamente usando o `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` método o `DataContext` classe.


#### <a name="to-execute-custom-sql-commands"></a>Para executar comandos SQL personalizados

O código a seguir mostra como enviar comandos SQL para inserir um registro em uma tabela e também para excluir um registro de uma tabela.

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a>Usando o contexto de dados completo
Nos exemplos anteriores, o `GetDataContext` método foi usado para obter o que é chamado de *o contexto de dados simplificado* para o esquema de banco de dados. O contexto de dados simplificado é mais fácil de usar ao construir consultas porque não há como muitos membros. Portanto, quando você procura as propriedades do IntelliSense, você pode se concentrar na estrutura de banco de dados, como as tabelas e procedimentos armazenados. No entanto, há um limite para que você pode fazer com o contexto de dados simplificado. Um contexto de dados completo que fornece a capacidade de executar outras ações. também está disponível que ele está localizado no `ServiceTypes` e tem o nome do *DataContext* parâmetro estático se você forneceu a ele. Se você não forneceu-lo, o nome do tipo de contexto de dados é gerado para você por SqlMetal.exe com base em outra entrada. Herda o contexto de dados completo de `System.Data.Linq.DataContext` e expõe os membros de sua classe base, incluindo as referências aos tipos de dados do ADO.NET, como o `Connection` objeto, métodos, como `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` e `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` que você pode usar para escrever consultas em SQL, e também um meio para funcionar com transações explicitamente.


#### <a name="to-use-the-full-data-context"></a>Para usar o contexto de dados completo

O código a seguir demonstra a obtenção de um objeto de contexto de dados completo e usá-lo para executar comandos diretamente no banco de dados. Nesse caso, os dois comandos são executados como parte da mesma transação.

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a>Excluindo dados
Esta etapa mostra como excluir linhas de uma tabela de dados.


#### <a name="to-delete-rows-from-the-database"></a>Para excluir linhas do banco de dados

Agora, limpar qualquer adicionadas linhas ao escrever uma função que exclui linhas de uma tabela especificada, uma instância do `System.Data.Linq.Table` classe. Em seguida, escrever uma consulta para localizar todas as linhas que você deseja excluir e direcionar os resultados da consulta no `deleteRows` função. Esse código aproveita a capacidade de fornecer aplicativo parcial de argumentos de função.

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a>Criando um banco de dados de teste
Esta seção mostra como configurar o banco de dados de teste para usar neste passo a passo.

Observe que, se você alterar o banco de dados de alguma forma, você precisará redefinir o provedor de tipos. Para redefinir o provedor de tipos, recriar ou limpe o projeto que contém o provedor de tipo.


#### <a name="to-create-the-test-database"></a>Para criar o banco de dados de teste

1. Em **Server Explorer**, abra o menu de atalho para o **conexões de dados** nó e escolha **Adicionar Conexão**. O **Adicionar Conexão** caixa de diálogo é exibida.

2. No **nome do servidor** caixa, especifique o nome de uma instância do SQL Server que têm acesso administrativo ao ou, se você não tiver acesso a um servidor, especifique (localdb\v11.0). SQL Express LocalDB fornece um servidor de banco de dados leve para desenvolvimento e teste em seu computador. É criado um novo nó no **Server Explorer** em **conexões de dados**. Para obter mais informações sobre o LocalDB, consulte [passo a passo: Criando um arquivo de banco de dados Local no Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).

3. Abra o menu de atalho para o novo nó de conexão e selecione **nova consulta**.

4. Copie o seguinte script SQL, cole-o no editor de consultas e, em seguida, escolha o **Execute** botão na barra de ferramentas ou escolha as teclas Ctrl + Shift + E.

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a>Consulte também
[Provedores de Tipos](index.md)

[Tipo SqlDataConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[Passo a passo: Gerando tipos F # em um arquivo DBML](generating-fsharp-types-from-dbml.md)

[Expressões de Consulta](../../language-reference/query-expressions.md)

[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)

[SqlMetal.exe &#40; Ferramenta de geração de código &#41;](https://msdn.microsoft.com/library/bb386987)
