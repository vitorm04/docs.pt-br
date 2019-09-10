---
title: Geração SQL no provedor exemplo
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854322"
---
# <a name="sql-generation-in-the-sample-provider"></a>Geração SQL no provedor exemplo
O [provedor de exemplo Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstra os novos componentes dos provedores de dados ADO.NET que dão suporte ao Entity Framework.  Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.  
  
 O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.  
  
## <a name="in-this-section"></a>Nesta seção  
 Esta seção inclui os seguintes tópicos:  
  
 [Arquitetura e design](architecture-and-design.md)  
  
 [Passo a passo: Geração de SQL](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Consulte também

- [Geração de SQL](sql-generation.md)
