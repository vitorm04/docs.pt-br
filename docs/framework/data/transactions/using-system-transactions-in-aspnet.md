---
title: Usar System.Transactions no ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: bfc75661ea538ac52b244e38eb10e6ae37a8fd62
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205830"
---
# <a name="using-systemtransactions-in-aspnet"></a>Usar System.Transactions no ASP.NET
Este tópico descreve como você pode usar <xref:System.Transactions> com êxito dentro de um aplicativo ASP.net.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Habilitar DistributedTransactionPermission no ASP.NET  
 <xref:System.Transactions>dá suporte a chamadores parcialmente confiáveis e é marcado com o atributo **AllowPartiallyTrustedCallers** (APTCA). Níveis de confiança para <xref:System.Transactions> são definidos com base nos tipos de recursos (por exemplo, memória do sistema, recursos compartilhados de todo o processo, recursos de todo o sistema e outros recursos), que <xref:System.Transactions> expõe e o nível de confiança deve ser necessária para acessar esses recursos. Em um ambiente de confiança parcial, um assembly de confiança total não pode usar somente as transações dentro do domínio de aplicativo (nesse caso, o único recurso que está sendo protegido é a memória do sistema), a menos que ele recebe o <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission>é exigido sempre que o gerenciamento de transações é escalonado para ser gerenciado pelo Microsoft Coordenador de Transações Distribuídas (MSDTC). Esse tipo de cenário usa recursos de todo o processo e especialmente um recurso global, que é o espaço reservado no log do MSDTC. Um exemplo dessa utilização é uma Web front-end para um banco de dados ou um aplicativo que usa um banco de dados como parte dos serviços que ele fornece.  
  
 O ASP.NET tem seu próprio conjunto de níveis de confiança e associa um conjunto específico de permissões a esses níveis de confiança por meio de arquivos de política. Para obter mais informações, consulte [níveis de confiança e arquivos de política do ASP.net](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Ao instalar inicialmente o SDK do Windows, nenhum dos arquivos de política ASP.NET padrão está associado <xref:System.Transactions.DistributedTransactionPermission>ao. Dessa forma, quando sua transação em um aplicativo ASP.net é escalonada para ser gerenciada pelo MSDTC, o escalonamento falha com um <xref:System.Security.SecurityException> após exigir o. <xref:System.Transactions.DistributedTransactionPermission> Para habilitar o escalonamento de transações em um ambiente de confiança parcial ASP.net, você deve <xref:System.Transactions.DistributedTransactionPermission> conceder o nos mesmos níveis de confiança padrão que <xref:System.Data.SqlClient.SqlClientPermission>os do. Você pode configurar seu próprio nível de confiança personalizado e arquivo de política para dar suporte a isso, ou pode modificar os arquivos de política padrão, que são o **Web_hightrust. config** e o **web_mediumtrust. config**.  
  
 Para modificar os arquivos de política, adicione um elemento **SecurityClass** para **DistributedTransactionPermission** ao elemento **SecurityClasses** sob o elemento **PolicyLevel** e adicione um elemento **IPermission** correspondente em ASP.NET **NamedPermissionSet** para System. Transactions. O arquivo de configuração a seguir demonstra isso.  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 Para obter mais informações sobre a política de segurança do ASP.NET, consulte [elemento SecurityPolicy (esquema de configurações do ASP.net)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).  
  
## <a name="dynamic-compilation"></a>Compilação dinâmica  
 Se você quiser importar e usar <xref:System.Transactions> o <xref:System.Transactions> em um aplicativo ASP.NET que é compilado dinamicamente no Access, você deve inserir uma referência ao assembly no arquivo de configuração. Especificamente, a referência deve ser adicionada na seção**assemblies** de **compilação**/do arquivo de configuração **Web. config** de raiz padrão ou em um arquivo de configuração do aplicativo Web específico. O exemplo a seguir demonstra isso.  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 Para obter mais informações, consulte [Adicionar elemento para assemblies para compilação (esquema de configurações de ASP.net)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).  
  
## <a name="see-also"></a>Consulte também

- [ASP.NET de níveis de confiança e arquivos de política](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [Elemento securityPolicy (esquema de configurações de ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Escalonamento de gerenciamento de transações](transaction-management-escalation.md)
