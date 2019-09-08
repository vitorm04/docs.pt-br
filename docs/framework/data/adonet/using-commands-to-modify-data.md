---
title: Usar os comandos para modificar dados
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780565"
---
# <a name="using-commands-to-modify-data"></a>Usar os comandos para modificar dados
Usando um provedor de dados .NET Framework, você pode executar procedimentos armazenados ou instruções de linguagem de definição de dados (por exemplo, CREATE TABLE e alterar coluna) para executar a manipulação de esquema em um banco de dados ou catálogo. Esses comandos não retornam linhas como uma consulta, portanto, o objeto **Command** fornece um **ExecuteNonQuery** para processá-los.  
  
 Além de usar o **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para processar instruções SQL que modificam dados, mas que não retornam linhas, como INSERT, Update e Delete.  
  
 Embora as linhas não sejam retornadas pelo método **ExecuteNonQuery** , os parâmetros de entrada e saída e os valores de retorno podem ser passados e retornados por meio da coleção de **parâmetros** do objeto de **comando** .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Atualizando dados em uma fonte de dados](updating-data-in-a-data-source.md)  
 Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dado.  
  
 [Executando operações de catálogo](performing-catalog-operations.md)  
 Descreve como executar comandos que modificam o esquema de banco de dados.  
  
## <a name="see-also"></a>Consulte também

- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [Comandos e parâmetros](commands-and-parameters.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
