---
title: Consulte através das relações
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 783ecb35408f63c7f3e7299e503c3f0fda3f36ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666430"
---
# <a name="querying-across-relationships"></a>Consulte através das relações
Referências a outros objetos ou coleções de outros objetos em suas definições de classe correspondem diretamente às relações de chave estrangeira na base de dados. Você pode usar estas relações quando você consulta usando notação de ponto para acessar as propriedades de relação e para navegar de um objeto para outro. Essas operações de acesso a traduzem mais complexo join ou correlacionaram a subconsultas no equivalente SQL.  
  
 Por exemplo, a consulta a seguir navega pedidos para clientes como uma maneira de restringir os resultados apenas 2 os pedidos de clientes localizados em Londres.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Se as propriedades da relação não existia você teria que escrevê-los manualmente como *junções*, exatamente como você faria em uma consulta SQL, como no código a seguir:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Você pode usar o *relação* propriedade para definir esse relacionamento específico uma vez. Você pode usar a sintaxe mais conveniente de ponto. Mas as propriedades de relação existem mais importante porque os modelos de objeto domínio específicos geralmente são definidos como hierarquias ou elementos gráficos. Os objetos que você programou com têm referências a outros objetos. É apenas uma coincidência felizmente que as relações de objeto-à- objeto correspondem às relações estrangeiro-chave- estilo em bases de dados. Acesso da propriedade em fornece uma maneira conveniente de escrever join.  
  
 Em relação a isso, as propriedades da relação são mais importantes no lado dos resultados de uma consulta de como parte da consulta própria. Depois que a consulta recuperou dados sobre um determinado cliente, a definição de classe indica que os clientes têm pedidos. Ou você espera é a propriedade de `Orders` de um cliente específico ser uma coleção que é preenchida com todos os pedidos do cliente. Isso é fato do contrato que você declarou definindo classes dessa maneira. Você espera consulte existem os pedidos mesmo se a consulta não solicitou pedidos. Você espera seu modelo de objeto manter uma ilusão que é uma extensão de memória de base de dados com objetos relacionados imediatamente disponíveis.  
  
 Agora que você tem relações, você pode escrever consultas com referência às propriedades de relação definidas em suas classes. Essas referências de relação correspondem às relações de chave estrangeira na base de dados. As operações que usam essas relações traduzem a mais complexo ingressar no equivalente SQL. Como você tiver definido uma relação (usando o atributo de <xref:System.Data.Linq.Mapping.AssociationAttribute> ), você não precisará codificar um join explícito em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Para ajudar a manter essa ilusão [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementa uma técnica chamada *carregamento adiado*. Para obter mais informações, consulte [adiada versus imediata Carregando](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Considere a seguinte consulta SQL projetar uma lista dos `CustomerID` - `OrderID` pares:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Para obter os mesmos resultados usando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você usa a referência de propriedade de `Orders` já que existe na classe de `Customer` . O `Orders` referência fornece as informações necessárias para executar a consulta e o projeto de `CustomerID` - `OrderID` pares, como no código a seguir:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Você também pode fazer o inverso. Isto é, você pode ver `Orders` e usar sua referência de relação de `Customer` para acessar informações sobre o objeto associado de `Customer` . O código a seguir projeta o mesmo `CustomerID` - `OrderID` pares como antes, mas desta vez consultando `Orders` em vez de `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Consulte também
- [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
