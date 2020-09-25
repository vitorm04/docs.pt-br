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
ms.openlocfilehash: 46157482d7ceb42b352c68dc9b0eab4f7688bc5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176169"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5f9af-102">Elemento \<remove> para connectionManagement (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="5f9af-102">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="5f9af-103">Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="5f9af-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="5f9af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f9af-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f9af-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5f9af-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5f9af-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5f9af-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f9af-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f9af-107">Attributes</span></span>  
  
|<span data-ttu-id="5f9af-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="5f9af-108">**Attribute**</span></span>|<span data-ttu-id="5f9af-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="5f9af-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="5f9af-110">Um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="5f9af-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f9af-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5f9af-111">Child Elements</span></span>  

 <span data-ttu-id="5f9af-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5f9af-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f9af-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5f9af-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5f9af-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="5f9af-114">**Element**</span></span>|<span data-ttu-id="5f9af-115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="5f9af-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5f9af-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5f9af-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5f9af-117">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="5f9af-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f9af-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f9af-118">Remarks</span></span>  

 <span data-ttu-id="5f9af-119">O `remove` elemento remove a entrada da lista de gerenciamento de conexões para o servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="5f9af-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="5f9af-120">O valor do `address` atributo deve ser um nome de host ou endereço IP válido.</span><span class="sxs-lookup"><span data-stu-id="5f9af-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5f9af-121">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="5f9af-121">Configuration Files</span></span>  

 <span data-ttu-id="5f9af-122">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5f9af-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f9af-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f9af-123">Example</span></span>  

 <span data-ttu-id="5f9af-124">O exemplo a seguir remove todas as entradas da lista de gerenciamento de conexões do servidor `www.adventure-works.com` e, em seguida, configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="5f9af-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f9af-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f9af-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="5f9af-126">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5f9af-126">Network Settings Schema</span></span>](index.md)
