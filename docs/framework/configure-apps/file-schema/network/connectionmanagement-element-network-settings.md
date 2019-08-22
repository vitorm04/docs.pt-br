---
title: Elemento <connectionManagement> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664164"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="b76fd-102">\<Elemento de > connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="b76fd-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="b76fd-103">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="b76fd-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="b76fd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b76fd-104">\<configuration></span></span>  
<span data-ttu-id="b76fd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b76fd-105">\<system.net></span></span>  
<span data-ttu-id="b76fd-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="b76fd-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b76fd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b76fd-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b76fd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b76fd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b76fd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b76fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b76fd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b76fd-110">Attributes</span></span>  
 <span data-ttu-id="b76fd-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b76fd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b76fd-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b76fd-112">Child Elements</span></span>  
  
|<span data-ttu-id="b76fd-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b76fd-113">**Element**</span></span>|<span data-ttu-id="b76fd-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b76fd-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b76fd-115">add</span><span class="sxs-lookup"><span data-stu-id="b76fd-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="b76fd-116">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="b76fd-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="b76fd-117">clear</span><span class="sxs-lookup"><span data-stu-id="b76fd-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="b76fd-118">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="b76fd-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="b76fd-119">remove</span><span class="sxs-lookup"><span data-stu-id="b76fd-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="b76fd-120">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="b76fd-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b76fd-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b76fd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b76fd-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b76fd-122">**Element**</span></span>|<span data-ttu-id="b76fd-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b76fd-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b76fd-124">system.net</span><span class="sxs-lookup"><span data-stu-id="b76fd-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b76fd-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="b76fd-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b76fd-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b76fd-126">Remarks</span></span>  
 <span data-ttu-id="b76fd-127">O `connectionManagement` elemento define o número máximo de conexões com um servidor ou grupo de servidores.</span><span class="sxs-lookup"><span data-stu-id="b76fd-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b76fd-128">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="b76fd-128">Configuration Files</span></span>  
 <span data-ttu-id="b76fd-129">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b76fd-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b76fd-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b76fd-130">Example</span></span>  
 <span data-ttu-id="b76fd-131">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="b76fd-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b76fd-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b76fd-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b76fd-133">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b76fd-133">Network Settings Schema</span></span>](index.md)
