---
title: "Como: Funções de base de dados personalizados de chamada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2aab11481bb23228f9ad920c5d01ef7d345e05d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-custom-database-functions"></a>Como: Funções de base de dados personalizados de chamada
Este tópico descreve como chamar funções personalizados que são definidas na base de dados de dentro das consultas LINQ to Entities.  
  
 Funções de base de dados que são chamadas de consultas LINQ to entidades são executadas em base de dados. Executar funções na base de dados pode melhorar o desempenho do aplicativo.  
  
 O procedimento a seguir fornece um contorno de alto nível para chamar uma função de base de dados personalizado. O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Para chamar funções personalizados que são definidas na base de dados  
  
1.  Crie uma função personalizada em seu base de dados.  
  
     Para obter mais informações sobre como criar funções personalizadas no SQL Server, consulte [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).  
  
2.  Declarar uma função em linguagem de definição de esquema de armazenamento (SSDL) do arquivo. edmx. O nome da função deve ser o mesmo que o nome da função declarada no base de dados.  
  
     Para obter mais informações, consulte [elemento de função (SSDL)](http://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).  
  
3.  Adicione um método correspondente a uma classe em seu código do aplicativo e aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> a nota de método que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente. A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.  
  
4.  Chame o método em uma consulta LINQ to Entities.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar uma função de base de dados personalizado de uma consulta LINQ to Entities. O exemplo usa o modelo de escola. Para obter informações sobre o modelo de escola, consulte [criando o banco de dados de exemplo School](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) e [gerando o EDMX escola arquivo](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 O código a seguir adiciona a função de `AvgStudentGrade` a base de dados de exemplo de escola.  
  
> [!NOTE]
>  As etapas para chamar uma função de base de dados personalizado são as mesmas independentemente do servidor de base de dados. No entanto, o código abaixo é específico para criar uma função em uma base de dados SQL Server. O código para criar uma função personalizada em outros servidores de base de dados pode ser diferente.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Exemplo  
 Em seguida, declarar uma função em linguagem de definição de esquema de armazenamento (SSDL) do arquivo. edmx. o código a seguir declara a função de `AvgStudentGrade` em SSDL:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Exemplo  
 Agora crie um método e mapear-lo a função declarada em SSDL. O método na classe é mapeado para a função definida em SSDL (acima) usando <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Quando esse método é chamado, a função correspondente na base de dados é executada.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Finalmente, chame o método em uma consulta LINQ to Entities. O código a seguir exibe os sobrenomes e as ordens média dos alunos no console:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do arquivo. edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
