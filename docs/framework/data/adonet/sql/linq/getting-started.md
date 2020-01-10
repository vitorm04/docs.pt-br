---
title: Guia de Introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634684"
---
# <a name="getting-started"></a>Guia de Introdução
Usando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você pode usar a tecnologia LINQ para acessar bancos de dados SQL da mesma forma que acessaria uma coleção na memória.  
  
 Por exemplo, o objeto `nw` no código a seguir é criado para representar o banco de dados `Northwind`, a tabela `Customers` é destinada, as linhas são filtradas para `Customers` de `London` e uma cadeia de caracteres de `CompanyName` é selecionada para recuperação.  
  
 Quando o loop é executado, a coleção de valores de `CompanyName` é recuperada.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Próximas etapas  
 Para obter alguns exemplos adicionais, incluindo inserção e atualização, consulte [o que você pode fazer com LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Em seguida, tente alguns tutoriais e explicações passo a passo para ter uma experiência prática de uso do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Consulte [aprendendo por passo a passos](learning-by-walkthroughs.md).  
  
 Por fim, saiba como começar em seu próprio projeto de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lendo [as etapas típicas para usar LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Veja também

- [LINQ to SQL](index.md)
- [Introdução ao LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Introdução ao LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [O modelo de objeto LINQ to SQL](the-linq-to-sql-object-model.md)
