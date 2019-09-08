---
title: 'Como: executar comandos SQL diretamente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 3f28351a29915bebd698e00113bb05647d8412b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781989"
---
# <a name="how-to-directly-execute-sql-commands"></a>Como: executar comandos SQL diretamente
Presumindo uma conexão de <xref:System.Data.Linq.DataContext>, você pode usar o <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> para executar comandos SQL que não retornam objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz o SQL Server aumentar o UnitPrice em 1,00.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Executar consultas SQL diretamente](how-to-directly-execute-sql-queries.md)
- [Comunicação com o banco de dados](communicating-with-the-database.md)
