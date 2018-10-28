---
title: '&lt;soquete&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: ff06fd6518e67020b4d67d4e081307b8e54bae85
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194690"
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="60bc0-102">&lt;soquete&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="60bc0-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="60bc0-103">Especifica se as operações de soquete usam portas de conclusão.</span><span class="sxs-lookup"><span data-stu-id="60bc0-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="60bc0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="60bc0-104">\<configuration></span></span>  
<span data-ttu-id="60bc0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="60bc0-105">\<system.net></span></span>  
<span data-ttu-id="60bc0-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="60bc0-106">\<settings></span></span>  
<span data-ttu-id="60bc0-107">\<soquete ></span><span class="sxs-lookup"><span data-stu-id="60bc0-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60bc0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60bc0-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60bc0-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60bc0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="60bc0-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60bc0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60bc0-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="60bc0-111">Attributes</span></span>  
  
|<span data-ttu-id="60bc0-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="60bc0-112">**Attribute**</span></span>|<span data-ttu-id="60bc0-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="60bc0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="60bc0-114">Indica se o soquete deve sempre usar portas de conclusão para aceitar chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="60bc0-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="60bc0-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="60bc0-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="60bc0-116">Indica se o soquete deve sempre usar portas de conclusão para chamadas de método Connect.</span><span class="sxs-lookup"><span data-stu-id="60bc0-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="60bc0-117">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="60bc0-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="60bc0-118">Especifica o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> a ser usado para um soquete.</span><span class="sxs-lookup"><span data-stu-id="60bc0-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="60bc0-119">O valor padrão depende da versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="60bc0-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60bc0-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60bc0-120">Child Elements</span></span>  
 <span data-ttu-id="60bc0-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="60bc0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60bc0-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60bc0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="60bc0-123">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="60bc0-123">**Element**</span></span>|<span data-ttu-id="60bc0-124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="60bc0-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="60bc0-125">settings</span><span class="sxs-lookup"><span data-stu-id="60bc0-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="60bc0-126">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="60bc0-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60bc0-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="60bc0-127">Remarks</span></span>  
 <span data-ttu-id="60bc0-128">O `alwaysUseCompletionPortsForAccept` e `alwaysUseCompletionPortsForConnect` atributos são usados para especificar o comportamento padrão sobre o uso de portas de conclusão pelas classes do <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span><span class="sxs-lookup"><span data-stu-id="60bc0-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="60bc0-129">Portas de conclusão são recomendadas para aplicativos de servidor de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="60bc0-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="60bc0-130">O valor padrão para o `alwaysUseCompletionPortsForAccept` e `alwaysUseCompletionPortsForConnect` atributos é **falso**.</span><span class="sxs-lookup"><span data-stu-id="60bc0-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="60bc0-131">O <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> pode ser usado para obter o valor atual do `alwaysUseCompletionPortsForAccept` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="60bc0-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="60bc0-132">O <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> pode ser usado para obter o valor atual do `alwaysUseCompletionPortsForConnect` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="60bc0-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="60bc0-133">O `ipProtectionLevel` atributo especifica o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> a ser usado para um soquete.</span><span class="sxs-lookup"><span data-stu-id="60bc0-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="60bc0-134">O <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriedade permite a configuração de uma restrição para um soquete IPv6 a um escopo especificado, como endereços com o mesmo locais do link ou prefixo local do site.</span><span class="sxs-lookup"><span data-stu-id="60bc0-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="60bc0-135">Essa opção permite que aplicativos impor restrições de acesso a soquetes IPv6.</span><span class="sxs-lookup"><span data-stu-id="60bc0-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="60bc0-136">Essas restrições permitem que um aplicativo em execução em uma LAN privada proteja-se de modo simples e robusto contra ataques externos.</span><span class="sxs-lookup"><span data-stu-id="60bc0-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="60bc0-137">Essa opção amplia ou reduz o escopo de um soquete de escuta, permitindo acesso irrestrito de usuários públicos e privados, quando apropriado, ou restringindo o acesso somente ao mesmo site, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="60bc0-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="60bc0-138">Isso `ipProtectionLevel` configuração do atributo afeta somente tráfego de entrada inicial:</span><span class="sxs-lookup"><span data-stu-id="60bc0-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="60bc0-139">Um servidor TCP escutando conexões de entrada em um soquete.</span><span class="sxs-lookup"><span data-stu-id="60bc0-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="60bc0-140">Um aplicativo de UDP receber um pacote em um soquete.</span><span class="sxs-lookup"><span data-stu-id="60bc0-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="60bc0-141">Essa configuração não afeta já estabelecidas conexões TCP (tráfego é irrestrito em ambas as direções) e não afeta um aplicativo de envio de pacotes UDP.</span><span class="sxs-lookup"><span data-stu-id="60bc0-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="60bc0-142">Os valores possíveis para o `ipProtectionLevel` configuração do atributo correspondem com os níveis de proteção definido especificados no <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeração da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="60bc0-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="60bc0-143">**Valor de atributo**</span><span class="sxs-lookup"><span data-stu-id="60bc0-143">**Attribute Value**</span></span>|<span data-ttu-id="60bc0-144">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="60bc0-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="60bc0-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="60bc0-145">EdgeRestricted</span></span>|<span data-ttu-id="60bc0-146">O nível de proteção de IP tem restrição de borda.</span><span class="sxs-lookup"><span data-stu-id="60bc0-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="60bc0-147">Esse valor seria usado por aplicativos projetados para operar pela Internet.</span><span class="sxs-lookup"><span data-stu-id="60bc0-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="60bc0-148">Essa configuração não permite a passagem de NAT (conversão de endereços de rede) usando a implementação do Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="60bc0-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="60bc0-149">Esses aplicativos podem ignorar firewalls IPv4, de modo que os aplicativos devem ser protegidos contra ataques de Internet direcionados à porta aberta.</span><span class="sxs-lookup"><span data-stu-id="60bc0-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="60bc0-150">No Windows Server 2003 e Windows XP, o valor padrão para o nível de proteção de IP em um soquete tem restrição de borda.</span><span class="sxs-lookup"><span data-stu-id="60bc0-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="60bc0-151">Restrito</span><span class="sxs-lookup"><span data-stu-id="60bc0-151">Restricted</span></span>|<span data-ttu-id="60bc0-152">O nível de proteção de IP é restrito.</span><span class="sxs-lookup"><span data-stu-id="60bc0-152">The IP protection level is restricted.</span></span> <span data-ttu-id="60bc0-153">Esse valor será usado por aplicativos de intranet que não implementam cenários de Internet.</span><span class="sxs-lookup"><span data-stu-id="60bc0-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="60bc0-154">Esses aplicativos geralmente não são testados nem protegidos contra ataques do estilo usado na Internet.</span><span class="sxs-lookup"><span data-stu-id="60bc0-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="60bc0-155">Essa configuração limitará o tráfego recebido para apenas link-local.</span><span class="sxs-lookup"><span data-stu-id="60bc0-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="60bc0-156">Irrestrito</span><span class="sxs-lookup"><span data-stu-id="60bc0-156">Unrestricted</span></span>|<span data-ttu-id="60bc0-157">O nível de proteção de IP é irrestrito.</span><span class="sxs-lookup"><span data-stu-id="60bc0-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="60bc0-158">Esse valor seria usado por aplicativos projetados para operar com a Internet, incluindo os aplicativos que aproveitam os recursos de passagem NAT IPv6 internos no Windows (Teredo, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="60bc0-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="60bc0-159">Esses aplicativos podem ignorar firewalls IPv4, de modo que os aplicativos devem ser protegidos contra ataques de Internet direcionados à porta aberta.</span><span class="sxs-lookup"><span data-stu-id="60bc0-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="60bc0-160">No Windows Server 2008 R2 e Windows Vista, o valor padrão para o nível de proteção de IP em um soquete é irrestrito.</span><span class="sxs-lookup"><span data-stu-id="60bc0-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="60bc0-161">Não especificado</span><span class="sxs-lookup"><span data-stu-id="60bc0-161">Unspecified</span></span>|<span data-ttu-id="60bc0-162">O nível de proteção de IP não é especificado.</span><span class="sxs-lookup"><span data-stu-id="60bc0-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="60bc0-163">No Windows 7 e Windows Server 2008 R2, o valor padrão para o nível de proteção de IP em um soquete é não especificado.</span><span class="sxs-lookup"><span data-stu-id="60bc0-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="60bc0-164">O valor padrão para o `ipProtectionLevel` atributo é **Unspecified**.</span><span class="sxs-lookup"><span data-stu-id="60bc0-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="60bc0-165">O <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> propriedade pode ser usada para obter o valor atual do `ipProtectionLevel` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="60bc0-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="60bc0-166">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="60bc0-166">Configuration Files</span></span>  
 <span data-ttu-id="60bc0-167">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="60bc0-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60bc0-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60bc0-168">Example</span></span>  
 <span data-ttu-id="60bc0-169">O exemplo a seguir mostra como especificar que as portas de conclusão devem ser usadas e que o padrão <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> deve ser irrestrito.</span><span class="sxs-lookup"><span data-stu-id="60bc0-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60bc0-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60bc0-170">See Also</span></span>  
- <xref:System.Net?displayProperty=nameWithType>  
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
- <xref:System.Net.Sockets?displayProperty=nameWithType>  
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
- [<span data-ttu-id="60bc0-171">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="60bc0-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
