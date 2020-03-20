---
title: Semântica de comparação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150448"
---
# <a name="comparison-semantics-entity-sql"></a>Semântica de comparação (Entity SQL)
Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:  
  
## <a name="explicit-comparison"></a>Comparação explícita  
 Operações de igualdade:  
  
- =  
  
- !=  
  
 Ordenando operações:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Operações de nulidade:  
  
- IS NULL  
  
- IS NOT NULL  
  
## <a name="explicit-distinction"></a>Distinção explícita  
 Distinção de igualdade:  
  
- DISTINTO  
  
- GROUP BY  
  
 Classificação a distinção:  
  
- ORDER BY  
  
## <a name="implicit-distinction"></a>Distinção implícita  
 Definir operações e predicados (igualdade):  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Predicados de item (igual):  
  
- IN  
  
## <a name="supported-combinations"></a>Combinações com suporte  
 A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:  
  
|**Tipo**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **Distintas**|**União**<br /><br /> **Intersect**<br /><br /> **Exceto**<br /><br /> **Definir**<br /><br /> **OVERLAPS**|**Em**|**< <=**<br /><br /> **> >=**|**ORDEM POR**|**É NULO**<br /><br /> **NÃO É NULO**|  
|-|-|-|-|-|-|-|-|  
|Tipo de entidade|Ref<sup>1</sup>|Todas as propriedades<sup>2</sup>|Todas as propriedades<sup>2</sup>|Todas as propriedades<sup>2</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Ref<sup>1</sup>|  
|Tipo complexo|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|  
|Linha|Todas as propriedades<sup>4</sup>|Todas as propriedades<sup>4</sup>|Todas as propriedades<sup>4</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Todas as propriedades<sup>4</sup>|Lance<sup>3</sup>|  
|Tipo primitivo|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|Específica do provedor|  
|Multiset|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|  
|Ref|Sim<sup>5</sup>|Sim<sup>5</sup>|Sim<sup>5</sup>|Sim<sup>5</sup>|Throw|Throw|Sim<sup>5</sup>|  
|Associação<br /><br /> type|Lance<sup>3</sup>|Throw|Throw|Throw|Lance<sup>3</sup>|Lance<sup>3</sup>|Lance<sup>3</sup>|  
  
 <sup>1</sup> As referências das instâncias de tipo de entidade dadas são implicitamente comparadas, como mostrado no exemplo a seguir:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Uma instância de entidade não pode ser comparado a uma referência explícita. Se isso for tentada, uma exceção é lançada. Por exemplo, a seguinte consulta irá acionar uma exceção:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup> Propriedades de tipos complexos são achatadas antes de serem enviadas para a loja, de modo que se tornam comparáveis (desde que todas as suas propriedades sejam comparáveis). Veja também <sup>4.</sup>  
  
 <sup>3</sup> O tempo de execução do Entity Framework detecta o caso sem suporte e lança uma exceção significativa sem engajar o provedor/loja.  
  
 <sup>4</sup> Uma tentativa é feita para comparar todas as propriedades. Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.  
  
 <sup>5</sup> Todos os elementos individuais das referências são comparados (isso inclui o nome do conjunto da entidade e todas as propriedades-chave do tipo entidade).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da Entity SQL](entity-sql-overview.md)
