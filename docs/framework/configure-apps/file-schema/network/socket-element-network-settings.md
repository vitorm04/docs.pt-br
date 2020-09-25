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
ms.openlocfilehash: b8df32745007b2a145d35b8cfcc4cbd2bd17eb33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201727"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="b8130-102">Elemento \<socket> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="b8130-102">\<socket> Element (Network Settings)</span></span>

<span data-ttu-id="b8130-103">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="b8130-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="b8130-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8130-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8130-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b8130-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b8130-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b8130-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8130-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8130-107">Attributes</span></span>  
  
|<span data-ttu-id="b8130-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="b8130-108">**Attribute**</span></span>|<span data-ttu-id="b8130-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b8130-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="b8130-110">Indica se o soquete sempre deve usar as portas de conclusão para aceitar chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="b8130-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="b8130-111">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b8130-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="b8130-112">Indica se o soquete sempre deve usar portas de conclusão para chamadas de método Connect.</span><span class="sxs-lookup"><span data-stu-id="b8130-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="b8130-113">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b8130-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="b8130-114">Especifica o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> a ser usado para um soquete.</span><span class="sxs-lookup"><span data-stu-id="b8130-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b8130-115">O valor padrão depende da versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="b8130-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8130-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b8130-116">Child Elements</span></span>  

 <span data-ttu-id="b8130-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b8130-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8130-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b8130-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b8130-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="b8130-119">**Element**</span></span>|<span data-ttu-id="b8130-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b8130-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8130-121">configurações</span><span class="sxs-lookup"><span data-stu-id="b8130-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b8130-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b8130-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8130-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8130-123">Remarks</span></span>  

 <span data-ttu-id="b8130-124">Os `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` atributos e são usados para especificar o comportamento padrão em relação ao uso de portas de conclusão pelas classes no <xref:System.Net.Sockets?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="b8130-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="b8130-125">As portas de conclusão são recomendadas para aplicativos de servidor de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="b8130-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="b8130-126">O valor padrão para os `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` atributos e é **false**.</span><span class="sxs-lookup"><span data-stu-id="b8130-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="b8130-127">O <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> pode ser usado para obter o valor atual do `alwaysUseCompletionPortsForAccept` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="b8130-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="b8130-128">O <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> pode ser usado para obter o valor atual do `alwaysUseCompletionPortsForConnect` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="b8130-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="b8130-129">O `ipProtectionLevel` atributo especifica o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> a ser usado para um soquete.</span><span class="sxs-lookup"><span data-stu-id="b8130-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="b8130-130">A <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriedade permite a configuração de uma restrição para um soquete IPv6 para um escopo especificado, como endereços com o mesmo link local ou local do site.</span><span class="sxs-lookup"><span data-stu-id="b8130-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="b8130-131">Essa opção permite que os aplicativos coloquem restrições de acesso em soquetes IPv6.</span><span class="sxs-lookup"><span data-stu-id="b8130-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="b8130-132">Essas restrições permitem que um aplicativo em execução em uma LAN privada proteja-se de modo simples e robusto contra ataques externos.</span><span class="sxs-lookup"><span data-stu-id="b8130-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="b8130-133">Essa opção amplia ou limita o escopo de um soquete de escuta, habilitando o acesso irrestrito de usuários públicos e privados quando apropriado ou restringindo o acesso somente ao mesmo site, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b8130-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="b8130-134">Essa `ipProtectionLevel` configuração de atributo afeta apenas o tráfego de entrada inicial:</span><span class="sxs-lookup"><span data-stu-id="b8130-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="b8130-135">Um servidor TCP escutando conexões de entrada em um soquete.</span><span class="sxs-lookup"><span data-stu-id="b8130-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="b8130-136">Um aplicativo UDP que recebe um pacote em um soquete.</span><span class="sxs-lookup"><span data-stu-id="b8130-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="b8130-137">Essa definição de configuração não afeta as conexões TCP já estabelecidas (o tráfego é irrestrito em ambas as direções) e não afeta um aplicativo que envia pacotes UDP.</span><span class="sxs-lookup"><span data-stu-id="b8130-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="b8130-138">Os valores possíveis para a `ipProtectionLevel` configuração de atributo correspondem aos níveis de proteção definidos especificados na <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeração da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b8130-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="b8130-139">**Valor do atributo**</span><span class="sxs-lookup"><span data-stu-id="b8130-139">**Attribute Value**</span></span>|<span data-ttu-id="b8130-140">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b8130-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="b8130-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="b8130-141">EdgeRestricted</span></span>|<span data-ttu-id="b8130-142">O nível de proteção de IP tem restrição de borda.</span><span class="sxs-lookup"><span data-stu-id="b8130-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="b8130-143">Esse valor seria usado por aplicativos projetados para operar pela Internet.</span><span class="sxs-lookup"><span data-stu-id="b8130-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="b8130-144">Essa configuração não permite a passagem de NAT (conversão de endereços de rede) usando a implementação do Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="b8130-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="b8130-145">Esses aplicativos podem ignorar firewalls IPv4, de modo que os aplicativos devem ser protegidos contra ataques de Internet direcionados à porta aberta.</span><span class="sxs-lookup"><span data-stu-id="b8130-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b8130-146">No Windows Server 2003 e Windows XP, o valor padrão para o nível de proteção de IP em um soquete tem restrição de borda.</span><span class="sxs-lookup"><span data-stu-id="b8130-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="b8130-147">Restrito</span><span class="sxs-lookup"><span data-stu-id="b8130-147">Restricted</span></span>|<span data-ttu-id="b8130-148">O nível de proteção de IP é restrito.</span><span class="sxs-lookup"><span data-stu-id="b8130-148">The IP protection level is restricted.</span></span> <span data-ttu-id="b8130-149">Esse valor será usado por aplicativos de intranet que não implementam cenários de Internet.</span><span class="sxs-lookup"><span data-stu-id="b8130-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="b8130-150">Esses aplicativos geralmente não são testados nem protegidos contra ataques do estilo usado na Internet.</span><span class="sxs-lookup"><span data-stu-id="b8130-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="b8130-151">Essa configuração limitará o tráfego recebido para apenas link-local.</span><span class="sxs-lookup"><span data-stu-id="b8130-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="b8130-152">Irrestrito</span><span class="sxs-lookup"><span data-stu-id="b8130-152">Unrestricted</span></span>|<span data-ttu-id="b8130-153">O nível de proteção de IP é irrestrito.</span><span class="sxs-lookup"><span data-stu-id="b8130-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="b8130-154">Esse valor seria usado por aplicativos projetados para operar com a Internet, incluindo os aplicativos que aproveitam os recursos de passagem NAT IPv6 internos no Windows (Teredo, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="b8130-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="b8130-155">Esses aplicativos podem ignorar firewalls IPv4, de modo que os aplicativos devem ser protegidos contra ataques de Internet direcionados à porta aberta.</span><span class="sxs-lookup"><span data-stu-id="b8130-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="b8130-156">No Windows Server 2008 R2 e Windows Vista, o valor padrão para o nível de proteção de IP em um soquete é irrestrito.</span><span class="sxs-lookup"><span data-stu-id="b8130-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="b8130-157">Não Especificado</span><span class="sxs-lookup"><span data-stu-id="b8130-157">Unspecified</span></span>|<span data-ttu-id="b8130-158">O nível de proteção de IP não é especificado.</span><span class="sxs-lookup"><span data-stu-id="b8130-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="b8130-159">No Windows 7 e Windows Server 2008 R2, o valor padrão para o nível de proteção de IP em um soquete é não especificado.</span><span class="sxs-lookup"><span data-stu-id="b8130-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="b8130-160">O valor padrão para o `ipProtectionLevel` atributo não é **especificado**.</span><span class="sxs-lookup"><span data-stu-id="b8130-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="b8130-161">A <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriedade pode ser usada para obter o valor atual do `ipProtectionLevel` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="b8130-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b8130-162">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="b8130-162">Configuration Files</span></span>  

 <span data-ttu-id="b8130-163">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b8130-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8130-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8130-164">Example</span></span>  

 <span data-ttu-id="b8130-165">O exemplo a seguir mostra como especificar que as portas de conclusão devem ser usadas e que o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> deve ser irrestrito.</span><span class="sxs-lookup"><span data-stu-id="b8130-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8130-166">Veja também</span><span class="sxs-lookup"><span data-stu-id="b8130-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="b8130-167">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b8130-167">Network Settings Schema</span></span>](index.md)
