---
title: Elemento <clear> para authenticationModules (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: 6ac2287ba9b17727835d43a3e3b8876f210fb5c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167321"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ccdb7-102">Elemento \<clear> para authenticationModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="ccdb7-102">\<clear> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="ccdb7-103">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="ccdb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccdb7-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccdb7-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ccdb7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ccdb7-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccdb7-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ccdb7-107">Attributes</span></span>  

 <span data-ttu-id="ccdb7-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ccdb7-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ccdb7-109">Child Elements</span></span>  

 <span data-ttu-id="ccdb7-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccdb7-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ccdb7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ccdb7-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="ccdb7-112">**Element**</span></span>|<span data-ttu-id="ccdb7-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ccdb7-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ccdb7-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ccdb7-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="ccdb7-115">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccdb7-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccdb7-116">Remarks</span></span>  

 <span data-ttu-id="ccdb7-117">O `clear` elemento remove todos os módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ccdb7-118">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="ccdb7-118">Configuration Files</span></span>  

 <span data-ttu-id="ccdb7-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ccdb7-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccdb7-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ccdb7-120">Example</span></span>  

 <span data-ttu-id="ccdb7-121">O exemplo a seguir remove todos os módulos de autenticação configurados.</span><span class="sxs-lookup"><span data-stu-id="ccdb7-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccdb7-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="ccdb7-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ccdb7-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ccdb7-123">Network Settings Schema</span></span>](index.md)
