---
title: Elemento <connectionManagement> (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 61fd40500934bc7b67d2960f4a64f8ac12466883
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285825"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="1f1b6-102">\<connectionManagement > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="1f1b6-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="1f1b6-103">Especifica o número máximo de conexões para um host de rede.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="1f1b6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1f1b6-104">\<configuration></span></span>  
<span data-ttu-id="1f1b6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1f1b6-105">\<system.net></span></span>  
<span data-ttu-id="1f1b6-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="1f1b6-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1b6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f1b6-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f1b6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1f1b6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1f1b6-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f1b6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1f1b6-110">Attributes</span></span>  
 <span data-ttu-id="1f1b6-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f1b6-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1f1b6-112">Child Elements</span></span>  
  
|<span data-ttu-id="1f1b6-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="1f1b6-113">**Element**</span></span>|<span data-ttu-id="1f1b6-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="1f1b6-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1f1b6-115">add</span><span class="sxs-lookup"><span data-stu-id="1f1b6-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="1f1b6-116">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="1f1b6-117">clear</span><span class="sxs-lookup"><span data-stu-id="1f1b6-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="1f1b6-118">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="1f1b6-119">remove</span><span class="sxs-lookup"><span data-stu-id="1f1b6-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="1f1b6-120">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f1b6-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1f1b6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1f1b6-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="1f1b6-122">**Element**</span></span>|<span data-ttu-id="1f1b6-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="1f1b6-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1f1b6-124">system.net</span><span class="sxs-lookup"><span data-stu-id="1f1b6-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="1f1b6-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f1b6-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f1b6-126">Remarks</span></span>  
 <span data-ttu-id="1f1b6-127">O `connectionManagement` elemento define o número máximo de conexões a um servidor ou grupo de servidores.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1f1b6-128">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="1f1b6-128">Configuration Files</span></span>  
 <span data-ttu-id="1f1b6-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1f1b6-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f1b6-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1f1b6-130">Example</span></span>  
 <span data-ttu-id="1f1b6-131">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="1f1b6-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f1b6-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f1b6-132">See also</span></span>
- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="1f1b6-133">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="1f1b6-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
