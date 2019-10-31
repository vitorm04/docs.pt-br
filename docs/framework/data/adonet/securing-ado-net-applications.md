---
title: Protegendo aplicativos ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c99c56afca475caafe32cca3f50d074fb82e0e00
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196723"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="132a5-102">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="132a5-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="132a5-103">Escrever um aplicativo seguro do ADO.NET envolve mais do que evitar armadilhas comuns de codificação como não validar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="132a5-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="132a5-104">Um aplicativo que acessa dados tem vários pontos possíveis de falha que um invasor pode explorar para recuperar, manipular ou destruir dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="132a5-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="132a5-105">Portanto, é importante compreender todos os aspectos de segurança, do processo de modelagem de ameaças durante a fase de projeto do aplicativo até a sua eventual implantação e manutenção contínua.</span><span class="sxs-lookup"><span data-stu-id="132a5-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="132a5-106">O .NET Framework fornece muitas classes, serviços e ferramentas úteis para administrar e proteger os aplicativos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="132a5-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="132a5-107">O CLR (Common Language Runtime) fornece um ambiente de tipo seguro no qual o código será executado, com CAS (segurança de acesso ao código) para restringir mais as permissões do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="132a5-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="132a5-108">Seguir práticas de codificação segura de acesso a dados limita o dano que pode ser infligido por um invasor potencial.</span><span class="sxs-lookup"><span data-stu-id="132a5-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="132a5-109">Escrever código seguro não protege contra buracos na segurança autoinfligidos ao trabalhar com recursos não gerenciados como bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="132a5-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="132a5-110">A maioria dos bancos de dados do servidor, como SQL Server, têm seus próprios sistemas de segurança, que melhoram a segurança quando implementados corretamente.</span><span class="sxs-lookup"><span data-stu-id="132a5-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="132a5-111">No entanto, até mesmo uma fonte de dados com um sistema de segurança robusto pode ser prejudicada em um ataque se não estiver configurada adequadamente.</span><span class="sxs-lookup"><span data-stu-id="132a5-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="132a5-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="132a5-112">In This Section</span></span>  
 [<span data-ttu-id="132a5-113">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="132a5-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="132a5-114">Fornece recomendações para criar aplicativos seguros do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="132a5-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="132a5-115">Acesso seguro a dados</span><span class="sxs-lookup"><span data-stu-id="132a5-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="132a5-116">Descreve como trabalhar com dados de uma fonte de dados segura.</span><span class="sxs-lookup"><span data-stu-id="132a5-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="132a5-117">Aplicativos cliente seguros</span><span class="sxs-lookup"><span data-stu-id="132a5-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="132a5-118">Descreve as considerações de segurança para aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="132a5-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="132a5-119">Segurança de acesso do código e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="132a5-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="132a5-120">Descreve como o CAS pode ajudar a proteger o código do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="132a5-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="132a5-121">Também descreve como trabalhar com confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="132a5-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="132a5-122">Privacidade e segurança de dados</span><span class="sxs-lookup"><span data-stu-id="132a5-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="132a5-123">Descreve as opções de criptografia para aplicativos ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="132a5-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="132a5-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="132a5-124">Related Sections</span></span>  
 <span data-ttu-id="132a5-125">[SQL Server Security](./sql/sql-server-security.md) (Segurança do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="132a5-125">[SQL Server Security](./sql/sql-server-security.md)</span></span>  
 <span data-ttu-id="132a5-126">Descreve os recursos de segurança do SQL Server da perspectiva de um desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="132a5-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="132a5-127">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="132a5-127">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="132a5-128">Descreve a segurança para aplicativos do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="132a5-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="132a5-129">Security</span><span class="sxs-lookup"><span data-stu-id="132a5-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="132a5-130">Contém links para tópicos que descrevem todos os aspectos de segurança no .NET.</span><span class="sxs-lookup"><span data-stu-id="132a5-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="132a5-131">[Ferramentas de segurança](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="132a5-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="132a5-132">As ferramentas do .NET Framework para proteger e administrar a política de segurança.</span><span class="sxs-lookup"><span data-stu-id="132a5-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="132a5-133">[Recursos para criar aplicativos seguros](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="132a5-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="132a5-134">Fornece links para tópicos para criar aplicativos seguros.</span><span class="sxs-lookup"><span data-stu-id="132a5-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="132a5-135">Bibliografia de segurança</span><span class="sxs-lookup"><span data-stu-id="132a5-135">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="132a5-136">Fornece links para recursos externos disponíveis online e em cópia impressa.</span><span class="sxs-lookup"><span data-stu-id="132a5-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132a5-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="132a5-137">See also</span></span>

- [<span data-ttu-id="132a5-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="132a5-138">ADO.NET</span></span>](index.md)
- <span data-ttu-id="132a5-139">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="132a5-139">[ADO.NET Overview](ado-net-overview.md)</span></span>
