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
ms.openlocfilehash: a76df48a9de084e1121a5e96b22edf7aa3acba23
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088479"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5376e-102">\<limpar > elemento para connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="5376e-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="5376e-103">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="5376e-103">Clears the connection management list.</span></span>  

<span data-ttu-id="5376e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5376e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5376e-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5376e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5376e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5376e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="5376e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**desmarque >**</span><span class="sxs-lookup"><span data-stu-id="5376e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5376e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5376e-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5376e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5376e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5376e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5376e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5376e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5376e-111">Attributes</span></span>  
 <span data-ttu-id="5376e-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5376e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5376e-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5376e-113">Child Elements</span></span>  
 <span data-ttu-id="5376e-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5376e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5376e-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5376e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5376e-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="5376e-116">**Element**</span></span>|<span data-ttu-id="5376e-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="5376e-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5376e-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5376e-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5376e-119">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="5376e-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5376e-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="5376e-120">Remarks</span></span>  
 <span data-ttu-id="5376e-121">O elemento `clear` limpa todas as entradas da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="5376e-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5376e-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="5376e-122">Configuration Files</span></span>  
 <span data-ttu-id="5376e-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="5376e-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5376e-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5376e-124">Example</span></span>  
 <span data-ttu-id="5376e-125">O exemplo a seguir limpa a lista de gerenciamento de conexão e, em seguida, adiciona novas entradas de gerenciamento de conexão para o servidor `www.contoso.com` e todos os outros hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="5376e-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5376e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5376e-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="5376e-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="5376e-127">Network Settings Schema</span></span>](index.md)
