---
title: SQL Server Compact e LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 4385dc10d36e1f175fa52a8821401b2a9bc9bd31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697264"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact e LINQ to SQL
SQL Server Compact é o banco de dados padrão instalado com o Visual Studio. Para obter mais informações, consulte [PAVE failover usando o SQL Server Compact (Visual Studio)](https://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Este tópico descreve as principais diferenças em uso, configuração, conjuntos de recursos e escopo de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dão suporte.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Características do SQL Server Compact com relação ao LINQ to SQL  
 Por padrão, o SQL Server Compact está instalado para todas as edições do Visual Studio e, portanto, está disponível no computador de desenvolvimento para uso com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Mas a implantação de um aplicativo que usa o SQL Server Compact e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] difere daquele para um aplicativo do SQL Server. O SQL Server Compact não faz parte do .NET Framework e, portanto, deve ser empacotado com o aplicativo ou ser baixado separadamente do site da Microsoft.  
  
 Observe as seguintes características:  
  
-   O SQL Server Compact é empacotado como uma DLL que pode ser usada em arquivos de banco de dados (extensão .sdf) diretamente.  
  
-   O SQL Server Compact é executado no mesmo processo que o aplicativo cliente. A eficiência de comunicação com o SQL Server Compact, portanto, pode ser significativamente maior do que se comunicando com o SQL Server. Por outro lado, o SQL Server Compact requer a interoperabilidade entre código gerenciado e com os custos de atendimento.  
  
-   O tamanho da DLL do SQL Server Compact é pequeno. Esse recurso reduz o tamanho total do aplicativo.  
  
-   O tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e a ferramenta de linha de comando SQLMetal dão suporte ao SQL Server Compact.  
  
-   O [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] não dá suporte ao SQL Server Compact.  
  
## <a name="feature-set"></a>Conjunto de recursos  
 O conjunto de recursos do SQL Server Compact é muito mais simples do que o conjunto de recursos do SQL Server das seguintes maneiras que podem afetar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos:  
  
-   O SQL Server Compact não dá suporte a procedimentos armazenados ou exibições.  
  
-   O SQL Server Compact dá suporte apenas um subconjunto dos tipos de dados e funções SQL.  
  
-   O SQL Server Compact dá suporte apenas a um subconjunto de construções SQL.  
  
-   O SQL Server Compact fornece somente um otimizador mínimo. É possível que algumas consultas atinjam o tempo limite.  
  
-   O SQL Server Compact não dá suporte a confiança parcial.  
  
## <a name="see-also"></a>Consulte também
- [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
