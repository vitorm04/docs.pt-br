---
title: Elemento <remove> para authenticationModules (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: a8afdf442f8dc4e57a407583ea6c452330dae53f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281015"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="53434-102">\<Remover > elemento para authenticationModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="53434-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="53434-103">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53434-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="53434-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="53434-104">\<configuration></span></span>  
<span data-ttu-id="53434-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="53434-105">\<system.net></span></span>  
<span data-ttu-id="53434-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="53434-106">\<authenticationModules></span></span>  
<span data-ttu-id="53434-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="53434-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53434-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53434-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53434-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="53434-109">Attributes and Elements</span></span>  
 <span data-ttu-id="53434-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="53434-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53434-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="53434-111">Attributes</span></span>  
  
|<span data-ttu-id="53434-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="53434-112">**Attribute**</span></span>|<span data-ttu-id="53434-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="53434-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="53434-114">**type**</span><span class="sxs-lookup"><span data-stu-id="53434-114">**type**</span></span>|<span data-ttu-id="53434-115">O nome do módulo de autenticação a ser removido.</span><span class="sxs-lookup"><span data-stu-id="53434-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53434-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="53434-116">Child Elements</span></span>  
 <span data-ttu-id="53434-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="53434-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53434-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="53434-118">Parent Elements</span></span>  
  
|<span data-ttu-id="53434-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="53434-119">**Element**</span></span>|<span data-ttu-id="53434-120">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="53434-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="53434-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="53434-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="53434-122">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="53434-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53434-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="53434-123">Remarks</span></span>  
 <span data-ttu-id="53434-124">O `remove` elemento remove os módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível mais alto na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="53434-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="53434-125">O valor para o `type` atributo deve ser um nome de classe válida.</span><span class="sxs-lookup"><span data-stu-id="53434-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="53434-126">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="53434-126">Configuration Files</span></span>  
 <span data-ttu-id="53434-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="53434-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53434-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53434-128">Example</span></span>  
 <span data-ttu-id="53434-129">O exemplo a seguir remove um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="53434-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53434-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53434-130">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="53434-131">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="53434-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
