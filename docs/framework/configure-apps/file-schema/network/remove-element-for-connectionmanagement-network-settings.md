---
title: Elemento <remove> para connectionManagement (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 8ab7a43fbb3e8df5bb0c99b5947f2fafb362399a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664037"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e1e21-102">\<remover o elemento > para connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="e1e21-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e1e21-103">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="e1e21-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="e1e21-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e1e21-104">\<configuration></span></span>  
<span data-ttu-id="e1e21-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e1e21-105">\<system.net></span></span>  
<span data-ttu-id="e1e21-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="e1e21-106">\<connectionManagement></span></span>  
<span data-ttu-id="e1e21-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="e1e21-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e21-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1e21-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1e21-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1e21-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1e21-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1e21-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1e21-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1e21-111">Attributes</span></span>  
  
|<span data-ttu-id="e1e21-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="e1e21-112">**Attribute**</span></span>|<span data-ttu-id="e1e21-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e1e21-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="e1e21-114">Um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="e1e21-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1e21-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1e21-115">Child Elements</span></span>  
 <span data-ttu-id="e1e21-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e1e21-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1e21-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1e21-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e1e21-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e1e21-118">**Element**</span></span>|<span data-ttu-id="e1e21-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e1e21-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e1e21-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e1e21-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e1e21-121">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="e1e21-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1e21-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1e21-122">Remarks</span></span>  
 <span data-ttu-id="e1e21-123">O `remove` elemento remove a entrada da lista de gerenciamento de conexões para o servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="e1e21-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="e1e21-124">O valor do `address` atributo deve ser um nome de host ou endereço IP válido.</span><span class="sxs-lookup"><span data-stu-id="e1e21-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e1e21-125">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e1e21-125">Configuration Files</span></span>  
 <span data-ttu-id="e1e21-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e1e21-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e21-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1e21-127">Example</span></span>  
 <span data-ttu-id="e1e21-128">O exemplo a seguir remove todas as entradas da lista de gerenciamento `www.adventure-works.com` de conexões do servidor e, em seguida, configura um aplicativo para usar `www.contoso.com` quatro conexões com o servidor e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="e1e21-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1e21-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1e21-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="e1e21-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e1e21-130">Network Settings Schema</span></span>](index.md)
