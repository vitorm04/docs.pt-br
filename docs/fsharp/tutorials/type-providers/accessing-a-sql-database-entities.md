---
title: "Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades (F#)"
description: 'Saiba como acessar dados de tipo para um banco de dados do SQL com base no modelo de dados de entidade ADO.NET em F # 3.0.'
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: e0e78e06fa1129ba5eeb73bc36c14343c93d6927
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.  Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

> [!NOTE]
Os links de referência de API levará você para o MSDN.  A referência da API docs.microsoft.com não está completa.

Esse guia passo a passo para o F# 3.0 mostra como acessar dados tipados para um banco de dados SQL baseado no Modelo de Dados de Entidade ADO.NET. Esse guia passo a passo mostra como configurar o provedor de tipos `SqlEntityConnection` do F# para uso com um banco de dados SQL, como criar consultas para dados, como chamar procedimentos armazenados no banco de dados, bem como usar alguns métodos e tipos do ADO.NET Entity Framework para atualizar o banco de dados.

Esse guia passo a passo ilustra as seguintes tarefas que você deve executar nesta ordem para que as instruções sejam bem-sucedidas:


- Criar o banco de dados escolar
<br />

- Criar e configurar um projeto F#
<br />

- Configurar o provedor de tipos e conecte-se ao modelo de dados de entidade
<br />

- Consulta o banco de dados
<br />

- Atualizando o banco de dados
<br />


## <a name="prerequisites"></a>Pré-requisitos
Você deve ter acesso a um servidor que esteja executando um SQL Server onde você possa criar um banco de dados para concluir estas etapas.

## <a name="create-the-school-database"></a>Criar o banco de dados escolar
Você pode criar o banco de dados escolar em qualquer servidor que esteja executando um SQL Server ao qual você tenha acesso administrativo ou pode usar LocalDB.


#### <a name="to-create-the-school-database"></a>Para criar o banco de dados escolar

1. Em **Server Explorer**, abra o menu de atalho para o **conexões de dados** nó e, em seguida, escolha **Adicionar Conexão**.
<br />  O **Adicionar Conexão** caixa de diálogo é exibida.
<br />

2. No **nome do servidor** caixa, especifique o nome de uma instância do SQL Server ao qual você tem acesso administrativo ou especificar (localdb\v11.0) se você não tiver acesso a um servidor.
<br />  O SQL Server Express LocalDB oferece um servidor de banco de dados leve para desenvolvimento e teste em seu computador. Para obter mais informações sobre o LocalDB, consulte [passo a passo: Criando um arquivo de banco de dados Local no Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).
<br />  É criado um novo nó no **Server Explorer** em **conexões de dados**.
<br />

3. Abra o menu de atalho para o novo nó de conexão e, em seguida, escolha **nova consulta**.
<br />

4. Abra [criando o banco de dados de exemplo School](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) no site da Microsoft e, em seguida, copiar e colar o script de banco de dados que cria o banco de dados School na janela do editor.
<br />


## <a name="BKMK_CreateConfigFSProj"> </a>

## <a name="create-and-configure-an-f-project"></a>Criar e configurar um projeto F#
Nesta etapa, você criará um projeto e o configurará para usar um provedor de tipos.


#### <a name="to-create-and-configure-an-f-project"></a>Para criar e configurar um projeto F#

1. Fechar o projeto anterior, crie outro projeto e nomeie-o **SchoolEDM**.
<br />

2. Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência**.
<br />

3. Escolha o **Framework** nó e, em seguida, no **Framework** , escolha **System. Data**, **System.Data.Entity**e **System.Data.Linq**.
<br />

