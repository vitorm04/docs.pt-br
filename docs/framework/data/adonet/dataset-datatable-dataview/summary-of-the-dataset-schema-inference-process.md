---
title: Resumo do processo de inferência de esquema de DataSet
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 5266d08212e5259bd5b242a70d61e29ad9008006
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203249"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Resumo do processo de inferência de esquema de DataSet
O processo de inferência determina primeiro, a partir do documento XML, quais elementos serão inferidos como tabelas. Do XML restante, o processo de inferência determina as colunas para essas tabelas. Para tabelas aninhadas, o processo de inferência <xref:System.Data.ForeignKeyConstraint> gera objetos aninhados <xref:System.Data.DataRelation> e.  
  
 Veja a seguir um breve resumo das regras de inferência:  
  
- Elementos que têm atributos são inferidos como tabelas.  
  
- Elementos que têm elementos filho são inferidos como tabelas.  
  
- Elementos que se repetem são inferidos como uma única tabela.  
  
- Se o documento, ou raiz, o elemento não tiver atributos e nenhum elemento filho que fosse inferido como colunas, ele será inferido como um <xref:System.Data.DataSet>. Caso contrário, o elemento Document é inferido como uma tabela.  
  
- Os atributos são inferidos como colunas.  
  
- Elementos que não têm atributos ou elementos filho, e que não se repetem, são inferidos como colunas.  
  
- Para elementos que são inferidos como tabelas aninhadas dentro de outros elementos que também são inferidos como tabelas, uma DataRelation aninhada é criada entre as duas tabelas. Uma nova coluna de chave primária chamada **TableName_Id** é adicionada às duas tabelas e usada pela **DataRelation**. Um **ForeignKeyConstraint** é criado entre as duas tabelas usando a coluna **TableName_Id** .  
  
- Para elementos que são inferidos como tabelas e que contêm texto, mas não têm elementos filho, uma nova coluna chamada **TableName_Text** é criada para o texto de cada um dos elementos. Se um elemento for inferido como uma tabela e tiver texto, mas também tiver elementos filho, o texto será ignorado.  
  
## <a name="see-also"></a>Consulte também

- [Derivando a estrutura relacional do DataSet do esquema XML](inferring-dataset-relational-structure-from-xml.md)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [Carregando informações de esquema de conjunto de dados de XML](loading-dataset-schema-information-from-xml.md)
- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
