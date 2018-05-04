---
title: Definição do esquema de DataTable
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 81da3937b709d4ef046eb1c470546f168bde4132
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="datatable-schema-definition"></a>Definição do esquema de DataTable
O esquema, ou a estrutura, de uma tabela é representado por colunas e restrições. Você define o esquema de uma <xref:System.Data.DataTable> usando objetos <xref:System.Data.DataColumn>, bem como objetos <xref:System.Data.ForeignKeyConstraint> e <xref:System.Data.UniqueConstraint>. As colunas em uma tabela podem ser mapeadas para colunas em uma fonte de dados, contêm valores calculados de expressões, incrementam automaticamente seus valores ou contêm valores de chave primária.  
  
 As referências por nome a colunas, relações e restrições em uma tabela diferenciam maiúsculas de minúsculas. Duas ou mais colunas, relações ou restrições podem, portanto, existir em uma tabela que tenha o mesmo nome, mas que seja diferente quanto ao uso de maiúsculas e minúsculas. Por exemplo, você pode ter **Col1** e **col1**. Nesse caso, uma referência a uma das colunas por nome deve corresponder ao uso exato de maiúsculas e minúsculas do nome da coluna; do contrário, uma exceção será lançada. Por exemplo, se a tabela **myTable** contém as colunas **Col1** e **col1**, você deve fazer referência a **Col1** por nome como  **myTable.Columns["Col1"]**, e **col1** como **myTable.Columns["col1"]**. Tentativa de fazer referência a uma das colunas como **myTable.Columns["COL1"]** poderia gerar uma exceção.  
  
 A regra de diferenciação de maiúsculas e minúsculas não se aplicará se houver apenas uma coluna, relação ou restrição com um nome específico. Ou seja, se nenhum outro objeto de coluna, relação ou restrição na tabela corresponder ao nome desse objeto de coluna, relação ou restrição específico, você poderá fazer referência ao objeto por nome usando qualquer uso de maiúsculas e minúsculas, e nenhuma exceção será lançada. Por exemplo, se a tabela tem somente **Col1**, você pode fazer referência a ele usando **meu. Colunas ["COL1"]**.  
  
> [!NOTE]
>  O <xref:System.Data.DataTable.CaseSensitive%2A> propriedade o **DataTable** não afeta a esse comportamento. O **CaseSensitive** propriedade aplica-se aos dados em uma tabela e afeta a classificação, pesquisa, filtragem, impondo restrições e assim por diante, mas não para referências a colunas, relações e restrições.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Adicionando colunas a um DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Descreve como definir as colunas de uma tabela usando **DataColumn** objetos.  
  
 [Criar colunas de expressão](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Explica como o **expressão** propriedade de uma coluna pode ser usada para calcular valores com base nos valores de outras colunas na linha.  
  
 [Criando colunas de incremento automático](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Descreve como uma coluna pode ser definida para incrementar automaticamente valores numéricos para garantir um valor de coluna exclusivo por linha.  
  
 [Definindo chaves primárias](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Descreve como especificar a chave primária de uma tabela de uma ou mais **DataColumn** objetos.  
  
 [Restrições de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Descreve como definir a chave estrangeira e restrições exclusivas para colunas em uma tabela.  
  
## <a name="see-also"></a>Consulte também  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
