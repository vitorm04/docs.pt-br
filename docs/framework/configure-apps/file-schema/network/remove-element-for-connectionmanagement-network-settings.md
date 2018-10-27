---
title: '&lt;remover&gt; elemento para connectionManagement (configurações de rede)'
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
ms.openlocfilehash: 03cac1523c0fce268c2df8d04134c0d5e88830e2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181547"
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="9636a-102">&lt;remover&gt; elemento para connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="9636a-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="9636a-103">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="9636a-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="9636a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9636a-104">\<configuration></span></span>  
<span data-ttu-id="9636a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9636a-105">\<system.net></span></span>  
<span data-ttu-id="9636a-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="9636a-106">\<connectionManagement></span></span>  
<span data-ttu-id="9636a-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="9636a-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9636a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9636a-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9636a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9636a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9636a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9636a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9636a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9636a-111">Attributes</span></span>  
  
|<span data-ttu-id="9636a-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="9636a-112">**Attribute**</span></span>|<span data-ttu-id="9636a-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="9636a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="9636a-114">Um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="9636a-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9636a-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9636a-115">Child Elements</span></span>  
 <span data-ttu-id="9636a-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9636a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9636a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9636a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9636a-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="9636a-118">**Element**</span></span>|<span data-ttu-id="9636a-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="9636a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9636a-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="9636a-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="9636a-121">Especifica o número máximo de conexões para um host de rede.</span><span class="sxs-lookup"><span data-stu-id="9636a-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9636a-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9636a-122">Remarks</span></span>  
 <span data-ttu-id="9636a-123">O `remove` elemento remove a entrada de lista de gerenciamento de conexão para o servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="9636a-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="9636a-124">O valor da `address` atributo deve ser um nome de host ou endereço IP válido.</span><span class="sxs-lookup"><span data-stu-id="9636a-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9636a-125">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="9636a-125">Configuration Files</span></span>  
 <span data-ttu-id="9636a-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="9636a-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9636a-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9636a-127">Example</span></span>  
 <span data-ttu-id="9636a-128">O exemplo a seguir remove quaisquer entradas de lista de gerenciamento de conexão para o servidor `www.adventure-works.com` e, em seguida, configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="9636a-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9636a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9636a-129">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="9636a-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9636a-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
