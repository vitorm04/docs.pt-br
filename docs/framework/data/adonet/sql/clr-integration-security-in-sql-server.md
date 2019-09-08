---
title: Segurança da integração CLR no SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794565"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="29da2-102">Segurança da integração CLR no SQL Server</span><span class="sxs-lookup"><span data-stu-id="29da2-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="29da2-103">Microsoft SQL Server fornece a integração do componente Common Language Runtime (CLR) do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29da2-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="29da2-104">A integração CLR permite que você escreva procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções com valor de tabela de streaming, usando qualquer linguagem de .NET Framework, como Microsoft Visual Basic .NET ou Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="29da2-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="29da2-105">O CLR dá suporte a um modelo de segurança chamado CAS (segurança de acesso do código) para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="29da2-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="29da2-106">Nesse modelo, as permissões são concedidas a assemblies com base nas evidências fornecidas pelo código nos metadados.</span><span class="sxs-lookup"><span data-stu-id="29da2-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="29da2-107">SQL Server integra o modelo de segurança baseado no usuário do SQL Server com o modelo de segurança baseado em acesso ao código do CLR.</span><span class="sxs-lookup"><span data-stu-id="29da2-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="29da2-108">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="29da2-108">External Resources</span></span>  
 <span data-ttu-id="29da2-109">Para obter mais informações sobre a integração CLR com o SQL Server, consulte os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="29da2-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="29da2-110">Recurso</span><span class="sxs-lookup"><span data-stu-id="29da2-110">Resource</span></span>|<span data-ttu-id="29da2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="29da2-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="29da2-112">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="29da2-112">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="29da2-113">Contém tópicos que descrevem CAS no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29da2-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="29da2-114">Segurança de integração CLR</span><span class="sxs-lookup"><span data-stu-id="29da2-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="29da2-115">Discute o modelo de segurança para execução de código gerenciado dentro de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29da2-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29da2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29da2-116">See also</span></span>

- <span data-ttu-id="29da2-117">[Securing ADO.NET Applications](../securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="29da2-117">[Securing ADO.NET Applications](../securing-ado-net-applications.md)</span></span>
- [<span data-ttu-id="29da2-118">Cenários de segurança do aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="29da2-118">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="29da2-119">Integração do Common Language Runtime ao SQL Server</span><span class="sxs-lookup"><span data-stu-id="29da2-119">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- <span data-ttu-id="29da2-120">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="29da2-120">[ADO.NET Overview](../ado-net-overview.md)</span></span>
