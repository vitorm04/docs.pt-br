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
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154732"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="a2a42-102">\<remover> Elemento para conexãoGerenciamento (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="a2a42-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="a2a42-103">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="a2a42-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="a2a42-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a2a42-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a2a42-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a2a42-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="a2a42-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de gerenciamento de conexão**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a2a42-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="a2a42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remover>**</span><span class="sxs-lookup"><span data-stu-id="a2a42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a2a42-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2a42-108">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2a42-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a2a42-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a2a42-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a2a42-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2a42-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a2a42-111">Attributes</span></span>  
  
|<span data-ttu-id="a2a42-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="a2a42-112">**Attribute**</span></span>|<span data-ttu-id="a2a42-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a2a42-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="a2a42-114">Um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="a2a42-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2a42-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a2a42-115">Child Elements</span></span>  
 <span data-ttu-id="a2a42-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a2a42-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2a42-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a2a42-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a2a42-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="a2a42-118">**Element**</span></span>|<span data-ttu-id="a2a42-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a2a42-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a2a42-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a2a42-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a2a42-121">Especifica o número máximo de conexões a um host de rede.</span><span class="sxs-lookup"><span data-stu-id="a2a42-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2a42-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2a42-122">Remarks</span></span>  
 <span data-ttu-id="a2a42-123">O `remove` elemento remove a entrada da lista de gerenciamento de conexão para o servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="a2a42-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="a2a42-124">O valor `address` do atributo deve ser um endereço IP válido ou nome de host.</span><span class="sxs-lookup"><span data-stu-id="a2a42-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a2a42-125">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a2a42-125">Configuration Files</span></span>  
 <span data-ttu-id="a2a42-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a2a42-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2a42-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2a42-127">Example</span></span>  
 <span data-ttu-id="a2a42-128">O exemplo a seguir remove todas as `www.adventure-works.com` entradas da lista de gerenciamento de conexão para o servidor e, em seguida, configura um aplicativo para usar quatro conexões para o servidor `www.contoso.com` e duas conexões para todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="a2a42-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2a42-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="a2a42-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a2a42-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a2a42-130">Network Settings Schema</span></span>](index.md)
