---
title: Procedimentos armazenados CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 9b31d93c1ebc0af9aa8e41b3a4c328af62da7e23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230805"
---
# <a name="clr-stored-procedures"></a>Procedimentos armazenados CLR
Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares. Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.  
  
> [!NOTE]
>  O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#. Você deve especificar para passar o parâmetro por referência e aplicar o \<out () > atributo para representar um parâmetro de saída, da seguinte maneira:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Para obter mais informações, consulte a versão do [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.
  
 **Documentação do SQL Server**

1. [Procedimentos armazenados CLR](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Consulte também

- [Criando objetos do SQL Server 2005 em código gerenciado](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
