---
title: Elemento <connectionManagement> (Configurações de Rede)
description: O <connectionManagement> elemento de configurações de rede especifica o número máximo de conexões a um host de rede no .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 52b780c739a00cb53694b547ee1a33c1b5d98c86
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167308"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="cd018-103">Elemento \<connectionManagement> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="cd018-103">\<connectionManagement> Element (Network Settings)</span></span>

<span data-ttu-id="cd018-104">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="cd018-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="cd018-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd018-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd018-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cd018-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cd018-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cd018-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd018-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="cd018-108">Attributes</span></span>  

 <span data-ttu-id="cd018-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cd018-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cd018-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cd018-110">Child Elements</span></span>  
  
|<span data-ttu-id="cd018-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="cd018-111">**Element**</span></span>|<span data-ttu-id="cd018-112">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="cd018-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cd018-113">add</span><span class="sxs-lookup"><span data-stu-id="cd018-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="cd018-114">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="cd018-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="cd018-115">clear</span><span class="sxs-lookup"><span data-stu-id="cd018-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="cd018-116">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="cd018-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="cd018-117">remove</span><span class="sxs-lookup"><span data-stu-id="cd018-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="cd018-118">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="cd018-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd018-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cd018-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cd018-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="cd018-120">**Element**</span></span>|<span data-ttu-id="cd018-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="cd018-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cd018-122">system.net</span><span class="sxs-lookup"><span data-stu-id="cd018-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="cd018-123">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="cd018-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd018-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd018-124">Remarks</span></span>  

 <span data-ttu-id="cd018-125">O `connectionManagement` elemento define o número máximo de conexões com um servidor ou grupo de servidores.</span><span class="sxs-lookup"><span data-stu-id="cd018-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cd018-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="cd018-126">Configuration Files</span></span>  

 <span data-ttu-id="cd018-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="cd018-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd018-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd018-128">Example</span></span>  

 <span data-ttu-id="cd018-129">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="cd018-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd018-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd018-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="cd018-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="cd018-131">Network Settings Schema</span></span>](index.md)
