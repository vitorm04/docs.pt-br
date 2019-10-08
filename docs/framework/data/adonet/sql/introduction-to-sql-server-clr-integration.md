---
title: Introdução à Integração do SQL Server CLR
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 76c6fb4cb37807f286f1f1f2aeedbdea6c74fe38
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002139"
---
# <a name="introduction-to-sql-server-clr-integration"></a>Introdução à Integração do SQL Server CLR
O CLR (Common Language Runtime) é o coração do Microsoft .NET Framework e fornece o ambiente de execução para todo o código do .NET Framework. O código que é executado dentro do CLR é conhecido como código gerenciado. O CLR fornece várias funções e serviços necessários para a execução do programa, incluindo a compilação just-in-time (JIT), alocação e gerenciamento de memória, imposição de segurança de tipo, manipulação de exceção, gerenciamento de segmento e segurança.  
  
 Com o CLR hospedado no Microsoft SQL Server (chamado de integração de CLR), você pode criar procedimentos armazenados, gatilhos, funções definidas pelo usuário, tipos definidos pelo usuário e agregados definidos pelo usuário no código gerenciado. Como o código gerenciado compila para código nativo antes de execução, você pode obter aumentos significativos de desempenho em alguns cenários.  
  
 O código gerenciado usa CAS (segurança de acesso do código), links de código e domínios de aplicativo para impedir que os assemblies executem determinadas operações. O SQL Server usa CAS para ajudar a proteger o código gerenciado e evitar o comprometimento do sistema operacional ou servidor de banco de dados.  
  
 Esta seção é destinada para fornecer somente as informações suficientes para começar a programar com a integração de CLR do SQL Server, e não para ser abrangente. Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
- [Visão geral da integração CLR (Common Language Runtime)](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Habilitando a integração de CLR  
 O recurso de integração do CLR (Common Language Runtime) está desativado por padrão no Microsoft SQL Server e deve ser habilitado para usar os objetos que são implementados usando a integração de CLR. Para habilitar a integração de CLR usando Transact-SQL, use a opção `clr enabled` do procedimento armazenado `sp_configure` conforme mostrado:  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Você pode desabilitar a integração de CLR configurando a opção `clr enabled` como 0. Quando você desabilita a integração de CLR, o SQL Server para de executar todas rotinas de CLR e descarrega todos os domínios de aplicativo.  
  
 Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
- [Habilitando a integração CLR](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Implantando um assembly de CLR  
 Uma vez que os métodos de CLR foram testados e verificados no servidor de teste, eles podem ser distribuídos para servidores de produção usando um script de implantação. O script de implantação pode ser gerado manualmente ou usando o SQL Server Management Studio. Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1. [Implantando objetos de banco de dados CLR](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Segurança de integração de CLR  
 O modelo de segurança de integração do Microsoft SQL Server com o CLR (Common Language Runtime) do Microsoft .NET Framework gerencia e protege o acesso entre diferentes tipos de objetos CLR e não CLR que são executados no SQL Server. Esses objetos podem ser chamados por uma instrução Transact-SQL ou outro objeto CLR que é executado no servidor.  
  
 Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
- [Segurança de integração CLR](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Depurando um assembly de CLR  
 O Microsoft SQL Server fornece suporte para depurar o Transact-SQL e objetos CLR (Common Language Runtime) no banco de dados. Depurar funciona entre linguagens: os usuários podem entrar perfeitamente em objetos CLR de Transact-SQL e vice-versa.  
  
 Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
- [Depurando objetos de banco de dados CLR](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Consulte também

- [Segurança de acesso do código e o ADO.NET](../code-access-security.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
