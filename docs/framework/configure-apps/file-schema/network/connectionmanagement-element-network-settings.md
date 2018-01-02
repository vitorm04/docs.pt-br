---
title: "&lt;connectionManagement&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 700d06d22c76762c80ea877006a8ac3789052b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="45f14-102">&lt;connectionManagement&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="45f14-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="45f14-103">Especifica o número máximo de conexões para um host de rede.</span><span class="sxs-lookup"><span data-stu-id="45f14-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="45f14-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="45f14-104">\<configuration></span></span>  
<span data-ttu-id="45f14-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="45f14-105">\<system.net></span></span>  
<span data-ttu-id="45f14-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="45f14-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f14-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45f14-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45f14-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45f14-108">Attributes and Elements</span></span>  
 <span data-ttu-id="45f14-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="45f14-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45f14-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="45f14-110">Attributes</span></span>  
 <span data-ttu-id="45f14-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="45f14-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45f14-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45f14-112">Child Elements</span></span>  
  
|<span data-ttu-id="45f14-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="45f14-113">**Element**</span></span>|<span data-ttu-id="45f14-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="45f14-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="45f14-115">add</span><span class="sxs-lookup"><span data-stu-id="45f14-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="45f14-116">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="45f14-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="45f14-117">clear</span><span class="sxs-lookup"><span data-stu-id="45f14-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="45f14-118">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="45f14-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="45f14-119">remove</span><span class="sxs-lookup"><span data-stu-id="45f14-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="45f14-120">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="45f14-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45f14-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45f14-121">Parent Elements</span></span>  
  
|<span data-ttu-id="45f14-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="45f14-122">**Element**</span></span>|<span data-ttu-id="45f14-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="45f14-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="45f14-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="45f14-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="45f14-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="45f14-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45f14-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="45f14-126">Remarks</span></span>  
 <span data-ttu-id="45f14-127">O `connectionManagement` elemento define o número máximo de conexões para um servidor ou grupo de servidores.</span><span class="sxs-lookup"><span data-stu-id="45f14-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="45f14-128">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="45f14-128">Configuration Files</span></span>  
 <span data-ttu-id="45f14-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="45f14-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f14-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45f14-130">Example</span></span>  
 <span data-ttu-id="45f14-131">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor www.contoso.com e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="45f14-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="45f14-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45f14-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="45f14-133">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="45f14-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
