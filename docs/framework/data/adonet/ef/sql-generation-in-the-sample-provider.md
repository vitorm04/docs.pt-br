---
title: Geração SQL no provedor exemplo
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: b2397570bb5f312aa6a3955a76234bde508fcc6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505493"
---
# <a name="sql-generation-in-the-sample-provider"></a>Geração SQL no provedor exemplo
O [provedor de exemplo do Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstra os novos componentes de provedores de dados ADO.NET que dão suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.  
  
 O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.  
  
## <a name="in-this-section"></a>Nesta seção  
 Esta seção inclui os seguintes tópicos:  
  
 [Arquitetura e design](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [Passo a passo: Geração SQL](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Consulte também
- [Geração de SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
