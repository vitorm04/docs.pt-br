---
title: Procedimentos armazenados CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: ca0fd2d33f0ad56c96fb63530e6ba3f7f7890f81
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450356"
---
# <a name="clr-stored-procedures"></a>Procedimentos armazenados CLR
Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares. Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.  
  
> [!NOTE]
> O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#. Você deve especificar para passar o parâmetro por referência e aplicar o atributo \<out () > para representar um parâmetro de saída, como no seguinte:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Para obter informações mais detalhadas, consulte a versão da [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.
  
 **Documentação do SQL Server**

1. [Procedimentos armazenados CLR](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))  
  
## <a name="see-also"></a>Confira também

- [Criando objetos SQL Server 2005 no código gerenciado](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
