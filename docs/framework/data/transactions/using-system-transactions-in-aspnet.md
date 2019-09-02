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
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="dc913-102">Usar System.Transactions no ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc913-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="dc913-103">Este tópico descreve como você pode usar <xref:System.Transactions> com êxito dentro de um aplicativo ASP.net.</span><span class="sxs-lookup"><span data-stu-id="dc913-103">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="dc913-104">Habilitar DistributedTransactionPermission no ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc913-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="dc913-105"><xref:System.Transactions>dá suporte a chamadores parcialmente confiáveis e é marcado com o atributo **AllowPartiallyTrustedCallers** (APTCA).</span><span class="sxs-lookup"><span data-stu-id="dc913-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="dc913-106">Níveis de confiança para <xref:System.Transactions> são definidos com base nos tipos de recursos (por exemplo, memória do sistema, recursos compartilhados de todo o processo, recursos de todo o sistema e outros recursos), que <xref:System.Transactions> expõe e o nível de confiança deve ser necessária para acessar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="dc913-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="dc913-107">Em um ambiente de confiança parcial, um assembly de confiança total não pode usar somente as transações dentro do domínio de aplicativo (nesse caso, o único recurso que está sendo protegido é a memória do sistema), a menos que ele recebe o <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="dc913-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="dc913-108"><xref:System.Transactions.DistributedTransactionPermission>é exigido sempre que o gerenciamento de transações é escalonado para ser gerenciado pelo Microsoft Coordenador de Transações Distribuídas (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="dc913-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="dc913-109">Esse tipo de cenário usa recursos de todo o processo e especialmente um recurso global, que é o espaço reservado no log do MSDTC.</span><span class="sxs-lookup"><span data-stu-id="dc913-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="dc913-110">Um exemplo dessa utilização é uma Web front-end para um banco de dados ou um aplicativo que usa um banco de dados como parte dos serviços que ele fornece.</span><span class="sxs-lookup"><span data-stu-id="dc913-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 <span data-ttu-id="dc913-111">O ASP.NET tem seu próprio conjunto de níveis de confiança e associa um conjunto específico de permissões a esses níveis de confiança por meio de arquivos de política.</span><span class="sxs-lookup"><span data-stu-id="dc913-111">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="dc913-112">Para obter mais informações, consulte [níveis de confiança e arquivos de política do ASP.net](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc913-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="dc913-113">Ao instalar inicialmente o SDK do Windows, nenhum dos arquivos de política ASP.NET padrão está associado <xref:System.Transactions.DistributedTransactionPermission>ao.</span><span class="sxs-lookup"><span data-stu-id="dc913-113">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="dc913-114">Dessa forma, quando sua transação em um aplicativo ASP.net é escalonada para ser gerenciada pelo MSDTC, o escalonamento falha com um <xref:System.Security.SecurityException> após exigir o. <xref:System.Transactions.DistributedTransactionPermission></span><span class="sxs-lookup"><span data-stu-id="dc913-114">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="dc913-115">Para habilitar o escalonamento de transações em um ambiente de confiança parcial ASP.net, você deve <xref:System.Transactions.DistributedTransactionPermission> conceder o nos mesmos níveis de confiança padrão que <xref:System.Data.SqlClient.SqlClientPermission>os do.</span><span class="sxs-lookup"><span data-stu-id="dc913-115">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="dc913-116">Você pode configurar seu próprio nível de confiança personalizado e arquivo de política para dar suporte a isso, ou pode modificar os arquivos de política padrão, que são o **Web_hightrust. config** e o **web_mediumtrust. config**.</span><span class="sxs-lookup"><span data-stu-id="dc913-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="dc913-117">Para modificar os arquivos de política, adicione um elemento **SecurityClass** para **DistributedTransactionPermission** ao elemento **SecurityClasses** sob o elemento **PolicyLevel** e adicione um elemento **IPermission** correspondente em ASP.NET **NamedPermissionSet** para System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="dc913-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the ASP.NET **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="dc913-118">O arquivo de configuração a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="dc913-118">The following configuration file demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="dc913-119">Para obter mais informações sobre a política de segurança do ASP.NET, consulte [elemento SecurityPolicy (esquema de configurações do ASP.net)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc913-119">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="dc913-120">Compilação dinâmica</span><span class="sxs-lookup"><span data-stu-id="dc913-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="dc913-121">Se você quiser importar e usar <xref:System.Transactions> o <xref:System.Transactions> em um aplicativo ASP.NET que é compilado dinamicamente no Access, você deve inserir uma referência ao assembly no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dc913-121">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="dc913-122">Especificamente, a referência deve ser adicionada na seção**assemblies** de **compilação**/do arquivo de configuração **Web. config** de raiz padrão ou em um arquivo de configuração do aplicativo Web específico.</span><span class="sxs-lookup"><span data-stu-id="dc913-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="dc913-123">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="dc913-123">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="dc913-124">Para obter mais informações, consulte [Adicionar elemento para assemblies para compilação (esquema de configurações de ASP.net)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc913-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc913-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc913-125">See also</span></span>

- <span data-ttu-id="dc913-126">[ASP.NET de níveis de confiança e arquivos de política](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dc913-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="dc913-127">[Elemento securityPolicy (esquema de configurações de ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dc913-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="dc913-128">Escalonamento de gerenciamento de transações</span><span class="sxs-lookup"><span data-stu-id="dc913-128">Transaction Management Escalation</span></span>](transaction-management-escalation.md)
