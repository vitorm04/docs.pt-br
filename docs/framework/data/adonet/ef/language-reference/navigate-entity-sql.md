---
title: NAVEGAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: e66a09276f40ab6d9ff7c11bb160385b4c1efb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542551"
---
# <a name="navigate-entity-sql"></a>NAVEGAR (Entity SQL)
Navega sobre a relação entre estabelecida entidades.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a>Arguments  
 `instance-expresssion`  
 Uma instância de um objeto.  
  
 `relationship-type`  
 O nome do tipo de relação, o arquivo de (CSDL) de linguagem de definição de esquema conceitual. O `relationship-type` é qualificado como \<namespace >.\< nome do tipo de relação >.  
  
 `to`  
 O final da relação.  
  
 `from`  
 O início da relação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se a cardinalidade da finalizar é 1, o valor de retorno será `Ref<T>`. Se a cardinalidade da finalizar é, no valor de retorno será `Collection<Ref<T>>`.  
  
## <a name="remarks"></a>Comentários  
 As relações são construções de primeira classe em [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM). As relações podem ser estabelecidas entre dois ou mais tipos de entidade, e os usuários podem navegar sobre a relação de fim (entidade) para outra. `from` e `to` condicional são opcionais quando não há nenhuma ambiguidade na resolução de nomes dentro da relação.  
  
 NAVIGATE é válido no espaço de C e de 2.0.  
  
 O formulário geral de uma compilação de navegação é o seguinte:  
  
 navegue (`instance-expresssion`, `relationship-type`, [ `to-end` , `from-end` ] [])  
  
 Por exemplo:  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 Onde OrderCustomer está `relationship`, e o cliente e ordem são `to-end` (cliente) e `from-end` (ordem) da relação. Se fosse uma relação n:1, então o tipo de resultado da expressão navegar é Ref\<cliente >.  
  
 A forma mais simples desta expressão é o seguinte:  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 Da mesma forma, em uma consulta da seguinte forma, a expressão navegar produziria uma coleção < Ref\<ordem >>.  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 A instância expressão deve ser um tipo de entidade/referência.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador NAVEGAR IN para navegar sobre o relacionamento estabelecido entre tipos de entidade de endereço e de SalesOrderHeader. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a>Consulte também
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Como: Navegue relações com o operador de navegar](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
