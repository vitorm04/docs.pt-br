---
title: Integração do Common Language Runtime do SQL
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d9fe0f03c88584607c6bc38fcbcff3f9424fd40c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183020"
---
# <a name="sql-server-common-language-runtime-integration"></a>Integração do Common Language Runtime do SQL

O SQL Server 2005 introduziu a integração do componente CLR do .NET Framework para Microsoft Windows. Isso significa que você pode gravar procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções de streaming com valor de tabela, usando qualquer linguagem do .NET Framework, incluindo o Microsoft Visual Basic .NET e o Microsoft Visual C#. O namespace <xref:Microsoft.SqlServer.Server> contém um conjunto de APIs de modo que o código gerenciado possa interagir com o ambiente do Microsoft SQL Server.  
  
 Esta seção descreve os recursos e os comportamentos específicos para a integração de CLR e as extensões específicas no processo do SQL Server para o ADO.NET.  
  
 Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente. Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **Documentação do SQL Server**  
  
1. [Conceitos de programação da Integração CLR (Common Language Runtime)](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a>Nesta seção  

 [Introdução à Integração do SQL Server CLR](introduction-to-sql-server-clr-integration.md)  
 Fornece uma introdução à Integração do SQL Server CLR. Fornece links para tópicos adicionais.  
  
 [Funções do CLR definidas pelo usuário](clr-user-defined-functions.md)  
 Descreve como implementar e usar os vários tipos de funções CLR: com valor de tabela, escalares e funções de agregação definida pelo usuário.  
  
 [Tipos definidos pelo usuário de CLR](clr-user-defined-types.md)  
 Descreve como implementar e usar tipos definidos pelo usuário CLR. Fornece links para tópicos adicionais.  
  
 [Procedimentos armazenados CLR](clr-stored-procedures.md)  
 Descreve como implementar e usar procedimentos armazenados CLR. Fornece links para tópicos adicionais.  
  
 [Gatilhos de CLR](clr-triggers.md)  
 Descreve como implementar e usar gatilhos CLR. Fornece links para tópicos adicionais.  
  
 [A conexão de contexto](the-context-connection.md)  
 Descreve a conexão de contexto.  
  
 [Comportamento específico do processo do SQL Server do ADO.NET](sql-server-in-process-specific-behavior-of-adonet.md)  
 Descreve as extensões específicas no processo do SQL Server para o ADO.NET, e a conexão de contexto. Fornece links para tópicos adicionais.  
  
## <a name="see-also"></a>Veja também

- [SQL Server e ADO.NET](index.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
