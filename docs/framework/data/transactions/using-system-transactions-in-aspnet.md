---
title: Usando System. Transactions no ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 7b73ec970776f39a0c056e2a706d4818cda6cd72
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534537"
---
# <a name="using-systemtransactions-in-aspnet"></a>Usando System. Transactions no ASP.NET
Este tópico descreve como você pode usar com êxito <xref:System.Transactions> dentro de um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo.  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Habilitar DistributedTransactionPermission no ASP.NET  
 <xref:System.Transactions> dá suporte a chamadores parcialmente confiáveis e é marcado com o **AllowPartiallyTrustedCallers** atributo (APTCA). Níveis de confiança para <xref:System.Transactions> são definidos com base nos tipos de recursos (por exemplo, memória do sistema, recursos compartilhados de todo o processo, recursos de todo o sistema e outros recursos), que <xref:System.Transactions> expõe e o nível de confiança deve ser necessária para acessar esses recursos. Em um ambiente de confiança parcial, um assembly de confiança total não pode usar somente as transações dentro do domínio de aplicativo (nesse caso, o único recurso que está sendo protegido é a memória do sistema), a menos que ele recebe o <xref:System.Transactions.DistributedTransactionPermission>.  
  
 <xref:System.Transactions.DistributedTransactionPermission>é solicitada sempre que o gerenciamento de transações será escalonado para ser gerenciado por Microsoft Distributed Transaction coordenador (MSDTC). Esse tipo de cenário usa recursos de todo o processo e especialmente um recurso global, que é o espaço reservado no log do MSDTC. Um exemplo dessa utilização é uma Web front-end para um banco de dados ou um aplicativo que usa um banco de dados como parte dos serviços que ele fornece.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]tem seu próprio conjunto de níveis de confiança e associa um conjunto específico de permissões esses níveis de confiança por meio de arquivos de política. Para obter mais informações, consulte [níveis de confiança do ASP.NET e arquivos de política](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1). Quando você instala o SDK do Windows, nenhum padrão inicialmente [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] arquivos de política associados a <xref:System.Transactions.DistributedTransactionPermission>. Assim, quando sua transação em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo será escalonado para ser gerenciado pelo MSDTC, o escalonamento falhará com um <xref:System.Security.SecurityException> após exigindo a <xref:System.Transactions.DistributedTransactionPermission>. Para habilitar o escalonamento de transação em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ambiente de confiança parcial, você deve conceder a <xref:System.Transactions.DistributedTransactionPermission> nos níveis de confiança padrão mesmo que os do <xref:System.Data.SqlClient.SqlClientPermission>. Você pode configurar seu próprio arquivo de nível e a diretiva de confiança personalizadas para dar suporte a isso ou você pode modificar os arquivos de política padrão, que são **Web_hightrust** e **Web_mediumtrust**.  
  
 Para modificar os arquivos de política, adicione uma **SecurityClass** elemento para **DistributedTransactionPermission** para o **SecurityClasses** elemento sob o  **PolicyLevel** elemento e adicione um correspondente **IPermission** elemento sob o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** para System. Transactions. O arquivo de configuração a seguir demonstra isso.  
  
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
  
 Para obter mais informações sobre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] política de segurança, consulte [securityPolicy Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## <a name="dynamic-compilation"></a>Compilação dinâmica  
 Se você deseja importar e usar <xref:System.Transactions> em uma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo é compilado dinamicamente no access, você deve colocar uma referência para o <xref:System.Transactions> assembly no arquivo de configuração. Especificamente, a referência deve ser adicionada sob a **compilação**/**assemblies** seção da raiz padrão **Web. config** arquivo de configuração, ou um arquivo de configuração de um aplicativo Web específico. O exemplo a seguir demonstra isso.  
  
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
  
 Para obter mais informações, consulte [adicione o elemento para assemblies de compilação (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## <a name="see-also"></a>Consulte também  
 [Níveis de confiança do ASP.NET e arquivos de política](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [securityPolicy Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [Escalonamento de gerenciamento de transações](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
