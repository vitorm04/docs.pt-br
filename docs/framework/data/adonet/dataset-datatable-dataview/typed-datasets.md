---
title: DataSets tipados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6ede928352c9e0f02f6ad4c27ce8f5347b868986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="typed-datasets"></a>DataSets tipados
Juntamente com acesso de associação tardia por meio de valores com variáveis fracamente tipadas, o <xref:System.Data.DataSet> fornece acesso a dados por meio de uma metáfora fortemente tipada. Tabelas e colunas que fazem parte do **DataSet** podem ser acessados usando nomes amigáveis e fortemente tipadas variáveis.  
  
 Um tipo **DataSet** é uma classe que deriva de um **conjunto de dados**. Como tal, ele herda todos os eventos, métodos e propriedades de um **conjunto de dados**. Além disso, um tipo **DataSet** fornece métodos com rigidez de tipos, propriedades e eventos. Isso significa que você pode acessar tabelas e colunas pelo nome, em vez de usar métodos baseados em coleção. Além de melhor legibilidade do código, com um tipo **DataSet** também permite que o código do Visual Studio .NET editor preencher linhas automaticamente conforme você digita.  
  
 Além disso, fortemente tipada **DataSet** fornece acesso a valores como o tipo correto em tempo de compilação. Com um fortemente tipada **conjunto de dados**, erros de incompatibilidade de tipo são detectados quando o código é compilado em vez de em tempo de execução.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerando conjuntos de dados fortemente tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 Descreve como criar e usar um fortemente tipada **conjunto de dados**.  
  
 [Anotando DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 Descreve como anotar o esquema de linguagem XSD de definição de esquema XML usado para gerar um fortemente tipada **DataSet**, fornecer **DataSet** nomes amigáveis de elementos sem alterar o esquema subjacente.  
  
## <a name="see-also"></a>Consulte também  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
