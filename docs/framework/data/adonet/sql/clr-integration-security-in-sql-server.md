---
title: "Segurança da integração CLR no SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: aa211005f13fca2c55ff693a12b3e37629e39ad3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="0ca3d-102">Segurança da integração CLR no SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ca3d-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="0ca3d-103">Microsoft SQL Server fornece a integração do componente de tempo de execução (CLR) de linguagem comum do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="0ca3d-104">Integração CLR permite que você grave procedimentos armazenados, disparadores, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e streaming funções com valor de tabela, usando qualquer linguagem do .NET Framework, como o Microsoft Visual Basic .NET ou o Microsoft Visual c#.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="0ca3d-105">O CLR oferece suporte a um modelo de segurança denominado segurança de acesso ao código (CAS) para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="0ca3d-106">Nesse modelo, as permissões são concedidas a assemblies com base na evidência fornecida pelo código nos metadados.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="0ca3d-107">SQL Server integra-se o modelo de segurança com base em usuário do SQL Server com o modelo de segurança baseada em acesso de código do CLR.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0ca3d-108">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="0ca3d-108">External Resources</span></span>  
 <span data-ttu-id="0ca3d-109">Para obter mais informações sobre a integração de CLR com o SQL Server, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="0ca3d-110">Recurso</span><span class="sxs-lookup"><span data-stu-id="0ca3d-110">Resource</span></span>|<span data-ttu-id="0ca3d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ca3d-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="0ca3d-112">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="0ca3d-112">Code Access Security</span></span>](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="0ca3d-113">Contém tópicos que descrevem o CAS no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="0ca3d-114">Segurança da integração CLR</span><span class="sxs-lookup"><span data-stu-id="0ca3d-114">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=59998)|<span data-ttu-id="0ca3d-115">Discute o modelo de segurança para código gerenciado em execução dentro do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0ca3d-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ca3d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ca3d-116">See Also</span></span>  
 <span data-ttu-id="0ca3d-117">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0ca3d-117">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 [<span data-ttu-id="0ca3d-118">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ca3d-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="0ca3d-119">Integração do Common Language Runtime ao SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ca3d-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 <span data-ttu-id="0ca3d-120">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0ca3d-120">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
