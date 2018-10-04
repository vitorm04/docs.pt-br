---
title: '&lt;authenticationModules&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 394a686fe07036d6c3ac2bc51fb3503e1ee4a9e6
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777559"
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="79696-102">&lt;authenticationModules&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="79696-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="79696-103">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="79696-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="79696-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="79696-104">\<configuration></span></span>  
<span data-ttu-id="79696-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="79696-105">\<system.net></span></span>  
<span data-ttu-id="79696-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="79696-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79696-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79696-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79696-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="79696-108">Attributes and Elements</span></span>  
 <span data-ttu-id="79696-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="79696-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79696-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="79696-110">Attributes</span></span>  
 <span data-ttu-id="79696-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="79696-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79696-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="79696-112">Child Elements</span></span>  
  
|<span data-ttu-id="79696-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="79696-113">**Element**</span></span>|<span data-ttu-id="79696-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="79696-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="79696-115">add</span><span class="sxs-lookup"><span data-stu-id="79696-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="79696-116">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79696-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="79696-117">clear</span><span class="sxs-lookup"><span data-stu-id="79696-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="79696-118">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79696-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="79696-119">remove</span><span class="sxs-lookup"><span data-stu-id="79696-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="79696-120">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79696-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79696-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="79696-121">Parent Elements</span></span>  
  
|<span data-ttu-id="79696-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="79696-122">**Element**</span></span>|<span data-ttu-id="79696-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="79696-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="79696-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="79696-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="79696-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="79696-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79696-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="79696-126">Remarks</span></span>  
 <span data-ttu-id="79696-127">O `authenticationModule` elemento Especifica os módulos de autenticação que conduzir o processo de autenticação com um servidor.</span><span class="sxs-lookup"><span data-stu-id="79696-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="79696-128">Um módulo de autenticação deve implementar o <xref:System.Net.IAuthenticationModule> interface.</span><span class="sxs-lookup"><span data-stu-id="79696-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="79696-129">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="79696-129">Configuration Files</span></span>  
 <span data-ttu-id="79696-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="79696-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79696-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79696-131">Example</span></span>  
 <span data-ttu-id="79696-132">O exemplo a seguir permite que um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="79696-132">The following example enables an authentication module.</span></span> <span data-ttu-id="79696-133">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="79696-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79696-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79696-134">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="79696-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="79696-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
