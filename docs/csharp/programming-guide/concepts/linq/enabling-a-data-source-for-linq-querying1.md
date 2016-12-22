---
title: "Habilitando uma fonte de dados para consulta LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Habilitando uma fonte de dados para consulta LINQ
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Há várias maneiras de estender [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para habilitar qualquer fonte de dados a ser consultado no [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] padrão. A fonte de dados pode ser uma estrutura de dados, um serviço da Web, um sistema de arquivos ou um banco de dados, para citar alguns. O [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] padrão torna mais fácil para os clientes consultar uma fonte de dados para o qual [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultando estiver habilitado, a sintaxe e o padrão da consulta mudam. As formas nas quais [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pode ser estendido para esses dados de fontes incluem o seguinte:  
  
-   Implementando o <xref:System.Collections.Generic.IEnumerable%601> interface em um tipo para habilitar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para consultar objetos desse tipo.  
  
-   Criando métodos operadores de consulta padrão como <xref:System.Linq.Enumerable.Where%2A> e <xref:System.Linq.Enumerable.Select%2A> que estende um tipo, para habilitar personalizado [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas desse tipo.  
  
-   Criar um provedor de fonte de dados que implementa o <xref:System.Linq.IQueryable%601> interface. Um provedor que implementa essa interface recebe [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas na forma de árvores de expressão, ela pode ser executada de forma personalizada, por exemplo remotamente.  
  
-   Criar um provedor de fonte de dados que tira proveito de um objeto existente [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] tecnologia. Tal provedor habilitaria não apenas consulta, mas também insert, update e as operações de exclusão e mapeamento para tipos definidos pelo usuário.  
  
 Este tópico aborda essas opções.  
  
## Como habilitar consultas de LINQ da sua fonte de dados  
  
### Dados na memória  
 Há duas maneiras que você pode habilitar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta dos dados na memória. Se os dados são de um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>, você pode consultar os dados usando [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] a objetos. Se ele não faz sentido para habilitar a enumeração do tipo Implementando o <xref:System.Collections.Generic.IEnumerable%601> interface, você pode definir [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] padrão métodos de operador nesse tipo de consulta ou criar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] métodos operadores de consulta padrão que estendem o tipo. Implementações personalizadas dos operadores de consulta padrão devem usar a execução adiada para retornar os resultados.  
  
### Dados remotos  
 A melhor opção para habilitar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta de fonte de dados remota é implementar o <xref:System.Linq.IQueryable%601> interface. No entanto, isso é diferente de estender um provedor como [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] para uma fonte de dados. Nenhum modelo de provedor para estender existente [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] tecnologias, como [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], para outros tipos de fonte de dados estão disponíveis em [!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)].  
  
## Provedores de LINQ IQueryable  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedores que implementam <xref:System.Linq.IQueryable%601> podem variar muito em termos de complexidade. Esta seção discute os diferentes níveis de complexidade.  
  
 Um menos complexo `IQueryable` provedor pode fazer interface com um único método de um serviço Web. Esse tipo de provedor é muito específico porque ele espera informações específicas nas consultas que manipula. Ele tem um sistema de tipo fechado, talvez expondo um único tipo de resultado. A maior parte da execução da consulta ocorre localmente, por exemplo, usando o <xref:System.Linq.Enumerable> implementações de operadores de consulta padrão. Um provedor menos complexo pode examinar a expressão de chamada de apenas um método na árvore de expressão que representa a consulta e permitir que a lógica restante da consulta ser manipulada em outro lugar.  
  
 Um `IQueryable` provedor de complexidade média pode destinar uma fonte de dados que tem uma linguagem de consulta parcialmente expressiva. Se o destino é um serviço da Web, ele pode interface com mais de um método do serviço Web e selecione o método para chamar com base na pergunta que representa a consulta. Um provedor de complexidade média teria um sistema de tipo mais sofisticado que um provedor simples, mas ainda seria um sistema de tipo fixo. Por exemplo, o provedor pode expor os tipos que possuem relações um\-para\-muitos que podem ser atravessadas, mas não forneceria tecnologia de mapeamento para tipos definidos pelo usuário.  
  
 Um complexo `IQueryable` provedor, como o [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] provedor, poderia traduzir completa [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas em uma linguagem de consulta expressiva, como SQL. Um provedor complexo é mais geral do que um provedor menos complexo, porque pode manipular uma variedade maior de perguntas na consulta. Ele também tem um sistema de tipo aberto e, portanto, deve conter uma infraestrutura extensiva para mapear tipos definidos pelo usuário. Desenvolver um provedor complexo requer uma quantidade significativa de esforço.  
  
## Consulte também  
 <xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)