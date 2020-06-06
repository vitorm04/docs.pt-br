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
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154888"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="a566c-102">Elemento \<connectionManagement> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="a566c-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="a566c-103">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="a566c-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="a566c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a566c-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a566c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a566c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a566c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a566c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a566c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a566c-107">Attributes</span></span>  
 <span data-ttu-id="a566c-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a566c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a566c-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a566c-109">Child Elements</span></span>  
  
|<span data-ttu-id="a566c-110">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a566c-110">**Element**</span></span>|<span data-ttu-id="a566c-111">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a566c-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a566c-112">adicionar</span><span class="sxs-lookup"><span data-stu-id="a566c-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a566c-113">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="a566c-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="a566c-114">formatação</span><span class="sxs-lookup"><span data-stu-id="a566c-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a566c-115">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="a566c-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="a566c-116">remove</span><span class="sxs-lookup"><span data-stu-id="a566c-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a566c-117">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="a566c-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a566c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a566c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a566c-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a566c-119">**Element**</span></span>|<span data-ttu-id="a566c-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a566c-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a566c-121">system.net</span><span class="sxs-lookup"><span data-stu-id="a566c-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="a566c-122">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="a566c-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a566c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="a566c-123">Remarks</span></span>  
 <span data-ttu-id="a566c-124">O `connectionManagement` elemento define o número máximo de conexões com um servidor ou grupo de servidores.</span><span class="sxs-lookup"><span data-stu-id="a566c-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a566c-125">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a566c-125">Configuration Files</span></span>  
 <span data-ttu-id="a566c-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a566c-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a566c-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a566c-127">Example</span></span>  
 <span data-ttu-id="a566c-128">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="a566c-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a566c-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="a566c-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a566c-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a566c-130">Network Settings Schema</span></span>](index.md)
