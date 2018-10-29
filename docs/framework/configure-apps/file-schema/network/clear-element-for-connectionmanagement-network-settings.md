---
title: '&lt;Limpar&gt; elemento para connectionManagement (configurações de rede)'
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
ms.openlocfilehash: dba05128220b34bed34da4309a4994cbc4e1bd40
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205094"
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e1e07-102">&lt;Limpar&gt; elemento para connectionManagement (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="e1e07-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e1e07-103">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="e1e07-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="e1e07-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e1e07-104">\<configuration></span></span>  
<span data-ttu-id="e1e07-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e1e07-105">\<system.net></span></span>  
<span data-ttu-id="e1e07-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="e1e07-106">\<connectionManagement></span></span>  
<span data-ttu-id="e1e07-107">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="e1e07-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e07-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1e07-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1e07-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1e07-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1e07-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1e07-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1e07-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1e07-111">Attributes</span></span>  
 <span data-ttu-id="e1e07-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e1e07-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1e07-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1e07-113">Child Elements</span></span>  
 <span data-ttu-id="e1e07-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e1e07-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1e07-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1e07-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e1e07-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e1e07-116">**Element**</span></span>|<span data-ttu-id="e1e07-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="e1e07-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e1e07-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e1e07-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="e1e07-119">Especifica o número máximo de conexões para um host de rede.</span><span class="sxs-lookup"><span data-stu-id="e1e07-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1e07-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1e07-120">Remarks</span></span>  
 <span data-ttu-id="e1e07-121">O `clear` elemento limpa todas as entradas da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="e1e07-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e1e07-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="e1e07-122">Configuration Files</span></span>  
 <span data-ttu-id="e1e07-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e1e07-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e07-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1e07-124">Example</span></span>  
 <span data-ttu-id="e1e07-125">O exemplo a seguir limpa a lista de gerenciamento de conexão e, em seguida, adiciona novas entradas de gerenciamento de conexão para o servidor `www.contoso.com` e todos os outros hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="e1e07-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1e07-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1e07-126">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="e1e07-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="e1e07-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
