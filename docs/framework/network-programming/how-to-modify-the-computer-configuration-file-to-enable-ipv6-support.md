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
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Como modificar o arquivo de configuração do computador para habilitar o suporte a IPv6
O exemplo de código a seguir mostra como modificar o arquivo de configuração do computador, *machine.config* para habilitar o suporte a IPv6. O arquivo *machine.config* é armazenado na pasta *%Windir%\Microsoft.NET\Framework* no diretório em que o Windows foi instalado. Há um outro arquivo *machine.config* nas pastas em *%Windir%\Microsoft.NET\Framework* para cada versão do .NET Framework instalada no computador (por exemplo, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.  
  
 Para o .NET Framework versão 1.1 e anterior, o valor da opção de configuração **ipv6 enabled** especifica se os membros da classe <xref:System.Net.Dns?displayProperty=fullName> retornam endereços IPv6.  
  
 Para o .NET Framework versão 2.0 e posteriores, se o Windows der suporte ao IPv6, todos os membros da classe <xref:System.Net.Dns?displayProperty=fullName>, (por exemplo, o método <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName>), retornarão endereços IPv6 com uma limitação. Os membros obsoletos da classe <xref:System.Net.Dns?displayProperty=fullName> (por exemplo, o método <xref:System.Net.Dns.Resolve%2A?displayProperty=fullName>) lerão e reconhecerão o valor no arquivo de configuração.  
  
> [!NOTE]
>  Para o .NET Framework versão 2.0 e posteriores, o IPv6 é habilitado por padrão. Para o .NET Framework versão 1.1 e anteriores, o IPv6 é desabilitado por padrão.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Endereçamento IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)   
 [Esquema de configurações de rede](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<Elemento ipv6> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)

