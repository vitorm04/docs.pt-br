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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088479"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="6d017-102">Elemento \<clear> para connectionManagement (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="6d017-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="6d017-103">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="6d017-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="6d017-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d017-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d017-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6d017-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d017-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6d017-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d017-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="6d017-107">Attributes</span></span>  
 <span data-ttu-id="6d017-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6d017-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6d017-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6d017-109">Child Elements</span></span>  
 <span data-ttu-id="6d017-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6d017-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d017-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6d017-111">Parent Elements</span></span>  
  
|<span data-ttu-id="6d017-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="6d017-112">**Element**</span></span>|<span data-ttu-id="6d017-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="6d017-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6d017-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="6d017-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="6d017-115">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="6d017-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d017-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d017-116">Remarks</span></span>  
 <span data-ttu-id="6d017-117">O `clear` elemento limpa todas as entradas da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="6d017-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6d017-118">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6d017-118">Configuration Files</span></span>  
 <span data-ttu-id="6d017-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6d017-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d017-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d017-120">Example</span></span>  
 <span data-ttu-id="6d017-121">O exemplo a seguir limpa a lista de gerenciamento de conexão e, em seguida, adiciona novas entradas de gerenciamento de conexão para o servidor `www.contoso.com` e todos os outros hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="6d017-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d017-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="6d017-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="6d017-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6d017-123">Network Settings Schema</span></span>](index.md)
