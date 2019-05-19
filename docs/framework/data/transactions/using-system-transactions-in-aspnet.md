---
title: Usar System.Transactions no ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 866d7b69fa6c18f6edfb48655b213e140a095a28
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880229"
---
# <a name="using-systemtransactions-in-aspnet"></a>Usar System.Transactions no ASP.NET
Este tópico descreve como você pode usar com êxito <xref:System.Transactions> dentro de um aplicativo ASP.NET.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Habilitar DistributedTransactionPermission no ASP.NET  
 <xref:System.Transactions> dá suporte a chamadores parcialmente confiáveis e é marcado com o **AllowPartiallyTrustedCallers** atributo (APTCA). Níveis de confiança para <xref:System.Transactions> são definidos com base nos tipos de recursos (por exemplo, memória do sistema, recursos compartilhados de todo o processo, recursos de todo o sistema e outros recursos), que <xref:System.Transactions> expõe e o nível de confiança deve ser necessária para acessar esses recursos. Em um ambiente de confiança parcial, um assembly de confiança total não pode usar somente as transações dentro do domínio de aplicativo (nesse caso, o único recurso que está sendo protegido é a memória do sistema), a menos que ele recebe o <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission> é solicitada sempre que o gerenciamento de transações é escalonado para ser gerenciado pelo Microsoft Distributed Transaction coordenador (MSDTC). Esse tipo de cenário usa recursos de todo o processo e especialmente um recurso global, que é o espaço reservado no log do MSDTC. Um exemplo dessa utilização é uma Web front-end para um banco de dados ou um aplicativo que usa um banco de dados como parte dos serviços que ele fornece.  
  
 ASP.NET tem seu próprio conjunto de níveis de confiança e associa um conjunto específico de permissões esses níveis de confiança por meio de arquivos de política. Para obter mais informações, consulte [níveis de confiança do ASP.NET e arquivos de política](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). Quando você instala o SDK do Windows inicialmente, nenhum dos arquivos de política padrão do ASP.NET estão associados a <xref:System.Transactions.DistributedTransactionPermission>. Dessa forma, quando sua transação em um aplicativo ASP.NET é escalonada para ser gerenciado pelo MSDTC, o escalonamento falhará com um <xref:System.Security.SecurityException> após exigindo a <xref:System.Transactions.DistributedTransactionPermission>. Para habilitar o escalonamento de bloqueios de transação em um ambiente de confiança parcial do ASP.NET, você deve conceder a <xref:System.Transactions.DistributedTransactionPermission> em que os níveis de confiança padrão mesmo que as de <xref:System.Data.SqlClient.SqlClientPermission>. Você pode configurar seu próprio arquivo de nível e a diretiva de confiança personalizadas para dar suporte a isso ou você pode modificar os arquivos de política padrão, que são **Web_hightrust** e **Web_mediumtrust**.  
  
 Para modificar os arquivos de política, adicione uma **SecurityClass** elemento para **DistributedTransactionPermission** para o **SecurityClasses** elemento sob o  **PolicyLevel** elemento e adicione um correspondente **IPermission** elemento sob o ASP.NET **NamedPermissionSet** para System. Transactions. O arquivo de configuração a seguir demonstra isso.  
  
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
  
 Para obter mais informações sobre a política de segurança do ASP.NET, consulte [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).  
  
## <a name="dynamic-compilation"></a>Compilação dinâmica  
 Se você deseja importar e usar <xref:System.Transactions> em um aplicativo ASP.NET que é compilado dinamicamente no access, você deve colocar uma referência para o <xref:System.Transactions> assembly no arquivo de configuração. Especificamente, a referência deve ser adicionada sob a **compilação**/**assemblies** seção da raiz padrão **Web. config** arquivo de configuração, ou um arquivo de configuração de um aplicativo Web específico. O exemplo a seguir demonstra isso.  
  
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
  
 Para obter mais informações, consulte [adicione o elemento para assemblies de compilação (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).  
  
## <a name="see-also"></a>Consulte também

- [Níveis de confiança do ASP.NET e arquivos de política](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Escalonamento de gerenciamento de transações](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
