---
title: "Geração SQL no provedor exemplo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58a49f7bf5d385466810a3c59bda748ef66d5840
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation-in-the-sample-provider"></a>Geração SQL no provedor exemplo
O [provedor do Entity Framework exemplo](http://go.microsoft.com/fwlink/?LinkId=180616) demonstra os novos componentes ADO.NET de provedores de dados que oferecem suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.  
  
 O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.  
  
## <a name="in-this-section"></a>Nesta seção  
 Esta seção inclui os seguintes tópicos:  
  
 [Arquitetura e Design](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [Passo a passo: Geração de SQL](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Consulte também  
 [Geração SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
