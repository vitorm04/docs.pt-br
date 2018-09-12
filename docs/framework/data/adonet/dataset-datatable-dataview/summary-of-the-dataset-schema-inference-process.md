---
title: Resumo do processo de inferência de esquema de conjunto de dados
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1583d5232a3dd483bbe2a6fa0b1bc8a3ae6a659f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700486"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Resumo do processo de inferência de esquema de conjunto de dados
O processo de inferência primeiro determina, do documento XML, quais elementos serão inferidos como tabelas. Do XML restante, o processo de inferência determina as colunas para essas tabelas. Para tabelas aninhadas, gera o processo de inferência de tipos aninhados <xref:System.Data.DataRelation> e <xref:System.Data.ForeignKeyConstraint> objetos.  
  
 A seguir está um breve resumo de regras de inferência:  
  
-   Elementos que têm atributos são inferidos como tabelas.  
  
-   Elementos que têm elementos filho são inferidos como tabelas.  
  
-   Elementos que se repetem são inferidos como uma única tabela.  
  
-   Se o elemento de documento ou raiz, tem nenhum atributo e nenhum elemento filho que seria inferido como colunas, ele será inferido como um <xref:System.Data.DataSet>. Caso contrário, o elemento do documento é inferido como uma tabela.  
  
-   Atributos são inferidos como colunas.  
  
-   Elementos que não têm atributos ou elementos filho e que não se repetem, são inferidos como colunas.  
  
-   Para elementos que são inferidos como tabelas aninhadas dentro de outros elementos que também sejam inferidos como tabelas, um aninhado **DataRelation** é criada entre as duas tabelas. Uma coluna de chave primária, novo chamada **TableName_Id** é adicionado para ambas as tabelas e usado pela **DataRelation**. Um **ForeignKeyConstraint** é criada entre as duas tabelas usando o **TableName_Id** coluna.  
  
-   Para elementos que são inferidos como tabelas e que contêm texto, mas que nenhum elemento filho, uma nova coluna chamada **TableName_Text** é criado para o texto de cada um dos elementos. Se um elemento é inferido como uma tabela e tem o texto, mas também tem elementos filho, o texto será ignorado.  
  
## <a name="see-also"></a>Consulte também  
 [Derivando a estrutura relacional do DataSet do esquema XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Carregando informações de esquema de conjunto de dados de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
