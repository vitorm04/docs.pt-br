---
title: "Como modificar o arquivo de configuração do computador para habilitar o suporte a IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: 18
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a23a2690b0df30eaa815d0b321200af3a3403e5
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="2efb7-102">Como modificar o arquivo de configuração do computador para habilitar o suporte a IPv6</span><span class="sxs-lookup"><span data-stu-id="2efb7-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="2efb7-103">O exemplo de código a seguir mostra como modificar o arquivo de configuração do computador, *machine.config* para habilitar o suporte a IPv6.</span><span class="sxs-lookup"><span data-stu-id="2efb7-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="2efb7-104">O arquivo *machine.config* é armazenado na pasta *%Windir%\Microsoft.NET\Framework* no diretório em que o Windows foi instalado.</span><span class="sxs-lookup"><span data-stu-id="2efb7-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="2efb7-105">Há um outro arquivo *machine.config* nas pastas em *%Windir%\Microsoft.NET\Framework* para cada versão do .NET Framework instalada no computador (por exemplo, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="2efb7-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="2efb7-106">Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="2efb7-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="2efb7-107">Para o .NET Framework versão 1.1 e anterior, o valor da opção de configuração **ipv6 enabled** especifica se os membros da classe <xref:System.Net.Dns?displayProperty=fullName> retornam endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="2efb7-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=fullName> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="2efb7-108">Para o .NET Framework versão 2.0 e posteriores, se o Windows der suporte ao IPv6, todos os membros da classe <xref:System.Net.Dns?displayProperty=fullName>, (por exemplo, o método <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName>), retornarão endereços IPv6 com uma limitação.</span><span class="sxs-lookup"><span data-stu-id="2efb7-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=fullName> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="2efb7-109">Os membros obsoletos da classe <xref:System.Net.Dns?displayProperty=fullName> (por exemplo, o método <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName>) lerão e reconhecerão o valor no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2efb7-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=fullName> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2efb7-110">Para o .NET Framework versão 2.0 e posteriores, o IPv6 é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="2efb7-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="2efb7-111">Para o .NET Framework versão 1.1 e anteriores, o IPv6 é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="2efb7-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2efb7-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2efb7-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2efb7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2efb7-113">See Also</span></span>  
 <span data-ttu-id="2efb7-114">[Endereçamento IPv6](../../../docs/framework/network-programming/ipv6-addressing.md) </span><span class="sxs-lookup"><span data-stu-id="2efb7-114">[IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md) </span></span>  
 <span data-ttu-id="2efb7-115">[Esquema de configurações de rede](../../../docs/framework/configure-apps/file-schema/network/index.md) </span><span class="sxs-lookup"><span data-stu-id="2efb7-115">[Network Settings Schema](../../../docs/framework/configure-apps/file-schema/network/index.md) </span></span>  
 [<span data-ttu-id="2efb7-116">\<Elemento ipv6> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2efb7-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)

