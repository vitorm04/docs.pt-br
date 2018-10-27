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
ms.openlocfilehash: 074f2f0cd2c3ac6c6287db08b22ead07afa58fc5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190808"
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="8a452-102">&lt;authenticationModules&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8a452-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8a452-103">Especifica os módulos usados para autenticar solicitações de rede.</span><span class="sxs-lookup"><span data-stu-id="8a452-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="8a452-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8a452-104">\<configuration></span></span>  
<span data-ttu-id="8a452-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8a452-105">\<system.net></span></span>  
<span data-ttu-id="8a452-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="8a452-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a452-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a452-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a452-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8a452-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8a452-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8a452-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a452-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8a452-110">Attributes</span></span>  
 <span data-ttu-id="8a452-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8a452-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8a452-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8a452-112">Child Elements</span></span>  
  
|<span data-ttu-id="8a452-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="8a452-113">**Element**</span></span>|<span data-ttu-id="8a452-114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8a452-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8a452-115">add</span><span class="sxs-lookup"><span data-stu-id="8a452-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="8a452-116">Adiciona um módulo de autenticação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a452-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="8a452-117">clear</span><span class="sxs-lookup"><span data-stu-id="8a452-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="8a452-118">Limpa todos os módulos de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a452-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="8a452-119">remove</span><span class="sxs-lookup"><span data-stu-id="8a452-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="8a452-120">Remove um módulo de autenticação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a452-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8a452-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8a452-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8a452-122">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="8a452-122">**Element**</span></span>|<span data-ttu-id="8a452-123">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8a452-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8a452-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="8a452-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="8a452-125">Contém configurações que especificam como o .NET Framework se conecta à rede.</span><span class="sxs-lookup"><span data-stu-id="8a452-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a452-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a452-126">Remarks</span></span>  
 <span data-ttu-id="8a452-127">O `authenticationModule` elemento Especifica os módulos de autenticação que conduzir o processo de autenticação com um servidor.</span><span class="sxs-lookup"><span data-stu-id="8a452-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="8a452-128">Um módulo de autenticação deve implementar o <xref:System.Net.IAuthenticationModule> interface.</span><span class="sxs-lookup"><span data-stu-id="8a452-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8a452-129">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8a452-129">Configuration Files</span></span>  
 <span data-ttu-id="8a452-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8a452-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a452-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a452-131">Example</span></span>  
 <span data-ttu-id="8a452-132">O exemplo a seguir permite que um módulo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="8a452-132">The following example enables an authentication module.</span></span> <span data-ttu-id="8a452-133">Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="8a452-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a452-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a452-134">See Also</span></span>  
- <xref:System.Net.IAuthenticationModule>  
- <xref:System.Net.AuthenticationManager>  
- [<span data-ttu-id="8a452-135">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8a452-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
