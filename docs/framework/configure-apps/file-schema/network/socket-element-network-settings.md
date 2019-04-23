---
title: Elemento <socket> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 82bfe3b6e3107ff787716657dbf0b31dcadde911
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160151"
---
# <a name="socket-element-network-settings"></a>\<soquete > (configurações de rede)
Especifica se as operações de soquete usam portas de conclusão.  
  
 \<configuration>  
\<system.net>  
\<Configurações >  
\<socket>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|Indica se o soquete deve sempre usar portas de conclusão para aceitar chamadas de método. O valor padrão é `false`.|  
|`alwaysUseCompletionPortsForConnect`|Indica se o soquete deve sempre usar portas de conclusão para chamadas de método Connect. O valor padrão é `false`.|  
|`ipProtectionLevel`|Especifica o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> a ser usado para um soquete. O valor padrão depende da versão do Windows.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 O `alwaysUseCompletionPortsForAccept` e `alwaysUseCompletionPortsForConnect` atributos são usados para especificar o comportamento padrão sobre o uso de portas de conclusão pelas classes do <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace. Portas de conclusão são recomendadas para aplicativos de servidor de alto desempenho.  
  
 O valor padrão para o `alwaysUseCompletionPortsForAccept` e `alwaysUseCompletionPortsForConnect` atributos é **falso**.  
  
 O <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> pode ser usado para obter o valor atual do `alwaysUseCompletionPortsForAccept` atributo dos arquivos de configuração aplicáveis. O <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> pode ser usado para obter o valor atual do `alwaysUseCompletionPortsForConnect` atributo dos arquivos de configuração aplicáveis.  
  
 O `ipProtectionLevel` atributo especifica o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> a ser usado para um soquete. O <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriedade permite a configuração de uma restrição para um soquete IPv6 a um escopo especificado, como endereços com o mesmo locais do link ou prefixo local do site. Essa opção permite que aplicativos impor restrições de acesso a soquetes IPv6. Essas restrições permitem que um aplicativo em execução em uma LAN privada proteja-se de modo simples e robusto contra ataques externos. Essa opção amplia ou reduz o escopo de um soquete de escuta, permitindo acesso irrestrito de usuários públicos e privados, quando apropriado, ou restringindo o acesso somente ao mesmo site, conforme necessário.  
  
 Isso `ipProtectionLevel` configuração do atributo afeta somente tráfego de entrada inicial:  
  
-   Um servidor TCP escutando conexões de entrada em um soquete.  
  
-   Um aplicativo de UDP receber um pacote em um soquete.  
  
 Essa configuração não afeta já estabelecidas conexões TCP (tráfego é irrestrito em ambas as direções) e não afeta um aplicativo de envio de pacotes UDP.  
  
 Os valores possíveis para o `ipProtectionLevel` configuração do atributo correspondem com os níveis de proteção definido especificados no <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeração da seguinte maneira:  
  
|**Valor de atributo**|**Descrição**|  
|-|-|  
|EdgeRestricted|O nível de proteção de IP tem restrição de borda. Esse valor seria usado por aplicativos projetados para operar pela Internet. Essa configuração não permite a passagem de NAT (conversão de endereços de rede) usando a implementação do Windows Teredo. Esses aplicativos podem ignorar firewalls IPv4, de modo que os aplicativos devem ser protegidos contra ataques de Internet direcionados à porta aberta. No Windows Server 2003 e Windows XP, o valor padrão para o nível de proteção de IP em um soquete tem restrição de borda.|  
|Restrito|O nível de proteção de IP é restrito. Esse valor será usado por aplicativos de intranet que não implementam cenários de Internet. Esses aplicativos geralmente não são testados nem protegidos contra ataques do estilo usado na Internet. Essa configuração limitará o tráfego recebido para apenas link-local.|  
|Irrestrito|O nível de proteção de IP é irrestrito. Esse valor seria usado por aplicativos projetados para operar com a Internet, incluindo os aplicativos que aproveitam os recursos de passagem NAT IPv6 internos no Windows (Teredo, por exemplo). Esses aplicativos podem ignorar firewalls IPv4, de modo que os aplicativos devem ser protegidos contra ataques de Internet direcionados à porta aberta. No Windows Server 2008 R2 e Windows Vista, o valor padrão para o nível de proteção de IP em um soquete é irrestrito.|  
|Não especificado|O nível de proteção de IP não é especificado. No Windows 7 e Windows Server 2008 R2, o valor padrão para o nível de proteção de IP em um soquete é não especificado.|  
  
 O valor padrão para o `ipProtectionLevel` atributo é **Unspecified**.  
  
 O <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriedade pode ser usada para obter o valor atual do `ipProtectionLevel` atributo dos arquivos de configuração aplicáveis.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que as portas de conclusão devem ser usadas e que o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> deve ser irrestrito.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
