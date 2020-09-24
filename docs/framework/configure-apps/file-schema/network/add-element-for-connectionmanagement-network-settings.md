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
ms.openlocfilehash: 05e4a1bc42dc39c7d2b56e30c98bdeefd31e4416
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149472"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="a5ffd-102">Elemento \<add> para connectionManagement (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="a5ffd-102">\<add> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="a5ffd-103">Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-103">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="a5ffd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5ffd-104">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5ffd-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a5ffd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a5ffd-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5ffd-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a5ffd-107">Attributes</span></span>  
  
|<span data-ttu-id="a5ffd-108">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="a5ffd-108">**Attribute**</span></span>|<span data-ttu-id="a5ffd-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a5ffd-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="a5ffd-110">Uma cadeia de caracteres que descreve um endereço IP ou nome DNS.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-110">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="a5ffd-111">O número máximo de conexões permitidas a um servidor.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-111">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="a5ffd-112">Se não for fornecido, o padrão será 2.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-112">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5ffd-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a5ffd-113">Child Elements</span></span>  

 <span data-ttu-id="a5ffd-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5ffd-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5ffd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a5ffd-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="a5ffd-116">**Element**</span></span>|<span data-ttu-id="a5ffd-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a5ffd-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a5ffd-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a5ffd-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a5ffd-119">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5ffd-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5ffd-120">Remarks</span></span>  

 <span data-ttu-id="a5ffd-121">O valor do `address` atributo deve ser um asterisco para indicar todas as conexões ou uma cadeia de caracteres do formulário `<schema>://<idn_hostname>[:<port>]` .</span><span class="sxs-lookup"><span data-stu-id="a5ffd-121">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="a5ffd-122">Se o URI passado para qualquer API HTTP contiver Unicode, o nome será convertido internamente usando o <xref:System.Uri.DnsSafeHost%2A> que pode retornar uma cadeia de caracteres Punicode (comportamento dependente da configuração de IDN atual).</span><span class="sxs-lookup"><span data-stu-id="a5ffd-122">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a5ffd-123">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="a5ffd-123">Configuration Files</span></span>  

 <span data-ttu-id="a5ffd-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a5ffd-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ffd-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5ffd-125">Example</span></span>  

 <span data-ttu-id="a5ffd-126">O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.</span><span class="sxs-lookup"><span data-stu-id="a5ffd-126">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5ffd-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5ffd-127">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a5ffd-128">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="a5ffd-128">Network Settings Schema</span></span>](index.md)
