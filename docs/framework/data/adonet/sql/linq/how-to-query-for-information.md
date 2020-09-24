---
title: 'Como: consultar informações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166398"
---
# <a name="how-to-query-for-information"></a>Como: consultar informações

As consultas em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usam a mesma sintaxe que as consultas no LINQ. A única diferença é que os objetos referenciados em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consultas são mapeados para elementos em um banco de dados. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento.  
  
 Alguns recursos das consultas do LINQ podem precisar de atenção especial em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos. Para obter mais informações, consulte [conceitos de consulta](query-concepts.md).  
  
## <a name="example"></a>Exemplo  

 A consulta a seguir solicita uma lista de clientes de Londres. Neste exemplo, `Customers` é uma tabela no banco de dados de exemplo Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Criando o modelo de objeto](creating-the-object-model.md)
- [Baixar bancos de dados de amostra](downloading-sample-databases.md)
- [Consultando o banco de dados](querying-the-database.md)
