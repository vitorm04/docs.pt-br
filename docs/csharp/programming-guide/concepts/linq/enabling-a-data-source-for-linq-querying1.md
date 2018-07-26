---
title: Habilitando uma fonte de dados para consulta LINQ1
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 5b67995f40bc0cb703003aa80b511268f21da8b8
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220991"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Habilitando uma fonte de dados para consulta LINQ
Há várias formas de estender o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para permitir que qualquer fonte de dados seja consultada no padrão [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. A fonte de dados pode ser uma estrutura de dados, um serviço Web, um sistema de arquivos ou um banco de dados, apenas para citar algumas opções. O padrão [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] torna fácil para os clientes consultarem uma fonte de dados para a qual a consulta do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] está habilitada, porque a sintaxe e o padrão de consulta não mudam. As formas nas quais o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pode ser estendido para essas fontes de dados incluem as seguintes:  
  
-   Implementação da interface <xref:System.Collections.Generic.IEnumerable%601> em um tipo para habilitar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para consultas de Objetos desse tipo.  
  
-   Criação de métodos de operador de consulta padrão, como <xref:System.Linq.Enumerable.Where%2A> e <xref:System.Linq.Enumerable.Select%2A> que estendem um tipo, para habilitar consultas personalizadas de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] desse tipo.  
  
-   Criação de um provedor para sua fonte de dados que implemente a interface <xref:System.Linq.IQueryable%601>. Um provedor que implementa a interface recebe consultas de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na forma de árvores de expressões, as quais ele pode executar de forma personalizada, por exemplo, remotamente.  
  
-   Criar um provedor para sua fonte de dados que se beneficia de uma tecnologia existente do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Tal provedor habilitaria não apenas a consulta, mas também operações de inserção, atualização e exclusão e mapeamento para tipos definidos pelo usuário.  
  
 Este tópico aborda essas opções.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Como habilitar consultas de LINQ da sua fonte de dados  
  
### <a name="in-memory-data"></a>Dados na memória  
 Há duas formas como você pode habilitar consultas do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para dados na memória. Se os dados forem de um tipo que implemente <xref:System.Collections.Generic.IEnumerable%601>, você poderá consultar os dados usando o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para Objetos. Se não fizer sentido habilitar a enumeração do tipo por meio da implementação da interface <xref:System.Collections.Generic.IEnumerable%601>, você poderá definir métodos de operador de consulta padrão do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesse tipo ou criar métodos de operador de consulta padrão do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] que estendem o tipo. As implementações personalizadas dos operadores de consulta padrão devem usar a execução adiada para retornar os resultados.  
  
### <a name="remote-data"></a>Dados remotos  
 A melhor opção para habilitar consultas do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] de uma fonte de dados remota é implementar a interface <xref:System.Linq.IQueryable%601>. No entanto, isso é diferente de estender um provedor como o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] para uma fonte de dados. Nenhum modelo de provedor para estender as tecnologias [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] existentes, como o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], para outros tipos de fontes de dados está disponível no [!INCLUDE[vs_orcas_long](~/includes/vs-orcas-long-md.md)].  
  
## <a name="iqueryable-linq-providers"></a>Provedores IQueryable de LINQ  
 Os provedores de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] que implementam <xref:System.Linq.IQueryable%601> podem variar enormemente em termos de complexidade. Esta seção discute os diferentes níveis de complexidade.  
  
 Um provedor menos complexo de `IQueryable` poderia fazer a interface com um único método de um serviço Web. Esse tipo de provedor é muito específico porque ele espera informações específicas nas consultas que manipula. Ele possui um sistema de tipos fechado, talvez expondo um único tipo de resultado. A maior parte da execução da consulta ocorre localmente, por exemplo, usando as implementações de <xref:System.Linq.Enumerable> dos operadores de consulta padrão. Um provedor menos complexo poderia examinar somente uma expressão de chamada do método na árvore de expressões que representa a consulta e deixar que a lógica restante da consulta fosse manipulada em outro lugar.  
  
 Um provedor de `IQueryable` de complexidade média pode destinar uma fonte de dados que tem uma linguagem de consulta parcialmente expressiva. Se o destino é um serviço Web, ele pode fazer a interface com mais de um método de serviço Web e selecionar o método a ser chamado com base na questão representada pela consulta. Um provedor de complexidade média teria um sistema de tipos maiores do que um provedor simples, mas continuaria a ser um sistema de tipo fixo. Por exemplo, o provedor pode expor os tipos que têm relação um para muitos que podem ser atravessados, mas não forneceria tecnologia de mapeamento de tipos definidos pelo usuário.  
  
 Um provedor complexo de `IQueryable`, como o provedor de [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], poderia traduzir consultas completas de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para uma linguagem de consultas expressiva, como SQL. Um provedor complexo é mais geral do que um provedor menos complexo porque pode manipular uma variedade mais ampla de perguntas na consulta. Ele também possui um sistema de tipos abertos e, consequentemente, deve conter uma infraestrutura extensiva para mapear tipos definidos pelo usuário. Desenvolver um provedor complexo requer uma quantidade significativa de esforço.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.IQueryable%601>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 <xref:System.Linq.Enumerable>  
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
