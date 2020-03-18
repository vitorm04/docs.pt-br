---
title: Habilitando uma fonte de dados para consulta LINQ
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635763"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Habilitando uma fonte de dados para consulta LINQ
Existem várias maneiras de estender o LINQ para permitir que qualquer fonte de dados seja consultada no padrão LINQ. A fonte de dados pode ser uma estrutura de dados, um serviço Web, um sistema de arquivos ou um banco de dados, apenas para citar algumas opções. O padrão LINQ facilita que os clientes consultarem uma fonte de dados para a qual a consulta LINQ está ativada, porque a sintaxe e o padrão da consulta não mudam. As maneiras pelas quais o LINQ pode ser estendido a essas fontes de dados incluem as seguintes:  
  
- Implementação <xref:System.Collections.Generic.IEnumerable%601> da interface em um tipo para habilitar linq para objetos consultando esse tipo.  
  
- Criando métodos padrão de <xref:System.Linq.Enumerable.Where%2A> operador <xref:System.Linq.Enumerable.Select%2A> de consulta, tais como e que estendem um tipo, para permitir consulta siniçal personalizada desse tipo.  
  
- Criação de um provedor para sua fonte de dados que implemente a interface <xref:System.Linq.IQueryable%601>. Um provedor que implementa essa interface recebe consultas LINQ na forma de árvores de expressão, que pode ser executada de forma personalizada, por exemplo remotamente.  
  
- Criar um provedor para sua fonte de dados que se aproveita de uma tecnologia LINQ existente. Tal provedor habilitaria não apenas a consulta, mas também operações de inserção, atualização e exclusão e mapeamento para tipos definidos pelo usuário.  
  
 Este tópico aborda essas opções.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Como habilitar consultas de LINQ da sua fonte de dados  
  
### <a name="in-memory-data"></a>Dados na memória  
 Existem duas maneiras de habilitar a consulta LINQ de dados na memória. Se os dados forem de <xref:System.Collections.Generic.IEnumerable%601>um tipo que implemente, você pode consultar os dados usando LINQ to Objects. Se não fizer sentido habilitar a enumeração do <xref:System.Collections.Generic.IEnumerable%601> seu tipo implementando a interface, você pode definir os métodos padrão de operador de consulta LINQ nesse tipo ou criar métodos padrão de operador de consulta LINQ que estendem o tipo. As implementações personalizadas dos operadores de consulta padrão devem usar a execução adiada para retornar os resultados.  
  
### <a name="remote-data"></a>Dados remotos  
 A melhor opção para habilitar a consulta LINQ de <xref:System.Linq.IQueryable%601> uma fonte de dados remota é implementar a interface. No entanto, isso é diferente de estender um provedor como o [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] para uma fonte de dados. Não há modelos de provedor para estender [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]as tecnologias linq existentes, tais como , para outros tipos de fonte de dados estão disponíveis no Visual Studio 2008.
  
## <a name="iqueryable-linq-providers"></a>Provedores IQueryable de LINQ  
 Os provedores <xref:System.Linq.IQueryable%601> linq que implementam podem variar amplamente em sua complexidade. Esta seção discute os diferentes níveis de complexidade.  
  
 Um provedor menos complexo de `IQueryable` poderia fazer a interface com um único método de um serviço Web. Esse tipo de provedor é muito específico porque ele espera informações específicas nas consultas que manipula. Ele possui um sistema de tipos fechado, talvez expondo um único tipo de resultado. A maior parte da execução da consulta ocorre localmente, por exemplo, usando as implementações de <xref:System.Linq.Enumerable> dos operadores de consulta padrão. Um provedor menos complexo poderia examinar somente uma expressão de chamada do método na árvore de expressões que representa a consulta e deixar que a lógica restante da consulta fosse manipulada em outro lugar.  
  
 Um provedor de `IQueryable` de complexidade média pode destinar uma fonte de dados que tem uma linguagem de consulta parcialmente expressiva. Se o destino é um serviço Web, ele pode fazer a interface com mais de um método de serviço Web e selecionar o método a ser chamado com base na questão representada pela consulta. Um provedor de complexidade média teria um sistema de tipos maiores do que um provedor simples, mas continuaria a ser um sistema de tipo fixo. Por exemplo, o provedor pode expor os tipos que têm relação um para muitos que podem ser atravessados, mas não forneceria tecnologia de mapeamento de tipos definidos pelo usuário.  
  
 Um `IQueryable` provedor complexo, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] como o provedor, pode traduzir consultas linq completas para uma linguagem de consulta expressiva, como o SQL. Um provedor complexo é mais geral do que um provedor menos complexo porque pode manipular uma variedade mais ampla de perguntas na consulta. Ele também possui um sistema de tipos abertos e, consequentemente, deve conter uma infraestrutura extensiva para mapear tipos definidos pelo usuário. Desenvolver um provedor complexo requer uma quantidade significativa de esforço.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
