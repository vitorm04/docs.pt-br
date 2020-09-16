---
title: Usar System.Transactions no ASP.NET
description: Use System. Transactions dentro de um aplicativo ASP.NET. Habilite as permissões de transação distribuída e trabalhe com a compilação dinâmica.
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: f8bf485389d9633a37201f6293fab8ccae7cf26f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544460"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="0ded3-104">Usar System.Transactions no ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0ded3-104">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="0ded3-105">Este tópico descreve como você pode usar com êxito <xref:System.Transactions> dentro de um aplicativo ASP.net.</span><span class="sxs-lookup"><span data-stu-id="0ded3-105">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="0ded3-106">Habilitar DistributedTransactionPermission no ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0ded3-106">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="0ded3-107"><xref:System.Transactions> dá suporte a chamadores parcialmente confiáveis e é marcado com o `AllowPartiallyTrustedCallers` atributo (APTCA).</span><span class="sxs-lookup"><span data-stu-id="0ded3-107"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="0ded3-108">Os níveis de confiança para <xref:System.Transactions> são definidos com base nos tipos de recursos (por exemplo, memória do sistema, recursos compartilhados de todo o processo, recursos de todo o sistema e outros recursos) que <xref:System.Transactions> expõe e o nível de confiança que deve ser necessário para acessar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="0ded3-108">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="0ded3-109">Em um ambiente de confiança parcial, um assembly de confiança total não pode usar somente as transações dentro do domínio de aplicativo (nesse caso, o único recurso que está sendo protegido é a memória do sistema), a menos que ele recebe o <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="0ded3-109">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="0ded3-110"><xref:System.Transactions.DistributedTransactionPermission> é exigido sempre que o gerenciamento de transações é escalonado para ser gerenciado pelo Microsoft Coordenador de Transações Distribuídas (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="0ded3-110"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="0ded3-111">Esse tipo de cenário usa recursos de todo o processo e especialmente um recurso global, que é o espaço reservado no log do MSDTC.</span><span class="sxs-lookup"><span data-stu-id="0ded3-111">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="0ded3-112">Um exemplo dessa utilização é uma Web front-end para um banco de dados ou um aplicativo que usa um banco de dados como parte dos serviços que ele fornece.</span><span class="sxs-lookup"><span data-stu-id="0ded3-112">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="0ded3-113">O ASP.NET tem seu próprio conjunto de níveis de confiança e associa um conjunto específico de permissões a esses níveis de confiança por meio de arquivos de política.</span><span class="sxs-lookup"><span data-stu-id="0ded3-113">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="0ded3-114">Para obter mais informações, consulte [níveis de confiança e arquivos de política do ASP.net](/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0ded3-114">For more information, see [ASP.NET Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="0ded3-115">Ao instalar inicialmente o SDK do Windows, nenhum dos arquivos de política ASP.NET padrão está associado ao <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="0ded3-115">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="0ded3-116">Dessa forma, quando sua transação em um aplicativo ASP.NET é escalonada para ser gerenciada pelo MSDTC, o escalonamento falha com um <xref:System.Security.SecurityException> após exigir o <xref:System.Transactions.DistributedTransactionPermission> .</span><span class="sxs-lookup"><span data-stu-id="0ded3-116">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="0ded3-117">Para habilitar o escalonamento de transações em um ambiente de confiança parcial ASP.NET, você deve conceder o <xref:System.Transactions.DistributedTransactionPermission> nos mesmos níveis de confiança padrão que os do <xref:System.Data.SqlClient.SqlClientPermission> .</span><span class="sxs-lookup"><span data-stu-id="0ded3-117">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="0ded3-118">Você pode configurar seu próprio nível de confiança personalizado e arquivo de política para dar suporte a isso, ou pode modificar os arquivos de política padrão, que são **Web_hightrust.config** e **Web_mediumtrust.config**.</span><span class="sxs-lookup"><span data-stu-id="0ded3-118">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="0ded3-119">Para modificar os arquivos de política, adicione um `SecurityClass` elemento para `DistributedTransactionPermission` ao `SecurityClasses` elemento sob o `PolicyLevel` elemento e adicione um `IPermission` elemento correspondente sob o ASP.NET `NamedPermissionSet` para System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="0ded3-119">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="0ded3-120">O arquivo de configuração a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="0ded3-120">The following configuration file demonstrates this.</span></span>

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

 <span data-ttu-id="0ded3-121">Para obter mais informações sobre a política de segurança do ASP.NET, consulte [elemento SecurityPolicy (esquema de configurações do ASP.net)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0ded3-121">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="0ded3-122">Compilação dinâmica</span><span class="sxs-lookup"><span data-stu-id="0ded3-122">Dynamic Compilation</span></span>
 <span data-ttu-id="0ded3-123">Se você quiser importar e usar <xref:System.Transactions> o em um aplicativo ASP.NET que é compilado dinamicamente no Access, você deve inserir uma referência ao <xref:System.Transactions> assembly no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0ded3-123">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="0ded3-124">Especificamente, a referência deve ser adicionada na `compilation/assemblies` seção do arquivo de configuração de **Web.config** raiz padrão ou em um arquivo de configuração de aplicativo Web específico.</span><span class="sxs-lookup"><span data-stu-id="0ded3-124">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="0ded3-125">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="0ded3-125">The following example demonstrates this.</span></span>

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

 <span data-ttu-id="0ded3-126">Para obter mais informações, consulte [Adicionar elemento para assemblies para compilação (esquema de configurações de ASP.net)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0ded3-126">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ded3-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ded3-127">See also</span></span>

- <span data-ttu-id="0ded3-128">[ASP.NET de níveis de confiança e arquivos de política](/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ded3-128">[ASP.NET Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="0ded3-129">[Elemento securityPolicy (esquema de configurações de ASP.NET)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ded3-129">[securityPolicy Element (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="0ded3-130">Escalonamento de gerenciamento de transações</span><span class="sxs-lookup"><span data-stu-id="0ded3-130">Transaction Management Escalation</span></span>](transaction-management-escalation.md)
