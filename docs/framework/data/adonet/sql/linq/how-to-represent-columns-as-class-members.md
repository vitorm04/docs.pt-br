---
title: 'Como: Representa colunas como membros de classe'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 65d8e44d540f902012d6df6094e85cc70a5d9b1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-columns-as-class-members"></a>Como: Representa colunas como membros de classe
Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo a ser associado a um campo ou propriedade com uma coluna de banco de dados.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Para mapear um campo ou propriedade a uma coluna de base de dados  
  
-   Adicione o atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> à declaração de propriedade ou campo.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mapeia o campo de `CustomerID` na classe de `Customer` para a coluna de `CustomerID` na tabela de base de dados de `Customers` .  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Você não precisa especificar a propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> se o nome pode ser inferido. Se você não especificar um nome, o nome é presumido ser o mesmo nome que a propriedade ou do campo.  
  
## <a name="see-also"></a>Consulte também  
 [O modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Como personalizar classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
