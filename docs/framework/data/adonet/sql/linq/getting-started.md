---
title: Guia de Introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 506257c13bbaada98dffa9d3a15c834037c1d971
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155227"
---
# <a name="getting-started"></a>Guia de Introdução
Usando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você pode usar o [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] tecnologia para acessar o SQL bancos de dados exatamente como você acessaria uma coleção em memória.  
  
 Por exemplo, o objeto `nw` no código a seguir é criado para representar o banco de dados `Northwind`, a tabela `Customers` é destinada, as linhas são filtradas para `Customers` de `London` e uma cadeia de caracteres de `CompanyName` é selecionada para recuperação.  
  
 Quando o loop é executado, a coleção de valores de `CompanyName` é recuperada.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Próximas etapas  
 Para obter alguns exemplos adicionais, incluindo a inserção e atualização, consulte [o que você pode fazer com LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).  
  
 Em seguida, tente alguns tutoriais e explicações passo a passo para ter uma experiência prática de uso do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Ver [aprendendo com explicações passo a passo](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
 Finalmente, Aprenda como começar a usar em seus próprios [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto lendo [etapas típicas para usar o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Consulte também

- [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [Introdução ao LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq.md)
- [Introdução ao LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Modelo de objeto LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
