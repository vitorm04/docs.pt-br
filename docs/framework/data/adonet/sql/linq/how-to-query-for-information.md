---
title: 'Como: consultar informações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793540"
---
# <a name="how-to-query-for-information"></a>Como: consultar informações
As consultas em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usam a mesma sintaxe que consultas em [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. A única diferença é que os objetos referenciados [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em consultas são mapeados para elementos em um banco de dados. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento.  
  
 Alguns recursos de consultas [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] podem precisar de atenção especial em aplicativos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Para obter mais informações, consulte [conceitos de consulta](query-concepts.md).  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir solicita uma lista de clientes de Londres. Neste exemplo, `Customers` é uma tabela no banco de dados de exemplo Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Criando o modelo de objeto](creating-the-object-model.md)
- [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)
- [Consultando o banco de dados](querying-the-database.md)
