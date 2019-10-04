---
title: FUNÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: bacc773351812a5db60f493f3025c8e4b07dbaa2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833797"
---
# <a name="function-entity-sql"></a>FUNÇÃO (Entity SQL)
Define uma função no escopo de um comando de consulta Entity SQL.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Argumentos  
 `function-name`  
 Nome da função.  
  
 `parameter-name`  
 Nome de um parâmetro em função.  
  
 `function_expression`  
 Uma expressão válida de Entity SQL que é a função. O comando na função pode atuar nos parâmetros de `parameter_name` passados para a função.  
  
 `data_type`  
 Nome de um tipo suportado.  
  
 COLEÇÃO (< type_definition @ no__t-0)  
 Uma expressão que retorna uma coleção de tipos suportados, de linhas, ou de referências.  
  
 REF **(** `data_type` **)**  
 Uma expressão que retorna uma referência a um tipo de objeto.  
  
 ROW **(** `row_expression` **)**  
 Uma expressão que retorna registros anônimos, tipados estrutural de um ou mais valores. Para obter mais informações, consulte [linha](row-entity-sql.md).  
  
## <a name="remarks"></a>Comentários  
 Várias funções com o mesmo nome podem ser declarados embutidos, como as assinaturas de função são diferentes. Para obter mais informações, consulte [resolução de sobrecarga de função](function-overload-resolution-entity-sql.md).  
  
 Uma função in-line pode ser chamado em um comando de Entity SQL somente após foi definida no comando. No entanto, uma função in-line pode ser chamada dentro de outra função in-line tanto antes ou após a função chamada foi definido. No exemplo a seguir, funciona a função B de chamadas de antes que a função B é definida:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Para obter mais informações, confira [Como: Chame uma função definida pelo usuário @ no__t-0.  
  
 As funções podem também ser declaradas no próprio modelo. As funções declaradas no modelo são executadas da mesma forma como as funções está embutido no comando. Para obter mais informações, consulte [funções definidas pelo usuário](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte comando de Entity SQL define uma função `Products` que recebe um valor inteiro para filtrar os produtos retornados.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Exemplo  
 O seguinte comando de Entity SQL define uma função `StringReturnsCollection` que utiliza uma coleção de cadeias de caracteres para filtrar os contatos retornados.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [Entity SQL Language](entity-sql-language.md) (Linguagem SQL de entidade)
