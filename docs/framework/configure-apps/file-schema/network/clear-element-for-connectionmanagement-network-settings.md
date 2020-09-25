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
ms.openlocfilehash: 446bec116118ee8b604ef3664a6eb0452e6d5a38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184099"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="331c4-102">Elemento \<clear> para connectionManagement (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="331c4-102">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="331c4-103">Limpa a lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="331c4-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="331c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="331c4-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="331c4-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="331c4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="331c4-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="331c4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="331c4-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="331c4-107">Attributes</span></span>  

 <span data-ttu-id="331c4-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="331c4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="331c4-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="331c4-109">Child Elements</span></span>  

 <span data-ttu-id="331c4-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="331c4-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="331c4-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="331c4-111">Parent Elements</span></span>  
  
|<span data-ttu-id="331c4-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="331c4-112">**Element**</span></span>|<span data-ttu-id="331c4-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="331c4-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="331c4-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="331c4-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="331c4-115">Especifica o número máximo de conexões com um host de rede.</span><span class="sxs-lookup"><span data-stu-id="331c4-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="331c4-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="331c4-116">Remarks</span></span>  

 <span data-ttu-id="331c4-117">O `clear` elemento limpa todas as entradas da lista de gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="331c4-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="331c4-118">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="331c4-118">Configuration Files</span></span>  

 <span data-ttu-id="331c4-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="331c4-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="331c4-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="331c4-120">Example</span></span>  

 <span data-ttu-id="331c4-121">O exemplo a seguir limpa a lista de gerenciamento de conexão e, em seguida, adiciona novas entradas de gerenciamento de conexão para o servidor `www.contoso.com` e todos os outros hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="331c4-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="331c4-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="331c4-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="331c4-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="331c4-123">Network Settings Schema</span></span>](index.md)
