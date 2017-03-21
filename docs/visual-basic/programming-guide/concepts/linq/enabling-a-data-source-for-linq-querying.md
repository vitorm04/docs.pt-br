---
title: Habilitando uma fonte de dados para LINQ Querying2 | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34bdc4e056d982799eac35eb2398dd3f23f6f351
ms.lasthandoff: 03/13/2017

---
# <a name="enabling-a-data-source-for-linq-querying"></a>Habilitando uma fonte de dados para consulta LINQ
Há várias maneiras de estender [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para habilitar qualquer fonte de dados a ser consultado no [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] padrão. A fonte de dados pode ser uma estrutura de dados, um serviço Web, um sistema de arquivos ou um banco de dados, apenas para citar algumas opções. O padrão [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] torna fácil para os clientes consultarem uma fonte de dados para a qual a consulta do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] está habilitada, porque a sintaxe e o padrão de consulta não mudam. As formas nas quais [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pode ser estendido para esses dados de fontes incluem o seguinte:  
  
-   Implementando o <xref:System.Collections.Generic.IEnumerable%601>interface em um tipo para habilitar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para consultar objetos desse tipo.</xref:System.Collections.Generic.IEnumerable%601>  
  
-   Criando métodos operadores de consulta padrão como <xref:System.Linq.Enumerable.Where%2A>e <xref:System.Linq.Enumerable.Select%2A>que estende um tipo, para habilitar personalizado [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas desse tipo.</xref:System.Linq.Enumerable.Select%2A> </xref:System.Linq.Enumerable.Where%2A>  
  
-   Criar um provedor de fonte de dados que implementa o <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> Um provedor que implementa a interface recebe consultas de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] na forma de árvores de expressões, as quais ele pode executar de forma personalizada, por exemplo, remotamente.  
  
-   Criar um provedor de fonte de dados que tira proveito de um objeto existente [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] tecnologia. Tal provedor habilitaria não apenas a consulta, mas também operações de inserção, atualização e exclusão e mapeamento para tipos definidos pelo usuário.  
  
 Este tópico aborda essas opções.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Como habilitar consultas de LINQ da sua fonte de dados  
  
### <a name="in-memory-data"></a>Dados na memória  
 Há duas maneiras que você pode habilitar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta dos dados na memória. Se os dados são de um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>, você pode consultar os dados usando [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para objetos.</xref:System.Collections.Generic.IEnumerable%601> Se ele não faz sentido para habilitar a enumeração do tipo Implementando o <xref:System.Collections.Generic.IEnumerable%601>interface, você pode definir [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] padrão métodos de operador nesse tipo de consulta ou criar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] métodos operadores de consulta padrão que estendem o tipo.</xref:System.Collections.Generic.IEnumerable%601> As implementações personalizadas dos operadores de consulta padrão devem usar a execução adiada para retornar os resultados.  
  
### <a name="remote-data"></a>Dados remotos  
 A melhor opção para habilitar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta de fonte de dados remota é implementar o <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> No entanto, isso é diferente de estender um provedor como o [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] para uma fonte de dados. Nenhum modelo de provedor para estender existente [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] tecnologias, como [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], para outros tipos de fonte de dados estão disponíveis em [!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)].  
  
## <a name="iqueryable-linq-providers"></a>Provedores IQueryable de LINQ  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]provedores que implementam <xref:System.Linq.IQueryable%601>podem variar muito em complexidade.</xref:System.Linq.IQueryable%601> Esta seção discute os diferentes níveis de complexidade.  
  
 Um provedor menos complexo de `IQueryable` poderia fazer a interface com um único método de um serviço Web. Esse tipo de provedor é muito específico porque ele espera informações específicas nas consultas que manipula. Ele possui um sistema de tipos fechado, talvez expondo um único tipo de resultado. A maior parte da execução da consulta ocorre localmente, por exemplo, usando o <xref:System.Linq.Enumerable>implementações de operadores de consulta padrão.</xref:System.Linq.Enumerable> Um provedor menos complexo poderia examinar somente uma expressão de chamada do método na árvore de expressões que representa a consulta e deixar que a lógica restante da consulta fosse manipulada em outro lugar.  
  
 Um provedor de `IQueryable` de complexidade média pode destinar uma fonte de dados que tem uma linguagem de consulta parcialmente expressiva. Se o destino é um serviço Web, ele pode fazer a interface com mais de um método de serviço Web e selecionar o método a ser chamado com base na questão representada pela consulta. Um provedor de complexidade média teria um sistema de tipos maiores do que um provedor simples, mas continuaria a ser um sistema de tipo fixo. Por exemplo, o provedor pode expor os tipos que têm relação um para muitos que podem ser atravessados, mas não forneceria tecnologia de mapeamento de tipos definidos pelo usuário.  
  
 Um provedor complexo de `IQueryable`, como o provedor de [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], poderia traduzir consultas completas de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para uma linguagem de consultas expressiva, como SQL. Um provedor complexo é mais geral do que um provedor menos complexo porque pode manipular uma variedade mais ampla de perguntas na consulta. Ele também possui um sistema de tipos abertos e, consequentemente, deve conter uma infraestrutura extensiva para mapear tipos definidos pelo usuário. Desenvolver um provedor complexo requer uma quantidade significativa de esforço.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.IQueryable%601></xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
