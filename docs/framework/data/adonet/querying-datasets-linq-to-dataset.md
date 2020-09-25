---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: f42cd792772a4e2b9f24ea8f76ea588da10d9c51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184970"
---
# <a name="querying-datasets-linq-to-dataset"></a>Consultando DataSets (LINQ to DataSet)

Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta. Formular consultas com LINQ to DataSet é semelhante ao uso de LINQ (consulta integrada à linguagem) em relação a outras fontes de dados habilitadas para LINQ. No entanto, lembre-se de que, ao usar consultas LINQ em um <xref:System.Data.DataSet> objeto, você está consultando uma enumeração de <xref:System.Data.DataRow> objetos em vez de uma enumeração de um tipo personalizado. Isso significa que você pode usar qualquer um dos membros da <xref:System.Data.DataRow> classe em suas consultas LINQ. Isso permite que você crie consultas sofisticadas e complexas.  
  
 Assim como acontece com outras implementações do LINQ, você pode criar LINQ to DataSet consultas em duas formas diferentes: sintaxe de expressão de consulta e sintaxe de consulta baseada em método. Você pode usar sintaxe de expressão de consulta ou sintaxe de consulta baseada em método para executar consultas em tabelas únicas em um <xref:System.Data.DataSet> , em relação a várias tabelas em uma <xref:System.Data.DataSet> ou em tabelas em um tipo <xref:System.Data.DataSet> .  
  
## <a name="in-this-section"></a>Nesta seção  

 [Consultas de tabela única](single-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em uma única tabela.  
  
 [Consultas de tabela cruzada](cross-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em tabelas cruzadas.  
  
 [Consultando DataSets tipados](querying-typed-datasets.md)  
 Descreve como consultar objetos <xref:System.Data.DataSet> tipados.  
  
## <a name="see-also"></a>Veja também

- [LINQ para exemplos de DataSet](linq-to-dataset-examples.md)
- [Carregando dados em um DataSet](loading-data-into-a-dataset.md)