4. Escolha o **extensões** nó, adicione uma referência para o [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly e, em seguida, escolha o **Okey** botão para ignorar a caixa de diálogo.
<br />

5. Adicione o código a seguir para definir um módulo interno e abrir namespaces apropriados. O provedor de tipos pode injetar tipos somente em um namespace particular ou interno.
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. Para executar o código neste passo a passo interativamente como um script em vez de como um programa compilado, abra o menu de atalho para o nó do projeto, escolha **Adicionar Novo Item**, adicione um arquivo de script F # e, em seguida, adicione o código de cada etapa no script. Para carregar as referências de assembly, adicione as linhas a seguir.
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. Realce cada bloco de código conforme o adiciona e escolha as teclas Alt + Enter para executá-lo em F# Interativo.
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Configurar o provedor de tipos e conectar ao Modelo de Dados de Entidade
Nesta etapa, você configura um provedor de tipos com uma conexão de dados e obtém um contexto de dados que permite trabalhar com dados.


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Para configurar o provedor de tipos e conectar ao Modelo de Dados de Entidade

1. Insira o código a seguir para configurar o provedor de tipos `SqlEntityConnection` que gera tipos do F# com base no Modelo de Dados de Entidade que você criou anteriormente. Em vez da cadeia de conexão completa do EDMX, use apenas a cadeia de conexão SQL.
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  Esta ação configura um provedor de tipos com a conexão de banco de dados que você criou anteriormente. A propriedade `MultipleActiveResultSets` é necessária quando você usa o ADO.NET Entity Framework porque essa propriedade permite que vários comandos sejam executados de modo assíncrono no banco de dados em uma conexão, isso pode ocorrer frequentemente no código do ADO.NET Entity Framework. Para obter mais informações, confira [MARS (Conjunto de Resultados Ativos Múltiplos)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).
<br />

2. Obtenha o contexto de dados que é um objeto com tabelas do banco de dados como propriedades e procedimentos armazenados e funções do banco de dados como métodos.
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>Consultando o banco de dados
Nesta etapa, você usará expressões de consulta F# para executar várias consultas no banco de dados.


#### <a name="to-query-the-data"></a>Para consultar os dados

- Insira o código a seguir para consultar os dados do modelo de dados de entidade. Observe o efeito de Pluralize = true que altera Course para Courses e Person para People na tabela de banco de dados.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a>Atualizando o banco de dados
Para atualizar o banco de dados, use as classes e os métodos do Entity Framework. Você pode usar dois tipos de contexto de dados com o provedor de tipos SQLEntityConnection. Primeiro, `ServiceTypes.SimpleDataContextTypes.EntityContainer` é o contexto de dados simplificado que inclui somente as propriedades fornecidas que representam tabelas e colunas do banco de dados. Segundo, o contexto de dados completo é uma instância da classe `System.Data.Objects.ObjectContext` do Entity Framework que contém o método `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` para adicionar linhas ao banco de dados. O Entity Framework reconhece as tabelas e os relacionamentos entre elas, assim, ele impõe consistência ao banco de dados.


#### <a name="to-update-the-database"></a>Para atualizar o banco de dados

1. Adicione o código a seguir ao seu programa. Neste exemplo, você adiciona dois objetos com um relacionamento entre eles e um instrutor e uma atribuição comercial. A tabela `OfficeAssignments` contém a coluna `InstructorID` que faz referência à coluna `PersonID` na tabela `Person`.
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

Nada será alterado no banco de dados até que você chame `System.Data.Objects.ObjectContext.SaveChanges`.
<br />

2. Agora, restaure o banco de dados ao seu estado anterior ao excluir os objetos que você adicionou.
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
Ao usar uma expressão de consulta, lembre-se de que a consulta estará sujeita a avaliação lenta. Portanto, o banco de dados ainda estará aberto para leitura durante quaisquer avaliações encadeadas como nos blocos de expressão lambda após cada expressão de consulta. Qualquer operação de banco de dados que usar explícita ou implicitamente uma transação deverá ocorrer depois que as operações de leitura forem concluídas.


## <a name="next-steps"></a>Próximas etapas
Explore outras opções de consulta examinando os operadores de consulta disponíveis no [expressões de consulta](../../language-reference/query-expressions.md)e também Revise o [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) entender qual funcionalidade está disponível para você quando você usar esse provedor de tipo.


## <a name="see-also"></a>Consulte também
[Provedores de Tipos](index.md)  
[Tipo SqlEntityConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[Passo a passo: Gerando tipos F # de um arquivo de esquema EDMX](generating-fsharp-types-from-edmx.md)  
[Entity Framework do ADO.NET](https://msdn.microsoft.com/library/bb399572)  
[Visão geral do arquivo. edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[Gerador EDM &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)  
