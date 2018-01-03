---
title: 'Como: Representa colunas computadas'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 42afded36f6006f369dfddb7ed3a51598b3fc33a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-computed-columns"></a>Como: Representa colunas computadas
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para representar uma coluna cujo conteúdo é o resultado do cálculo.  
  
 Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não suporta colunas computadas como chaves primárias.  
  
### <a name="to-represent-a-computed-column"></a>Para representar uma coluna computado  
  
1.  Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
2.  Atribuir uma representação de cadeia de caracteres de fórmula à propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> .  
  
## <a name="see-also"></a>Consulte também  
 [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Como personalizar classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
