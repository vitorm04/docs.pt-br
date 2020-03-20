---
title: Habilitando e desabilitando o IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048571"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="5d9db-102">Habilitando e desabilitando o IPv6</span><span class="sxs-lookup"><span data-stu-id="5d9db-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="5d9db-103">Para usar o protocolo IPv6, verifique se você está executando uma versão do sistema operacional que dá suporte ao IPv6 e se o sistema operacional e as classes de rede estão configuradas corretamente.</span><span class="sxs-lookup"><span data-stu-id="5d9db-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="5d9db-104">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="5d9db-104">Configuration Steps</span></span>  
 <span data-ttu-id="5d9db-105">A tabela a seguir lista várias configurações</span><span class="sxs-lookup"><span data-stu-id="5d9db-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="5d9db-106">Sistema operacional habilitado para IPv6?</span><span class="sxs-lookup"><span data-stu-id="5d9db-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="5d9db-107">Classes de rede habilitadas para IPv6?</span><span class="sxs-lookup"><span data-stu-id="5d9db-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="5d9db-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d9db-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="5d9db-109">Não</span><span class="sxs-lookup"><span data-stu-id="5d9db-109">No</span></span>|<span data-ttu-id="5d9db-110">Não</span><span class="sxs-lookup"><span data-stu-id="5d9db-110">No</span></span>|<span data-ttu-id="5d9db-111">Pode analisar endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="5d9db-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="5d9db-112">Não</span><span class="sxs-lookup"><span data-stu-id="5d9db-112">No</span></span>|<span data-ttu-id="5d9db-113">Sim</span><span class="sxs-lookup"><span data-stu-id="5d9db-113">Yes</span></span>|<span data-ttu-id="5d9db-114">Pode analisar endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="5d9db-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="5d9db-115">Sim</span><span class="sxs-lookup"><span data-stu-id="5d9db-115">Yes</span></span>|<span data-ttu-id="5d9db-116">Não</span><span class="sxs-lookup"><span data-stu-id="5d9db-116">No</span></span>|<span data-ttu-id="5d9db-117">Pode analisar endereços IPv6 e resolver endereços IPv6 usando métodos de resolução de nomes não marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="5d9db-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="5d9db-118">Sim</span><span class="sxs-lookup"><span data-stu-id="5d9db-118">Yes</span></span>|<span data-ttu-id="5d9db-119">Sim</span><span class="sxs-lookup"><span data-stu-id="5d9db-119">Yes</span></span>|<span data-ttu-id="5d9db-120">Pode analisar e resolver endereços IPv6 usando todos os métodos, incluindo aqueles marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="5d9db-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="5d9db-121">Lembre-se de que, para habilitar o suporte ao IPv6 em todas as classes no namespace System.Net, é necessário modificar o arquivo de configuração do computador ou o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d9db-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="5d9db-122">O arquivo de configuração de um aplicativo tem precedência sobre o arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="5d9db-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="5d9db-123">Para obter um exemplo de como modificar o arquivo de configuração do computador, *machine.config*, para habilitar o suporte ao IPv6, consulte [Como modificar o arquivo de configuração do computador para habilitar o suporte ao IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="5d9db-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="5d9db-124">Além disso, verifique se o suporte ao IPv6 está habilitado no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5d9db-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="5d9db-125">O .NET Framework tem uma opção de configuração definida em um arquivo de configuração da seguinte maneira</span><span class="sxs-lookup"><span data-stu-id="5d9db-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="5d9db-126">Para o .NET Framework versão 1.1 e anterior, o valor da opção de configuração **ipv6 enabled** especifica se os membros da classe <xref:System.Net.Dns?displayProperty=nameWithType> retornam endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="5d9db-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="5d9db-127">Para o .NET Framework versão 2.0 e posterior, se o Windows der suporte ao IPv6, os membros da classe <xref:System.Net.Dns?displayProperty=nameWithType>, (por exemplo, o método <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>), retornarão endereços IPv6 com uma limitação.</span><span class="sxs-lookup"><span data-stu-id="5d9db-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="5d9db-128">Os membros obsoletos do DNS <xref:System.Net.Dns?displayProperty=nameWithType> (por exemplo, o método <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lerão e reconhecerão o valor no arquivo de configuração para a configuração ipv6 enabled.</span><span class="sxs-lookup"><span data-stu-id="5d9db-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9db-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="5d9db-129">See also</span></span>

- [<span data-ttu-id="5d9db-130">Protocolo da Internet Versão 6</span><span class="sxs-lookup"><span data-stu-id="5d9db-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="5d9db-131">Soquetes</span><span class="sxs-lookup"><span data-stu-id="5d9db-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="5d9db-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5d9db-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="5d9db-133">\<ipv6 elemento> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="5d9db-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
