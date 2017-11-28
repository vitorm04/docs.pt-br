---
title: 'Como: Filtrar dados relacionados'
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
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f02b09cc5389a90ea42a0dd851579327972c20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-related-data"></a>Como: Filtrar dados relacionados
Use o método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> para especificar subpropriedades consultas para limitar a quantidade de dados recuperados.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limita `Orders` recuperado com aqueles que não foram enviados hoje. Essa abordagem, sem qualquer `Orders` deve ser recuperado mesmo que somente um subconjunto é desejado.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultando o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
