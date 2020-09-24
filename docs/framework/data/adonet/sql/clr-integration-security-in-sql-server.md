---
title: Segurança da integração CLR no SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: e5d15b4e5ac36f7ecddf45179c65a60995a1a578
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147769"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="eddc3-102">Segurança da integração CLR no SQL Server</span><span class="sxs-lookup"><span data-stu-id="eddc3-102">CLR Integration Security in SQL Server</span></span>

<span data-ttu-id="eddc3-103">Microsoft SQL Server fornece a integração do componente Common Language Runtime (CLR) do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eddc3-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="eddc3-104">A integração CLR permite que você escreva procedimentos armazenados, gatilhos, tipos definidos pelo usuário, funções definidas pelo usuário, agregações definidas pelo usuário e funções com valor de tabela de streaming, usando qualquer linguagem de .NET Framework, como o Microsoft Visual Basic .NET ou o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="eddc3-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="eddc3-105">O CLR dá suporte a um modelo de segurança chamado CAS (segurança de acesso do código) para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eddc3-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="eddc3-106">Nesse modelo, as permissões são concedidas a assemblies com base nas evidências fornecidas pelo código nos metadados.</span><span class="sxs-lookup"><span data-stu-id="eddc3-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="eddc3-107">SQL Server integra o modelo de segurança baseado no usuário do SQL Server com o modelo de segurança baseado em acesso ao código do CLR.</span><span class="sxs-lookup"><span data-stu-id="eddc3-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="eddc3-108">Recursos externos</span><span class="sxs-lookup"><span data-stu-id="eddc3-108">External Resources</span></span>  

 <span data-ttu-id="eddc3-109">Para obter mais informações sobre a integração CLR com o SQL Server, consulte os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="eddc3-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="eddc3-110">Recurso</span><span class="sxs-lookup"><span data-stu-id="eddc3-110">Resource</span></span>|<span data-ttu-id="eddc3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="eddc3-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="eddc3-112">Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="eddc3-112">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="eddc3-113">Contém tópicos que descrevem CAS no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eddc3-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="eddc3-114">Segurança da integração CLR</span><span class="sxs-lookup"><span data-stu-id="eddc3-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="eddc3-115">Discute o modelo de segurança para execução de código gerenciado dentro de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eddc3-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eddc3-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="eddc3-116">See also</span></span>

- [<span data-ttu-id="eddc3-117">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="eddc3-117">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="eddc3-118">Cenários de Segurança de Aplicativo no SQL Server</span><span class="sxs-lookup"><span data-stu-id="eddc3-118">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="eddc3-119">Integração do Common Language Runtime do SQL</span><span class="sxs-lookup"><span data-stu-id="eddc3-119">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="eddc3-120">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="eddc3-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
