---
title: '&lt;connectionManagement&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 28864de79e809968f7efa6f3b052cfd599961854
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685020"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="2747f-102">&lt;connectionManagement&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2747f-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2747f-103">Especifica o número máximo de conexões para um host de rede.</span><span class="sxs-lookup"><span data-stu-id="2747f-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="2747f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2747f-104">\<configuration></span></span>  
<span data-ttu-id="2747f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2747f-105">\<system.net></span></span>  
<span data-ttu-id="2747f-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="2747f-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2747f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2747f-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2747f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2747f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2747f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2747f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2747f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2747f-110">Attributes</span></span>  
 <span data-ttu-id="2747f-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2747f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2747f-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2747f-112">Child Elements</span></span>  
  
|<span data-ttu-id="2747f-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2747f-113">**Element**</span></span>|<span data-ttu-id="2747f-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2747f-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2747f-115">add</span><span class="sxs-lookup"><span data-stu-id="2747f-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2747f-116">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="2747f-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="2747f-117">clear</span><span class="sxs-lookup"><span data-stu-id="2747f-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2747f-118">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="2747f-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="2747f-119">remove</span><span class="sxs-lookup"><span data-stu-id="2747f-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2747f-120">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="2747f-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2747f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2747f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2747f-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2747f-122">**Element**</span></span>|<span data-ttu-id="2747f-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2747f-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2747f-124">system.net</span><span class="sxs-lookup"><span data-stu-id="2747f-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="2747f-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="2747f-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2747f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="2747f-126">Remarks</span></span>  
 <span data-ttu-id="2747f-127">O `connectionManagement` elemento define o número máximo de conexões a um servidor ou grupo de servidores.</span><span class="sxs-lookup"><span data-stu-id="2747f-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2747f-128">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="2747f-128">Configuration Files</span></span>  
 <span data-ttu-id="2747f-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2747f-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2747f-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2747f-130">Example</span></span>  
 <span data-ttu-id="2747f-131">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="2747f-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2747f-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2747f-132">See also</span></span>
- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="2747f-133">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2747f-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
