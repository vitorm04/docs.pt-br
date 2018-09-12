---
title: DataSets tipados
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 68721bcdbce6bf6d3279d6018ce6bc48d65c55a3
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700265"
---
# <a name="typed-datasets"></a>DataSets tipados
Juntamente com acesso de associação tardia por meio de valores com variáveis fracamente tipadas, o <xref:System.Data.DataSet> fornece acesso a dados por meio de uma metáfora fortemente tipada. Tabelas e colunas que fazem parte do **conjunto de dados** podem ser acessadas usando nomes amigáveis e variáveis fortemente tipadas.  
  
 Tipado **DataSet** é uma classe que deriva de uma **conjunto de dados**. Como tal, herda todos os eventos, métodos e propriedades de um **conjunto de dados**. Além disso, um tipado **conjunto de dados** fornece propriedades, eventos e métodos com rigidez de tipos. Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção. Além da leitura aprimorada do código, com um tipo **conjunto de dados** também permite que o código do Visual Studio .NET editor preencher linhas automaticamente conforme você digita.  
  
 Além disso, fortemente tipada **conjunto de dados** fornece acesso aos valores como o tipo correto no tempo de compilação. Com fortemente tipado **conjunto de dados**, erros de incompatibilidade de tipo são capturados quando o código é compilado em vez de no tempo de execução.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerando conjuntos de dados fortemente tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 Descreve como criar e usar fortemente tipado **conjunto de dados**.  
  
 [Anotando DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 Descreve como anotar o esquema XSD (linguagem) de definição de esquema XML usado para gerar um com rigidez de tipos **DataSet**, para dar aos **conjunto de dados** nomes amigáveis de elementos sem alterar o esquema subjacente.  
  
## <a name="see-also"></a>Consulte também  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
