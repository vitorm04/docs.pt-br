---
title: "Execução lado a lado no ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60da108fd77465917cdfe1dd744067eac9e88d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="side-by-side-execution-in-adonet"></a>Execução lado a lado no ADO.NET
Execução lado a lado no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é a capacidade de executar um aplicativo em um computador que tem várias versões do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] instalado exclusivamente usando a versão para a qual o aplicativo foi compilado. Para obter informações detalhadas sobre a configuração de execução lado a lado, consulte [execução lado a lado](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Um aplicativo compilado com uma versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pode ser executado em uma versão diferente de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. No entanto, recomendamos que você compila uma versão do aplicativo para cada versão instalada do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]e executá-los separadamente. Em qualquer cenário, você deve estar ciente das alterações no [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] entre as versões que podem afetar a compatibilidade ou compatibilidade com versões anteriores do seu aplicativo.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Compatibilidade e compatibilidade com versões anteriores  
 Compatibilidade com versões posteriores significa que um aplicativo pode ser compilado com uma versão anterior do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], mas ainda será executado com êxito em uma versão posterior do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]o código escrito para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 é compatível com versões posteriores.  
  
 Compatibilidade com versões anteriores significa que um aplicativo é compilado para uma versão mais recente do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], mas continua a ser executado em versões anteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sem qualquer perda de funcionalidade. Obviamente, isso não será o caso dos recursos introduzidos em uma nova versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>O .NET Framework Data Provider para ODBC  
 Começando com a versão 1.1, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para ODBC (<xref:System.Data.Odbc>) é incluído como parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. O provedor de dados ODBC está disponível para [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] desenvolvedores versão 1.0 como um Web baixar a partir de [Data Access and Storage Developer Center](http://go.microsoft.com/fwlink/?linkid=4173). O namespace baixado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para ODBC é **Microsoft.Data.Odbc**.  
  
 Se você tiver um aplicativo desenvolvido para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0 que usa o provedor de dados ODBC para se conectar à sua fonte de dados e você deseja executar o aplicativo no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 ou posterior, você deve atualizar o namespace do ODBC provedor de dados **data**. Você então deve recompilá-lo para a versão mais recente do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Se você tiver um aplicativo desenvolvido para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0 ou posterior que usa o provedor de dados ODBC para se conectar à sua fonte de dados e você deseja executar o aplicativo no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, você deve baixar o provedor de dados ODBC e instalar -o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sistema versão 1.0. Você deve alterar o namespace para o provedor de dados ODBC **Microsoft.Data.Odbc**e recompilar o aplicativo para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>O provedor de dados .NET Framework para Oracle  
 Começando com a versão 1.1, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle (<xref:System.Data.OracleClient>) é incluído como parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. O provedor de dados está disponível para [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] desenvolvedores versão 1.0 como um Web baixar a partir de [Data Access and Storage Developer Center](http://go.microsoft.com/fwlink/?linkid=4173).  
  
 Se você tiver um aplicativo desenvolvido para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0 ou posterior que usa o provedor de dados para se conectar à sua fonte de dados e você deseja executar o aplicativo no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, você deve baixar o provedor de dados e instalá-lo no < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  sistema versão 1.0.  
  
## <a name="code-access-security"></a>Segurança de acesso do código  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) são necessárias para executar com a permissão FullTrust. Qualquer tentativa de usar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados de k do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0 em uma zona com menos de causas de permissão FullTrust um <xref:System.Security.SecurityException>.  
  
 No entanto, começando com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0, todos os [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados podem ser usados em regiões parcialmente confiáveis. Além disso, um novo recurso de segurança foi adicionado para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1. Esse recurso permite que você restrinja quais cadeias de caracteres podem ser usadas em uma zona de segurança específico de conexão. Você também pode desabilitar o uso de senhas em branco para uma zona de segurança específico. Para obter mais informações, consulte [Segurança de acesso do código e ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Como cada instalação do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tem um arquivo de config separado, não há nenhum problema de compatibilidade com configurações de segurança. No entanto, se seu aplicativo depende dos recursos de segurança adicionais de [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] incluídos no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 ou posterior, você não poderá distribuí-lo para um sistema de versão 1.0.  
  
## <a name="sqlcommand-execution"></a>Execução de SqlCommand  
 Começando com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1, a maneira que <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> executa comandos os dados de origem foi alterada.  
  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> executada todos os comandos no contexto da **sp_executesql** procedimento armazenado. Como resultado, os comandos que afetam o estado de conexão (por exemplo, SET NOCOUNT ON), se aplicam somente à execução do comando atual. O estado da conexão não é modificado para os comandos subsequentes executados enquanto a conexão estiver aberta.  
  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 e posteriores, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> só executa um comando no contexto da **sp_executesql** procedimento armazenado se o comando contiver parâmetros, que fornece um benefício de desempenho. Como resultado, se um comando que afetam o estado da conexão é incluído em um comando sem parâmetros, modifica o estado da conexão para todos os comandos subsequentes executadas enquanto a conexão estiver aberta.  
  
 Considere o seguinte lote de comandos executados em uma chamada para <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 e versões posterior, NOCOUNT permanecerá ON para os comandos subsequentes executados enquanto a conexão estiver aberta. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, NOCOUNT está apenas ON para a execução do comando atual.  
  
 Essa alteração pode afetar a compatibilidade com versões anteriores e de avanço do seu aplicativo, se você depender do comportamento de <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> para uma versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Para aplicativos que são executados em versões anteriores e posteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], você pode escrever seu código para certificar-se de que o comportamento é o mesmo, independentemente da versão que você está executando no. Se você quiser garantir que um comando modifica o estado da conexão para todos os comandos subsequentes, é recomendável que você execute o comando usando <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Se você quiser garantir que um comando não modifique a conexão para todos os comandos subsequentes, é recomendável que você inclua os comandos para redefinir o estado de conexão em seu comando. Por exemplo:  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
