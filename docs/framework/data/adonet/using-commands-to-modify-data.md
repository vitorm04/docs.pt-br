---
title: Usar os comandos para modificar dados
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: e2f61dbf74f28d026ae91a2bc8f5bb78530ffeac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177248"
---
# <a name="using-commands-to-modify-data"></a>Usar os comandos para modificar dados

Usando um provedor de dados .NET Framework, você pode executar procedimentos armazenados ou instruções de linguagem de definição de dados (por exemplo, CREATE TABLE e alterar coluna) para executar a manipulação de esquema em um banco de dados ou catálogo. Esses comandos não retornam linhas como uma consulta, portanto, o objeto **Command** fornece um **ExecuteNonQuery** para processá-los.  
  
 Além de usar o **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para processar instruções SQL que modificam dados, mas que não retornam linhas, como INSERT, Update e Delete.  
  
 Embora as linhas não sejam retornadas pelo método **ExecuteNonQuery** , os parâmetros de entrada e saída e os valores de retorno podem ser passados e retornados por meio da coleção de **parâmetros** do objeto de **comando** .  
  
## <a name="in-this-section"></a>Nesta seção  

 [Atualizando dados em uma fonte de dados](updating-data-in-a-data-source.md)  
 Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dado.  
  
 [Executar operações de catálogo](performing-catalog-operations.md)  
 Descreve como executar comandos que modificam o esquema de banco de dados.  
  
## <a name="see-also"></a>Veja também

- [Recuperando e modificando dados no ADO.NET](retrieving-and-modifying-data.md)
- [Comandos e parâmetros](commands-and-parameters.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
