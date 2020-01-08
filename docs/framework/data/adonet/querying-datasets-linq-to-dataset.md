---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634775"
---
# <a name="querying-datasets-linq-to-dataset"></a>Consultando DataSets (LINQ to DataSet)
Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta. Formular consultas com LINQ to DataSet é semelhante ao uso de LINQ (consulta integrada à linguagem) em relação a outras fontes de dados habilitadas para LINQ. No entanto, lembre-se de que, ao usar consultas LINQ em um objeto <xref:System.Data.DataSet>, você está consultando uma enumeração de objetos <xref:System.Data.DataRow> em vez de uma enumeração de um tipo personalizado. Isso significa que você pode usar qualquer um dos membros da classe <xref:System.Data.DataRow> em suas consultas LINQ. Isso permite que você crie consultas sofisticadas e complexas.  
  
 Assim como acontece com outras implementações do LINQ, você pode criar LINQ to DataSet consultas em duas formas diferentes: sintaxe de expressão de consulta e sintaxe de consulta baseada em método. Você pode usar sintaxe de expressão de consulta ou sintaxe de consulta baseada em método para executar consultas em tabelas únicas em um <xref:System.Data.DataSet>, em várias tabelas em uma <xref:System.Data.DataSet>ou em tabelas em um <xref:System.Data.DataSet>tipado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Consultas de tabela única](single-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em uma única tabela.  
  
 [Consultas de tabela cruzada](cross-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em tabelas cruzadas.  
  
 [Consultando DataSets tipados](querying-typed-datasets.md)  
 Descreve como consultar objetos <xref:System.Data.DataSet> tipados.  
  
## <a name="see-also"></a>Veja também

- [Exemplos de LINQ to DataSet](linq-to-dataset-examples.md)
- [Carregar dados para um conjunto de dados](loading-data-into-a-dataset.md)
