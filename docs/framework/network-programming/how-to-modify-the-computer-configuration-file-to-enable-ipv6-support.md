---
title: Como modificar o arquivo de configuração do computador para habilitar o suporte a IPv6
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 32aa1c3fa50d5c0486da4ef6799c77ead605b504
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187251"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Como modificar o arquivo de configuração do computador para habilitar o suporte a IPv6
O exemplo de código a seguir mostra como modificar o arquivo de configuração do computador, *machine.config* para habilitar o suporte a IPv6. O arquivo *machine.config* é armazenado na pasta *%Windir%\Microsoft.NET\Framework* no diretório em que o Windows foi instalado. Há um outro arquivo *machine.config* nas pastas em *%Windir%\Microsoft.NET\Framework* para cada versão do .NET Framework instalada no computador (por exemplo, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.  
  
 Para o .NET Framework versão 1.1 e anterior, o valor da opção de configuração **ipv6 enabled** especifica se os membros da classe <xref:System.Net.Dns?displayProperty=nameWithType> retornam endereços IPv6.  
  
 Para o .NET Framework versão 2.0 e posteriores, se o Windows der suporte ao IPv6, todos os membros da classe <xref:System.Net.Dns?displayProperty=nameWithType>, (por exemplo, o método <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>), retornarão endereços IPv6 com uma limitação. Os membros obsoletos da classe <xref:System.Net.Dns?displayProperty=nameWithType> (por exemplo, o método <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lerão e reconhecerão o valor no arquivo de configuração.  
  
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
