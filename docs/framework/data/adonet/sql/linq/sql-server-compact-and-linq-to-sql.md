---
title: SQL Server Compact e LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792538"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact e LINQ to SQL
SQL Server Compact é o banco de dados padrão instalado com o Visual Studio. Para obter mais informações, consulte [usando SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Este tópico descreve as principais diferenças de uso, configuração, conjuntos de recursos e escopo de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suporte.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Características do SQL Server Compact com relação ao LINQ to SQL  
 Por padrão, o SQL Server Compact é instalado para todas as edições do Visual Studio e, portanto, está disponível no computador de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]desenvolvimento para uso com o. Mas a implantação de um aplicativo que usa SQL Server Compact [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e difere disso para um aplicativo SQL Server. O SQL Server Compact não faz parte do .NET Framework e, portanto, deve ser empacotado com o aplicativo ou ser baixado separadamente do site da Microsoft.  
  
 Observe as seguintes características:  
  
- O SQL Server Compact é empacotado como uma DLL que pode ser usada em arquivos de banco de dados (extensão .sdf) diretamente.  
  
- SQL Server Compact é executado no mesmo processo que o aplicativo cliente. A eficiência da comunicação com o SQL Server Compact pode, portanto, ser significativamente maior do que a comunicação com SQL Server. Por outro lado, SQL Server Compact requer interoperabilidade entre código gerenciado e não gerenciado com seus custos de atendedor.  
  
- O tamanho da DLL de SQL Server Compact é pequeno. Esse recurso reduz o tamanho total do aplicativo.  
  
- O tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e a ferramenta de linha de comando SQLMetal dão suporte ao SQL Server Compact.  
  
- O Object Relational Designer não oferece suporte a SQL Server Compact.  
  
## <a name="feature-set"></a>Conjunto de recursos  
 O conjunto de recursos SQL Server Compact é muito mais simples do que o conjunto de recursos de SQL Server das seguintes maneiras que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podem afetar os aplicativos:  
  
- O SQL Server Compact não dá suporte a procedimentos armazenados ou exibições.  
  
- O SQL Server Compact dá suporte apenas um subconjunto dos tipos de dados e funções SQL.  
  
- O SQL Server Compact dá suporte apenas a um subconjunto de construções SQL.  
  
- O SQL Server Compact fornece somente um otimizador mínimo. É possível que algumas consultas possam atingir o tempo limite.  
  
- O SQL Server Compact não dá suporte a confiança parcial.  
  
## <a name="see-also"></a>Consulte também

- [Referência](reference.md)
