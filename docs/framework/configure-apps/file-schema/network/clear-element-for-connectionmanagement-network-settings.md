---
title: Elemento <clear> para connectionManagement (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: 17b380b12977423669fd413132d69a3082daca41
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698368"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="1db91-102">\<clear > elemento para connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="1db91-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="1db91-103">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="1db91-103">Clears the connection management list.</span></span>  
  
[<span data-ttu-id="1db91-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="1db91-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="1db91-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1db91-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="1db91-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1db91-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="1db91-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="1db91-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db91-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1db91-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1db91-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1db91-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1db91-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1db91-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1db91-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1db91-111">Attributes</span></span>  
 <span data-ttu-id="1db91-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1db91-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1db91-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1db91-113">Child Elements</span></span>  
 <span data-ttu-id="1db91-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1db91-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1db91-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1db91-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1db91-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="1db91-116">**Element**</span></span>|<span data-ttu-id="1db91-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="1db91-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1db91-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="1db91-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="1db91-119">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="1db91-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db91-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="1db91-120">Remarks</span></span>  
 <span data-ttu-id="1db91-121">O elemento `clear` limpa todas as entradas da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="1db91-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1db91-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="1db91-122">Configuration Files</span></span>  
 <span data-ttu-id="1db91-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1db91-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db91-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1db91-124">Example</span></span>  
 <span data-ttu-id="1db91-125">O exemplo a seguir limpa a lista de gerenciamento de conexão e, em seguida, adiciona novas entradas de gerenciamento de conexão para o servidor `www.contoso.com` e todos os outros hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="1db91-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1db91-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1db91-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="1db91-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="1db91-127">Network Settings Schema</span></span>](index.md)
