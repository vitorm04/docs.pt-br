---
title: '&lt;Adicionar&gt; elemento connectionManagement (configurações de rede)'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c6cfd036a98c345da23fc7b3699987c9678e149d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753736"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="bd417-102">&lt;Adicionar&gt; elemento connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="bd417-102">&lt;add&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="bd417-103">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="bd417-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="bd417-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bd417-104">\<configuration></span></span>  
<span data-ttu-id="bd417-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bd417-105">\<system.net></span></span>  
<span data-ttu-id="bd417-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="bd417-106">\<connectionManagement></span></span>  
<span data-ttu-id="bd417-107">\<add></span><span class="sxs-lookup"><span data-stu-id="bd417-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd417-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd417-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd417-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd417-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bd417-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bd417-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd417-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd417-111">Attributes</span></span>  
  
|<span data-ttu-id="bd417-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="bd417-112">**Attribute**</span></span>|<span data-ttu-id="bd417-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="bd417-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="bd417-114">Uma cadeia de caracteres que descreve um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="bd417-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="bd417-115">O número máximo de conexões permitido para um servidor.</span><span class="sxs-lookup"><span data-stu-id="bd417-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="bd417-116">Se não for fornecido, o padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="bd417-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd417-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bd417-117">Child Elements</span></span>  
 <span data-ttu-id="bd417-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bd417-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd417-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bd417-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bd417-120">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="bd417-120">**Element**</span></span>|<span data-ttu-id="bd417-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="bd417-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bd417-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="bd417-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="bd417-123">Especifica o número máximo de conexões para um host de rede.</span><span class="sxs-lookup"><span data-stu-id="bd417-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd417-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd417-124">Remarks</span></span>  
 <span data-ttu-id="bd417-125">O valor de `address` atributo deve ser um asterisco para indicar todas as conexões ou uma cadeia de caracteres do formulário `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="bd417-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="bd417-126">Se o URI passado para quaisquer APIs HTTP contém Unicode, o nome será convertido usando internamente <xref:System.Uri.DnsSafeHost%2A> que podem retornar uma cadeia de caracteres punicode (comportamento depende da configuração atual de IDN).</span><span class="sxs-lookup"><span data-stu-id="bd417-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bd417-127">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="bd417-127">Configuration Files</span></span>  
 <span data-ttu-id="bd417-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="bd417-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd417-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd417-129">Example</span></span>  
 <span data-ttu-id="bd417-130">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor www.contoso.com e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="bd417-130">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd417-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd417-131">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="bd417-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="bd417-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
