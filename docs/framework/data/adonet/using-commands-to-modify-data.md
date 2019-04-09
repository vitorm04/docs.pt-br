---
title: Usar os comandos para modificar dados
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102447"
---
# <a name="using-commands-to-modify-data"></a>Usar os comandos para modificar dados
Usando um provedor de dados .NET Framework, você pode executar os procedimentos armazenados ou dados instruções linguagem de definição (por exemplo, CREATE TABLE e ALTER COLUMN) para executar a manipulação de esquema em um banco de dados ou o catálogo. Esses comandos não retornam linhas, como faria com uma consulta, portanto, o **comando** objeto fornece um **ExecuteNonQuery** para processá-las.  
  
 Além de usar **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para instruções SQL de processo que modificam dados, mas que não retornam linhas, como INSERT, UPDATE e excluir.  
  
 Embora linhas não são retornadas pelo **ExecuteNonQuery** parâmetros de método, entrada e saída e valores retornados podem ser passados e retornados por meio de **parâmetros** coleção do **comando**  objeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Atualizando dados em uma fonte de dados](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dados.  
  
 [Executar operações de catálogo](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Descreve como executar comandos que modificam o esquema de banco de dados.  
  
## <a name="see-also"></a>Consulte também

- [Recuperando e modificando dados no ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
