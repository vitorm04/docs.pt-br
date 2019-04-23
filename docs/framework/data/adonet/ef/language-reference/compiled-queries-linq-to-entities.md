---
title: Consultas compiladas (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: f3ba6bfd0f83270bc6b9e980fe92f6630c90ad49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193064"
---
# <a name="compiled-queries--linq-to-entities"></a>Consultas compiladas (LINQ to Entities)
Quando um aplicativo executa muitas vezes consultas estruturalmente similares no Entity Framework, geralmente é possível melhorar o desempenho compilando a consulta uma única vez e executando-a várias vezes com parâmetros diferentes. Por exemplo, um aplicativo pode precisar recuperar todos os clientes de uma cidade específica; a cidade é especificada em tempo de execução pelo usuário em um formulário. LINQ to Entities dá suporte ao uso de consultas compiladas para essa finalidade.  
  
 A partir do .NET Framework 4.5, as consultas LINQ são automaticamente armazenadas em cache. No entanto, você ainda pode usar consultas LINQ para reduzir esse custo em execuções posteriores e consultas compiladas podem ser mais eficientes que consultas LINQ que são automaticamente armazenadas em cache. Observe que as consultas LINQ to Entities que aplicam o operador `Enumerable.Contains` a coleções na memória não são armazenadas em cache automaticamente. Além disso, não é permitido parametrizar coleções na memória em consultas LINQ compiladas.  
  
 A classe <xref:System.Data.Objects.CompiledQuery> fornece a compilação e o cache de consultas para reutilização. Conceitualmente, essa classe contém um método <xref:System.Data.Objects.CompiledQuery> de `Compile` com várias sobrecargas. Chame o método `Compile` para criar um novo delegado para representar a consulta compilada. Os métodos `Compile`, com <xref:System.Data.Objects.ObjectContext> e valores de parâmetro, retornam um delegado que gera um resultado (como uma instância <xref:System.Linq.IQueryable%601>). A consulta é compilada somente uma vez durante a primeira execução. As opções de mesclagem definidas para a consulta no momento da compilação não podem ser alteradas posteriormente. Uma vez compilada a consulta, você só pode fornecer parâmetros de tipo primitivo, mas não pode substituir partes da consulta que alterariam o SQL gerado. Para obter mais informações, consulte [opções de mesclagem do Entity Framework e consultas compiladas](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 O [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] expressão de consulta que o <xref:System.Data.Objects.CompiledQuery>do `Compile` método compila é representada por um dos genéricos `Func` delega, tais como <xref:System.Func%605>. No máximo, a expressão de consulta pode encapsular um parâmetro `ObjectContext`, um parâmetro de retorno e 16 parâmetros de consulta. Se mais de 16 parâmetros de consulta forem necessários, você poderá criar uma estrutura cujas propriedades representem parâmetros de consulta. Será possível usar, então, as propriedades da estrutura na expressão de consulta depois de definir as propriedades.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que aceita um parâmetro de entrada <xref:System.Decimal> e retorna uma sequência de pedidos em que o total devido é maior ou igual a US$ 200:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que retorna uma instância <xref:System.Data.Objects.ObjectQuery%601>:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que retorna a média dos preços na lista de produtos como um valor <xref:System.Decimal>:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que aceita uma <xref:System.String> parâmetro de entrada e, em seguida, retorna um `Contact` cujos endereços de email começa com a cadeia de caracteres especificada:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que aceita os parâmetros de entrada <xref:System.DateTime> e <xref:System.Decimal> e retorna uma sequência de pedidos em que a data do pedido é posterior a 8 de março de 2003 e o total devido é menor que US$ 300:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que aceita um parâmetro de entrada <xref:System.DateTime> e retorna uma sequência de pedidos em que a data do pedido é posterior a 8 de março de 2004. Essa consulta retorna informações de pedidos como uma sequência de tipos anônimos. Os tipos anônimos são inferidos pelo compilador. Assim, não é possível especificar parâmetros de tipo no método <xref:System.Data.Objects.CompiledQuery> de `Compile` e o tipo é definido na própria consulta.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila e invoca uma consulta que aceita um parâmetro de entrada de estrutura definida pelo usuário e retorna uma sequência de pedidos. A estrutura define a data de início, a data de término e os parâmetros de consulta do total devido, e a consulta retorna os pedidos enviados entre 3 de março e 8 de março de 2003 com um total devido maior que US$ 700.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 A estrutura que define os parâmetros de consulta:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Consulte também

- [Entity Framework do ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Opções de mesclagem do Entity Framework e consultas compiladas](https://go.microsoft.com/fwlink/?LinkId=199591)
