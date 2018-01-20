---
title: SQL Server Compact e LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24f620319cd469538cf4454be7caffececdf9213
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact e LINQ to SQL
SQL Server Compact é o banco de dados padrão instalado com o Visual Studio. Para obter mais informações, consulte [PAVE sobre usando o SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Este tópico descreve as principais diferenças no uso, configuração, conjuntos de recursos e escopo de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suporte.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Características do SQL Server Compact com relação ao LINQ to SQL  
 Por padrão, o SQL Server Compact é instalado para todos os [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] edições e, portanto, está disponível no computador de desenvolvimento para uso com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Mas a implantação de um aplicativo que usa o SQL Server Compact e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] difere de um [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] aplicativo. O SQL Server Compact não faz parte do .NET Framework e, portanto, deve ser empacotado com o aplicativo ou ser baixado separadamente do site da Microsoft.  
  
 Observe as seguintes características:  
  
-   O SQL Server Compact é empacotado como uma DLL que pode ser usada em arquivos de banco de dados (extensão .sdf) diretamente.  
  
-   SQL Server Compact é executado no mesmo processo que o aplicativo cliente. A eficiência de comunicação com o SQL Server Compact, portanto, pode ser significativamente maior do que se comunicar com [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]. Por outro lado, o SQL Server Compact exigem interoperabilidade entre código gerenciado e com os seus custos atendente.  
  
-   O tamanho da DLL do SQL Server Compact é pequeno. Esse recurso reduz o tamanho total do aplicativo.  
  
-   O tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e a ferramenta de linha de comando SQLMetal dão suporte ao SQL Server Compact.  
  
-   O [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] não dá suporte ao SQL Server Compact.  
  
## <a name="feature-set"></a>Conjunto de recursos  
 O conjunto de recursos do SQL Server Compact é muito mais simples do que o conjunto de recursos do [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] das seguintes maneiras que podem afetar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos:  
  
-   O SQL Server Compact não dá suporte a procedimentos armazenados ou exibições.  
  
-   O SQL Server Compact dá suporte apenas um subconjunto dos tipos de dados e funções SQL.  
  
-   O SQL Server Compact dá suporte apenas a um subconjunto de construções SQL.  
  
-   O SQL Server Compact fornece somente um otimizador mínimo. É possível que algumas consultas podem atingir o tempo limite.  
  
-   O SQL Server Compact não dá suporte a confiança parcial.  
  
## <a name="see-also"></a>Consulte também  
 [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
