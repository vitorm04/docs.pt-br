---
title: Execução lado a lado no ADO.NET
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: 7435f64afa9ce45a29f4d0a537219f31968eb3f5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747269"
---
# <a name="side-by-side-execution-in-adonet"></a>Execução lado a lado no ADO.NET
Execução lado a lado na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é a capacidade de executar um aplicativo em um computador que tem várias versões do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] instalado, exclusivamente usando a versão para o qual o aplicativo foi compilado. Para obter informações detalhadas sobre como configurar a execução lado a lado, consulte [execução lado a lado](../../../../docs/framework/deployment/side-by-side-execution.md).  
  
 Um aplicativo compilado usando uma versão dos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pode executar em uma versão diferente de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. No entanto, recomendamos que você compilar uma versão do aplicativo para cada versão instalada do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]e executá-los separadamente. Em qualquer cenário, você deve estar ciente das alterações no [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] entre as versões que podem afetar a compatibilidade com versões posteriores ou compatibilidade com versões anteriores do seu aplicativo.  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>Compatibilidade com versões posteriores e compatibilidade com versões anteriores  
 Compatibilidade com versões significa que um aplicativo pode ser compilado com uma versão anterior da [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], mas ainda será executado com êxito em uma versão posterior do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] o código escrito para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 é compatível com versões posteriores.  
  
 Compatibilidade com versões anteriores significa que um aplicativo é compilado para uma versão mais recente do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], mas continua sendo executado em versões anteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sem qualquer perda de funcionalidade. Obviamente, isso não será o caso para recursos introduzidos em uma nova versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>O .NET Framework Data Provider para ODBC  
 Começando com a versão 1.1, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para ODBC (<xref:System.Data.Odbc>) está incluído como parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. O provedor de dados ODBC está disponível para [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] desenvolvedores versão 1.0 como uma Web baixar do [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173). O namespace para o baixado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para ODBC é **Microsoft.Data.Odbc**.  
  
 Se você tiver um aplicativo desenvolvido para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0 que usa o provedor de dados ODBC para se conectar à sua fonte de dados e você deseja executar o aplicativo a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 ou posterior, você deve atualizar o namespace do ODBC provedor de dados **System.Data.Odbc**. Você então deve recompilá-lo para a versão mais recente do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Se você tiver um aplicativo desenvolvido para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0 ou posterior que usa o provedor de dados ODBC para se conectar à sua fonte de dados e você deseja executar o aplicativo a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, você deve baixar o provedor de dados ODBC e instalar -na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sistema versão 1.0. Você deve alterar o namespace para o provedor de dados ODBC **Microsoft.Data.Odbc**e recompilar o aplicativo para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0.  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>O .NET Framework Data Provider for Oracle  
 Começando com a versão 1.1, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle (<xref:System.Data.OracleClient>) está incluído como parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. O provedor de dados está disponível para [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] desenvolvedores versão 1.0 como uma Web baixar do [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173).  
  
 Se você tiver um aplicativo desenvolvido para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0 ou posterior que usa o provedor de dados para se conectar à sua fonte de dados e você deseja executar o aplicativo a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, você deve baixar o provedor de dados e instalá-lo no < C4 > [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]  sistema de versão 1.0.  
  
## <a name="code-access-security"></a>Segurança de acesso do código  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0 (<xref:System.Data.SqlClient>, <xref:System.Data.OleDb>) são necessários para executar com a permissão FullTrust. Qualquer tentativa de usar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados k do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0 em uma zona com menos de causas de permissão FullTrust um <xref:System.Security.SecurityException>.  
  
 No entanto, começando com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0, todos os [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados podem ser usados em regiões parcialmente confiáveis. Além disso, um novo recurso de segurança foi adicionado para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedores de dados no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1. Esse recurso permite que você restrinja quais cadeias de caracteres podem ser usadas em uma zona de segurança específico de conexão. Você também pode desabilitar o uso de senhas em branco para uma zona de segurança específico. Para obter mais informações, consulte [Segurança de acesso do código e ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
 Porque cada instalação do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tem um arquivo separado do Security. config, não há problemas de compatibilidade com as configurações de segurança. No entanto, se seu aplicativo depende dos recursos de segurança adicional [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] incluídos no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 e posterior, você não poderá distribuí-lo para um sistema de versão 1.0.  
  
## <a name="sqlcommand-execution"></a>Execução de SqlCommand  
 Começando com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1, a maneira que <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> executa comandos em que os dados de origem foi alterada.  
  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> executada todos os comandos no contexto da **sp_executesql** procedimento armazenado. Como resultado, os comandos que afetam o estado da conexão (por exemplo, SET NOCOUNT ON), só se aplicam à execução do comando atual. O estado da conexão não será modificado de todos os comandos subsequentes executados enquanto a conexão está aberta.  
  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 e posterior, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> só executa um comando no contexto da **sp_executesql** procedimento armazenado se o comando contiver parâmetros, que fornece um benefício de desempenho. Como resultado, se um comando que afetam o estado da conexão estiver incluído em um comando sem parâmetros, ele modifica o estado da conexão para todos os comandos subsequentes executadas enquanto a conexão está aberta.  
  
 Considere o seguinte lote de comandos executados em uma chamada para <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 e posterior, NOCOUNT permanecerá Diante de todos os comandos subsequentes executados enquanto a conexão está aberta. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, NOCOUNT está apenas ON para a execução do comando atual.  
  
 Essa alteração pode afetar a compatibilidade retroativa e avançada do seu aplicativo se você depende do comportamento de <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> independentemente da versão dos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
 Para aplicativos que são executados em versões anteriores e posteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], você pode escrever seu código para certificar-se de que o comportamento é o mesmo, independentemente da versão que você estiver executando em. Se você quiser garantir que um comando modifica o estado da conexão para todos os comandos subsequentes, é recomendável que você execute o comando usando <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>. Se você quiser garantir que um comando não modifica a conexão para todos os comandos subsequentes, é recomendável que você inclua os comandos para redefinir o estado da conexão em seu comando. Por exemplo:  
  
```  
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
