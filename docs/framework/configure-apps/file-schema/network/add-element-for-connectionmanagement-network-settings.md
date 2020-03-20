---
title: Elemento <add> para connectionManagement (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155005"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="0eabd-102">\<adicionar> Elemento para gerenciamento de conexão (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="0eabd-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="0eabd-103">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexões.</span><span class="sxs-lookup"><span data-stu-id="0eabd-103">Adds an IP address or DNS name to the connection management list.</span></span>  

<span data-ttu-id="0eabd-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0eabd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0eabd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0eabd-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="0eabd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de gerenciamento de conexão**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0eabd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="0eabd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="0eabd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0eabd-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0eabd-108">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eabd-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0eabd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0eabd-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0eabd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eabd-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0eabd-111">Attributes</span></span>  
  
|<span data-ttu-id="0eabd-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="0eabd-112">**Attribute**</span></span>|<span data-ttu-id="0eabd-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0eabd-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="0eabd-114">Uma seqüência descrevendo um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="0eabd-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="0eabd-115">O número máximo de conexões permitidas a um servidor.</span><span class="sxs-lookup"><span data-stu-id="0eabd-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="0eabd-116">Se não for fornecido, o padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="0eabd-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eabd-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0eabd-117">Child Elements</span></span>  
 <span data-ttu-id="0eabd-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0eabd-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eabd-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0eabd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0eabd-120">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="0eabd-120">**Element**</span></span>|<span data-ttu-id="0eabd-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="0eabd-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0eabd-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="0eabd-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="0eabd-123">Especifica o número máximo de conexões a um host de rede.</span><span class="sxs-lookup"><span data-stu-id="0eabd-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eabd-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0eabd-124">Remarks</span></span>  
 <span data-ttu-id="0eabd-125">O valor `address` do atributo deve ser um asterisco para indicar todas `<schema>://<idn_hostname>[:<port>]`as conexões, ou uma seqüência do formulário .</span><span class="sxs-lookup"><span data-stu-id="0eabd-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="0eabd-126">Se o URI for passado para qualquer APIs HTTP que contenha Unicode, o nome será convertido internamente usando <xref:System.Uri.DnsSafeHost%2A> o que pode retornar uma seqüência de código punicode (comportamento dependente da configuração atual do IDN).</span><span class="sxs-lookup"><span data-stu-id="0eabd-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0eabd-127">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0eabd-127">Configuration Files</span></span>  
 <span data-ttu-id="0eabd-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0eabd-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eabd-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0eabd-129">Example</span></span>  
 <span data-ttu-id="0eabd-130">O exemplo a seguir configura um aplicativo para `www.contoso.com` usar quatro conexões para o servidor e duas conexões para todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="0eabd-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0eabd-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="0eabd-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="0eabd-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="0eabd-132">Network Settings Schema</span></span>](index.md)
