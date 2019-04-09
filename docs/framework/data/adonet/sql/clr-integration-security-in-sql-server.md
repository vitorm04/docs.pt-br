---
title: Segurança da integração CLR no SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 946401211d515df9ba5b9e38d7cfd10730973b64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165809"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="bbf8e-102">Segurança da integração CLR no SQL Server</span><span class="sxs-lookup"><span data-stu-id="bbf8e-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="bbf8e-103">Microsoft SQL Server fornece a integração do componente do common language runtime (CLR) do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="bbf8e-104">Integração CLR permite que você grave procedimentos armazenados, disparadores, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e streaming funções com valor de tabela, usando qualquer linguagem do .NET Framework, como o Microsoft Visual Basic .NET ou o Microsoft Visual c#.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="bbf8e-105">O CLR dá suporte a um modelo de segurança denominado segurança de acesso do código (CAS) para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="bbf8e-106">Nesse modelo, as permissões são concedidas a assemblies com base na evidência fornecida pelo código em metadados.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="bbf8e-107">SQL Server integra-se o modelo de segurança baseado em usuário do SQL Server com o modelo de segurança baseada em acesso de código do CLR.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="bbf8e-108">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="bbf8e-108">External Resources</span></span>  
 <span data-ttu-id="bbf8e-109">Para obter mais informações sobre a integração de CLR com o SQL Server, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="bbf8e-110">Recurso</span><span class="sxs-lookup"><span data-stu-id="bbf8e-110">Resource</span></span>|<span data-ttu-id="bbf8e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbf8e-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="bbf8e-112">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="bbf8e-112">Code Access Security</span></span>](../../../../../docs/framework/misc/code-access-security.md)|<span data-ttu-id="bbf8e-113">Contém tópicos que descrevem o CAS no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="bbf8e-114">Segurança de integração de CLR</span><span class="sxs-lookup"><span data-stu-id="bbf8e-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="bbf8e-115">Discute o modelo de segurança para código gerenciado em execução dentro do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bbf8e-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbf8e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbf8e-116">See also</span></span>

- [<span data-ttu-id="bbf8e-117">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bbf8e-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="bbf8e-118">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="bbf8e-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="bbf8e-119">Integração do Common Language Runtime do SQL</span><span class="sxs-lookup"><span data-stu-id="bbf8e-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="bbf8e-120">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bbf8e-120">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
