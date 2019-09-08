---
title: Procedimentos armazenados CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d2fde4fdcd5ab63906256d814256578b9baa9ecd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782503"
---
# <a name="clr-stored-procedures"></a>Procedimentos armazenados CLR
Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares. Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.  
  
> [!NOTE]
> O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#. Você deve especificar para passar o parâmetro por referência e aplicar o \<atributo out () > para representar um parâmetro de saída, como no seguinte:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Para obter informações mais detalhadas, consulte a versão da [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.
  
 **Documentação do SQL Server**

1. [Procedimentos armazenados CLR](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Consulte também

- [Criando objetos SQL Server 2005 no código gerenciado](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
